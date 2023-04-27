---
copyright:
  years: 2022, 2023
lastupdated: "2023-04-27"

keywords: support, backup, restore, disaster

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Understanding disaster recovery for IBM Cloud Data Security Broker
{: #sb_dr}

Components of the {{site.data.keyword.security_broker_short}} data protection services do not
require any protected data to be stored or cached to operate. This
guarantees that the data is not lost if any {{site.data.keyword.security_broker_short}}
component fails or goes down. In {{site.data.keyword.security_broker_short}} components, only
policy configurations and metadata is stored, and all this data is
recoverable.

It is possible to back up the configurations and metadata stored in a {{site.data.keyword.security_broker_short}} deployment and recover them after a significant outage,
facilitating quick service restoration in a disaster recovery scenario.
This section outlines the procedures for backing up and restoring the
{{site.data.keyword.security_broker_short}} deployment.

## Backup considerations
{: #sb_dr_bkp_considerations}

The following services are required for a complete {{site.data.keyword.security_broker_short}}
deployment:

-   Key management

-   Database

-   Cloud Object storage

Ensure that the backup schedule for these services aligns with the {{site.data.keyword.security_broker_short}} backups. Additionally, administrators must keep records which are used for linking the {{site.data.keyword.security_broker_short}} backup and the backups of the other
services, as well as all backups for the {{site.data.keyword.security_broker_short}} deployment
and the above mentioned services, in a secure location.

## Backup procedure
{: #sb_dr_bkp_procedure}

In {{site.data.keyword.security_broker_short}} Manager, all configuration and metadata data
needed for a {{site.data.keyword.security_broker_short}} deployment is stored. {{site.data.keyword.security_broker_short}} Manager's most recent configuration is always accessible to {{site.data.keyword.security_broker_short}} Shields. As a result, {{site.data.keyword.security_broker_short}} Manager is
the only part of {{site.data.keyword.security_broker_short}} that requires backup.

## Backing up Data Security Broker Manager deployed on {{site.data.keyword.cloud_notm}} Kubernetes cluster (Kubernetes) or {{site.data.keyword.redhat_openshift_full}} Kubernetes ({{site.data.keyword.redhat_openshift_notm}}) cluster
{: #sb_dr_bkp_dsb_manager}

{{site.data.keyword.security_broker_short}}  Manager instances running in an Kubernetes cluster or
{{site.data.keyword.redhat_openshift_notm}} cluster require network access to the cluster as well as access to a
workstation with permission to run Kubernetes or {{site.data.keyword.redhat_openshift_notm}} command line
tools. Additionally, the workstation must have a directory with write
permissions and sufficient storage to store the backup. 125GB of storage space is sufficient for all deployments.

**To take a backup, follow these steps:**

1.  Access the cluster where {{site.data.keyword.security_broker_short}} Manager is deployed by logging into a Kubernetes or {{site.data.keyword.redhat_openshift_notm}} workstation.

2.  To back up the MongoDB collections and {{site.data.keyword.security_broker_short}} Manager configuration files, create the script provided below and execute it. The location specified after the necessary **-b** option is where the backup file is kept by this script. Check whether the script is being used to back up a {{site.data.keyword.security_broker_short}} Manager deployment on an {{site.data.keyword.redhat_openshift_notm}} cluster or a Kubernetes cluster, and uncomment the relevant command alias for the specified type of cluster where {{site.data.keyword.security_broker_short}} Manager is installed.

```
#!/bin/bash
if [ $# -eq 0 ]
 then
   echo "No arguments supplied"
   echo "Usage: $0 -b <backup location> -n <k8s namespace>"
fi

while getopts b:n: flag
do
   case "${flag}" in
       b) backup=${OPTARG};;
       n) namespace=${OPTARG};;
   esac
done

if [ -z "${backup}" ];
then
  echo "Please provide backup location with -b option"
  exit
fi

if [ ! -d "$backup" ];
then
  echo "Please provide a valid backup location with -b option"
  exit
fi

if [ -z "${namespace}" ];
then
  echo "Please provide a valid namespace with -n option"
  exit
fi

    ### NOTE: SET THE kb ALIAS TO THE CORRECT ONE FOR THE CLUSTER TYPE
#
## For Kubernetes
#kb='kubectl --namespace $namespace'
## For OpenShift
kb='kubectl --namespace '$namespace

# Retrieving container details
    #
    #
echo $kb
    
BM_container="$($kb get pods -o=jsonpath='{range .items[?(@.metadata.labels.app=="dsb-manager")]}{.metadata.name}' )"
Mongo_container="$($kb get pods -o=jsonpath='{range .items[?(@.metadata.labels.app=="dsb-mongodb")]}{.metadata.name}')"
echo "BM_container ==>" $BM_container
echo "Mongo_container ==>" $Mongo_container

version="$($kb exec -it $BM_container -- bash -c 'cat /opt/baffle/BAFFLEVERSIONS | grep BMVERSION' | awk -F "=" '{print $2}' )"
version="${version//$'\r'/}"
echo "version ==>" $version

BM_BACKUP_DIR=$backup

MONGO_USER="$($kb exec -it $Mongo_container -- bash -c 'cat /run/secrets/mongodb_user' )"
MONGO_PASS="$($kb exec -it $Mongo_container -- bash -c 'cat /run/secrets/mongodb_pass' )"
echo $MONGO_USER
echo $MONGO_PASS

backup_directory=$BM_BACKUP_DIR/$version
mkdir -p $backup_directory
echo "backup_directory ==> "$backup_directory

#cp -r $BM_DEPLOY_DIR/config $backup_directory

# Mongodb backup
BackupMongo() {
 echo "Mongodb Backup.."
 readarray -t backup_dbs < <($kb exec -it $Mongo_container -- sh -c 'mongo m_db --quiet -u '$MONGO_USER' -p '$MONGO_PASS' --authenticationDatabase admin --eval "db.tenant.find({}, {\"_id\":false,\"tid\":true})"' | awk -F'"' '{print $4}')
 $kb exec -it $Mongo_container sh -c 'mongodump -u '${MONGO_USER}' -p '${MONGO_PASS}' --authenticationDatabase admin -d m_db -o /tmp/dump'
 for backup_db in "${backup_dbs[@]}"; do
    $kb exec -it $Mongo_container -- sh -c 'mongodump -u '${MONGO_USER}' -p '${MONGO_PASS}' --authenticationDatabase admin -d '$backup_db' --excludeCollection=audit -o /tmp/dump'
 done
 backupDumpMongoFile="/tmp/""$version"MONGO.tar.gz
 $kb exec -it $Mongo_container -- sh -c 'tar -czvf '${backupDumpMongoFile}' /tmp/dump'
 $kb cp $Mongo_container:$backupDumpMongoFile $backup_directory/"$version"MONGO.tar.gz
}

# DSB Manger backup
BMbackup() {
 echo "BM backup.."
 BMbackupDumpFile="/tmp/""$version"BM.tar.gz
 $kb exec -it $BM_container -- sh -c 'tar -czvf '${BMbackupDumpFile}' /opt/dsb/dsb-manager'
 $kb cp $BM_container:$BMbackupDumpFile $backup_directory/"$version"BM.tar.gz
}

BackupMongo
BMbackup
```
{: codeblock}

3.  The following files are added to the specified backup location after you have finished executing the script:

Release-DSB.\<release\>MONGO.tar.gz

Release-DSB.\<release\>BM.tar.gz

4.  Transfer the backups of the key management, object storage, and
    database services related to the {{site.data.keyword.security_broker_short}} deployment,
    as well as the {{site.data.keyword.security_broker_short}} Manager backup files, to a
    reliable backup storage location.

**Restore procedure**

The {{site.data.keyword.security_broker_short}} deployment can be recovered in a disaster
recovery situation to a state that was previously backed up, provided
that all dependent services are also recovered in the same manner. This
applies to any services that has suffered a irrecoverable failure. If
the dependent services were not affected, all that is required is to
ensure that network connectivity between the {{site.data.keyword.security_broker_short}}
deployment and those services is restored.

Since {{site.data.keyword.security_broker_short}} Manager contains all the configuration and
metadata needed for a {{site.data.keyword.security_broker_short}} deployment, the goal of the
process is to restore {{site.data.keyword.security_broker_short}} Manager to a previous state
so that a new shield can be deployed to enforce the previously
configured security policies.

## Restoring Data Security Broker Manager deployed on Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster to a previous state**

A new {{site.data.keyword.security_broker_short}} Manager deployment needs to be set up in the
cluster in order to return {{site.data.keyword.security_broker_short}} Manager to its previous
state. Please implement {{site.data.keyword.security_broker_short}} Manager on a Kubernetes or
{{site.data.keyword.redhat_openshift_notm}} cluster by following the deployment instructions.

The administrator carrying out the restore operation will require
network connectivity to the cluster as well as access to a workstation
with permission to use the command-line tools for Kubernetes or {{site.data.keyword.redhat_openshift_notm}}.

**To restore a {{site.data.keyword.security_broker_short}} deployment, follow these steps

1.  Log in to the workstation using command-line tools, and use the
    > recently installed Data Security Broker Manager to access the
    > Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster.

2.  To create a temporary storage area on the workstation, copy the Data
    > Security Broker Manager backup files there. The names of the
    > backup files will include:

3.  Release-Baffle.\<release\>MONGO.tar.gz

4.  Release-Baffle.\<release\>BM.tar.gz

> Text
>
> Copy

5.  To restore the Data Security Broker Manager configuration files and
    > MongoDB collections, create and execute the script provided below.
    > As an input to the script, specify the location of the temporary
    > storage location for backup files.

6.  Open a new browser tab and log into Data Security Broker Manager
    > after the script has finished running. Log in to confirm that the
    > applications, databases, and key stores\' original configurations
    > have been restored.

7.  For all of the applications with data security policies, deploy new
    > Data Security Broker Shields by adhering to the deployment
    > procedures. Make sure the Helm chart is updated with the
    > appropriate Sync ID for each application.

8.  Log into Data Security Broker Manager after the Data Security Broker
    > Shield pods have been deployed to make sure the newly installed
    > Data Security Broker Shields are in the RUNNING status.

**Restoring Data Security Broker Manager deployed using Docker on a
standalone machine**

On the standalone machine, a new Data Security Broker Manager deployment
must be created in order to return Data Security Broker Manager to a
previous state. Please do so by adhering to the guidelines for deploying
Data Security Broker Manager on a standalone machine.

The restore operation will be carried out by an administrator with sudo
access to the standalone machine.

**Following these steps will restore Data Security Broker Manager:**

1.  Enter the computer where a Data Security Broker Manager has been set
    > up.

2.  To create a temporary storage area on the computer, copy the Data
    > Security Broker Manager backup files there. The names of the
    > backup files will include:

3.  Release-Baffle.\<release\>MONGO.tar.gz

4.  Release-Baffle.\<release\>BM.tar.gz

> Text
>
> Copy

5.  To restore the Data Security Broker Manager configuration files and
    > MongoDB collections, create and execute the script provided below.
    > As the script\'s input, specify the location where backup files
    > are momentarily stored.

6.  Run the script listed below to recover the MongoDB collections and
    > Data Security Broker Manager configuration files. This script
    > requires as input a folder where backup files are located and that
    > is open to the script.

7.  #!/bin/bash

8.  

9.  if \[ \$# -eq 0 \]

10. then

11. echo \"No arguments supplied\"

12. echo \"Usage: \$0 -m \<mongodb backup tar.gz\> -b \<BM backup tar.gz
    > file\> -u \<mongdb user name used for backup\> -p \<mongdb
    > password used for backing up\> -n \<k8s namespace\>\"

13. fi

14. 

15. while getopts m:b:u:p: flag

16. do

17. case \"\${flag}\" in

18. m\) MongoDumpFile=\${OPTARG};;

19. b\) BMDumpFile=\${OPTARG};;

20. u\) MONGO_USER=\${OPTARG};;

21. p\) MONGO_PASS=\${OPTARG};;

22. \# n) namespace=\${OPTARG};;

23. esac

24. done

25. 

26. if \[ \$# -eq 0 \]

27. then

28. echo \"No arguments supplied\"

29. echo \"Usage: \$0 -b \<backup loaction\> -u \<mongdb user name used
    > for backup\> -p \<mongdb password used for backing up\>\"

30. fi

31. 

32. if \[ -z \"\${MongoDumpFile}\" \];

33. then

34. echo \"Please provide backup location with -m option\"

35. exit

36. fi

37. 

38. if \[ -z \"\${BMDumpFile}\" \];

39. then

40. echo \"Please provide backup location with -b option\"

41. exit

42. fi

43. 

44. if \[ ! -f \"\$MongoDumpFile\" \];

45. then

46. echo \"Please provide a valid backup location with -m option\"

47. exit

48. fi

49. 

50. if \[ ! -f \"\$BMDumpFile\" \];

51. then

52. echo \"Please provide a valid backup location with -b option\"

53. exit

54. fi

55. 

56. if \[ -z \"\${MONGO_USER}\" \];

57. then

58. echo \"Please provide Mongodb user via -u option. It should be same
    > user used for backup\"

59. exit

60. fi

61. 

62. if \[ -z \"\${MONGO_PASS}\" \];

63. then

64. echo \"Please provide Mongodb password via -p option. It should be
    > same password used for backup\"

65. exit

66. fi

67. 

68. #if \[ -z \"\${namespace}\" \];

69. #then

70. \# echo \"Please provide kubernetes namespace via -n option.\"

71. \# exit

72. #fi

73. 

74. version=\"\$(docker exec -it baffle_manager_1 sh -c \'cat
    > /opt/baffle/BAFFLEVERSIONS \| grep BMVERSION\' \| awk -F \"=\"
    > \'{print \$2}\')\"

75. version=\${version//\$\'\\r\'/}

76. echo \"version ==\> \"\$version

77. 

78. RestoreMongo() {

79. echo \"Mongodb Restore\...\"

80. mongocontainerdump=\"\$(basename \-- \$MongoDumpFile)\"

81. echo \"mongocontainerdump is ==\>\"\$mongocontainerdump

82. mongocontainerdump1=\"/tmp/\"\$mongocontainerdump

83. echo \"mongocontainerdump1 is ==\>\"\$mongocontainerdump1

84. sudo docker cp \$MongoDumpFile baffle_mongodb_1:/tmp/

85. sudo docker exec -it baffle_mongodb_1 sh -c \'tar -xvf
    > \'\${mongocontainerdump1}\' \'

86. sudo docker exec -it baffle_mongodb_1 sh -c \'mongorestore
    > \--username=\'\${MONGO_USER}\' \--db=baff
    > \--password=\'\${MONGO_PASS}\' \--authenticationDatabase=admin
    > /tmp/dump/baff\'

87. 

88. }

89. 

90. RestoreBM() {

91. echo \"BM Restore\...\"

92. BMcontainerdump=\"\$(basename \-- \$BMDumpFile)\"

93. BMcontainerdump1=\"/tmp/\"\$BMcontainerdump

94. sudo docker cp \$BMDumpFile baffle_manager_1:/tmp/

95. sudo docker exec -it baffle_manager_1 sh -c \'tar -xvf
    > \'\${BMcontainerdump1}\' \'

96. sudo docker exec -it baffle_manager_1 sh -c \'cp -pr
    > /tmp/opt/baffle/baffle-manager/\* /opt/baffle/baffle-manager/\'

97. 

98. }

99. 

100. RestoreMongo

101. RestoreBM

> Text
>
> Copy

102. Open a new browser tab and log into Data Security Broker Manager
     > after the script has finished running. Log in to confirm that the
     > applications, databases, and key stores\' original configurations
     > have been restored.

103. For all of the applications with data security policies, deploy new
     > Data Security Broker Shields by adhering to the deployment
     > procedures. To set the BM_IP with the new IP address or host name
     > for the recently deployed Data Security Broker Manager, make sure
     > to update the.env file. Update the SYNC_ID variable as well with
     > the appropriate Sync_ID for each application that the deployed
     > Data Security Broker Shield is linked to.

104. Log into Data Security Broker Manager after the Data Security
     > Broker Shield instances have been set up to ensure that they are
     > in the RUNNING status.
