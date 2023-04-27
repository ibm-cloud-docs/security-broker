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

-   Key management services

-   Database

-   Cloud Object storage

Ensure that the backup schedule for these services align with the {{site.data.keyword.security_broker_short}} backups. Additionally, administrators must keep records which are used for linking the {{site.data.keyword.security_broker_short}} backup and the backups of the other
services, as well as all backups for the {{site.data.keyword.security_broker_short}} deployment
and the above mentioned services, in a secure location.

## Backup procedure
{: #sb_dr_bkp_procedure}

In {{site.data.keyword.security_broker_short}} Manager, all configuration and metadata data
needed for a {{site.data.keyword.security_broker_short}} deployment is stored. {{site.data.keyword.security_broker_short}} Manager's most recent configuration is always accessible to {{site.data.keyword.security_broker_short}} Shields. As a result, {{site.data.keyword.security_broker_short}} Manager is
the only part of {{site.data.keyword.security_broker_short}} that requires backup.

## Backing up Data Security Broker Manager deployed on {{site.data.keyword.cloud_notm}} cluster or ({{site.data.keyword.redhat_openshift_notm}}) cluster
{: #sb_dr_bkp_dsb_manager}

{{site.data.keyword.security_broker_short}}  Manager instances running in a Kubernetes cluster or
{{site.data.keyword.redhat_openshift_notm}} cluster require network access to the cluster as well as access to the workstation with permission to execute Kubernetes or {{site.data.keyword.redhat_openshift_notm}} command line tools. Additionally, the workstation must have a directory with write
permissions and sufficient storage to store the backup. 125GB of storage space is sufficient for all deployments.

To take a backup, follow these steps:

1. Access the cluster where {{site.data.keyword.security_broker_short}} Manager is deployed by logging into a Kubernetes or {{site.data.keyword.redhat_openshift_notm}} workstation.

2. To back up the MongoDB collections and {{site.data.keyword.security_broker_short}} Manager configuration files, create the script provided below and execute it. The location that is specified after the **-b** option is where the backup file is kept by the script. Check whether the script is being used to back up a {{site.data.keyword.security_broker_short}} Manager deployment on a {{site.data.keyword.redhat_openshift_notm}} cluster or a Kubernetes cluster, and uncomment the relevant command alias for the specified type of cluster where {{site.data.keyword.security_broker_short}} Manager is installed.

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

3. The following files are added to the specified backup location after you have finished executing the script:

```
Release-DSB.\<release\>MONGO.tar.gz
Release-DSB.\<release\>BM.tar.gz
```
{: codeblock}

4. Transfer the backups of the key management, object storage, and database services related to the {{site.data.keyword.security_broker_short}} deployment, as well as the {{site.data.keyword.security_broker_short}} Manager backup files, to a reliable backup storage location.

## Restore procedure
{: #sb_dr_restore_procedure}

The {{site.data.keyword.security_broker_short}} deployment can be recovered in a disaster
recovery situation to a state that was previously backed up, provided
that all the dependent services are also recovered in the same manner. This
applies to any services that has suffered a irrecoverable failure. If
the dependent services were not affected, all that is required is to
ensure that the network connectivity between the {{site.data.keyword.security_broker_short}}
deployment and the dependent services is restored.

Since {{site.data.keyword.security_broker_short}} Manager contains all the configuration and
metadata needed for a {{site.data.keyword.security_broker_short}} deployment, the goal of the
process is to restore {{site.data.keyword.security_broker_short}} Manager to a previous state
so that a new shield can be deployed to enforce the previously configured security policies.

## Restoring Data Security Broker Manager deployed on a Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster to a previous state
{: #sb_dr_restore_procedure_dsb_manager}

A new {{site.data.keyword.security_broker_short}} Manager deployment needs to be set up in a Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster, in order to return {{site.data.keyword.security_broker_short}} Manager to its previous state. 
The administrator carrying out the restore operation requires network connectivity to the cluster as well as access to a workstation with permission to use the command-line tools for Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster.

To restore a {{site.data.keyword.security_broker_short}} deployment, follow the steps:

1. Log in to the workstation using command-line tools, and use the recently installed {{site.data.keyword.security_broker_short}} Manager to access the Kubernetes or {{site.data.keyword.redhat_openshift_notm}} cluster.

2. To create a temporary storage area on the workstation, copy the {{site.data.keyword.security_broker_short}} Manager backup files there. The names of the backup files includes the following:

```
Release-DSB.\<release\>MONGO.tar.gz
Release-DSB.\<release\>BM.tar.gz
```
{: codeblock}

3. To restore the {{site.data.keyword.security_broker_short}} Manager configuration files and MongoDB collections, create and execute the script provided below. As an input to the script, specify the location of the temporary storage location for backup files.

```
#!/bin/bash
if [ $# -eq 0 ]
then
echo "No arguments supplied"
echo "Usage: $0 -m <mongodb backup tar.gz> -b <BM backup tar.gz file> -u
<MongoDB user name used for original dsb Manager deployment> -p <MongoDB
password used in original dsb Manager deployment> -n <k8s namespace>"
fi
while getopts m:b:u:p:n: flag
do
case "${flag}" in
m) MONGO_DUMP_FILE=${OPTARG};;
b) BM_DUMP_FILE=${OPTARG};;
u) MONGO_USER=${OPTARG};;
p) MONGO_PASS=${OPTARG};;
n) NAMESPACE=${OPTARG};;
esac
done
if [ -z "${MONGO_DUMP_FILE}" ];
then
echo "Please provide backup location with -m option"
exit
fi
if [ -z "${BM_DUMP_FILE}" ];
then
echo "Please provide backup location with -b option"
exit
fi
if [ ! -f "$MONGO_DUMP_FILE" ];
then
echo "Please provide a valid backup location with -b option"
exit
fi
if [ ! -f "$BM_DUMP_FILE" ];
then
echo "Please provide a valid backup location with -b option"
exit
fi
if [ -z "${MONGO_USER}" ];
then
echo "Please provide Mongodb user via -u option. It should be same user used
for backup"
exit
fi
if [ -z "${MONGO_PASS}" ];
then
echo "Please provide Mongodb password via -p option. It should be same password
specified in the original dsb Manager deployment"
exit
fi
if [ -z "${NAMESPACE}" ];
then

echo "Please provide kubernetes NAMESPACE via -n option."
exit
fi
### NOTE: SET THE kb ALIAS TO THE CORRECT ONE FOR THE CLUSTER TYPE
## For Kubernetes
#kb='kubectl --namespace '$NAMESPACE
#echo "KB = "$kb
## For OpenShift
kb='kubectl --namespace '$NAMESPACE
echo "OC = "$kb

# Retrieving container details
BM_container="$($kb get pods -o=jsonpath='{range .items[?(@.metadata.labels.app=="dsb-manager")]}{.metadata.name}' )"
Mongo_container="$($kb get pods -o=jsonpath='{range .items[?(@.metadata.labels.app=="dsb-mongodb")]}{.metadata.name}')"
echo "BM_container ==>" $BM_container
echo "Mongo_container ==>" $Mongo_container

version="$($kb exec -it $BM_container -- bash -c 'cat /opt/baffle/BAFFLEVERSIONS | grep BMVERSION' | awk -F "=" '{print $2}' )"
version="${version//$'\r'/}"
echo "version ==>" $version

# Restore DSB MongoDB
RestoreMongo() 
{
echo "Mongodb Restore..."
MONGO_FILE=$(basename $MONGO_DUMP_FILE)
echo "MONGO_FILE ==> "$MONGO_FILE
$kb cp $MONGO_DUMP_FILE $Mongo_container:/tmp/$MONGO_FILE
$kb exec -it $Mongo_container -- sh -c 'tar -xvf /tmp/'$MONGO_FILE
$kb exec -it $Mongo_container -- sh -c 'mongorestore --username='${MONGO_USER}' --password='${MONGO_PASS}' --nsInclude=ibm.* --verbose --authenticationDatabase=admin /tmp/dump'
}

# Restore DSB Manager
RestoreBM() 
{
echo "BM Restore..."
BM_FILE=$(basename $BM_DUMP_FILE)
echo "BM_FILE ==> "$BM_FILE
$kb cp $BM_DUMP_FILE $NAMESPACE/$BM_container:/tmp/$BM_FILE
$kb exec -it $BM_container -- sh -c 'tar -xmvf /tmp/'$BM_FILE

#$kb exec -it $BM_container -- sh -c 'cp -pr /tmp/opt/dsb/dsb-manager/config /opt/dsb/dsb-manager/'
}

RestoreMongo
RestoreBM

```
{: codeblock}

4. Open a new browser tab and log into {{site.data.keyword.security_broker_short}} Manager
    after you have finished executing the script. Verify that the original configurations of the applications, databases, and key stores have been restored.

5. For all of the applications of {{site.data.keyword.security_broker_short}} Manager, with data security policies, deploy new {{site.data.keyword.security_broker_short}} Shields by adhering to the deployment    procedures. Ensure that the Helm chart is updated with the appropriate Sync ID for each application.

6. Log into {{site.data.keyword.security_broker_short}} Manager after the {{site.data.keyword.security_broker_short}} Shield have been deployed to ensure that the newly installed {{site.data.keyword.security_broker_short}} Shields are in the **RUNNING** status.

