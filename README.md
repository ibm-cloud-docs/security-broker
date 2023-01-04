---

copyright: 
  years: 2022, 2022
lastupdated: "2023-04-01"

keywords: security broker, read-me,

subcollection: security-broker

---

# security-broker
{: #readme-sb}

## Introduction
{: #sb_readme_intro}

IBM Cloud Data Security Broker is a complete data protection solution that secures sensitive data in enterprise databases by integrating with key management and databases to provide application-level encryption. 

Data Security Broker offers Data Protection Services which consists of two main components, namely:

Data Security Broker Manager is the administrative console for the solution that integrates with enterprise key managers and databases and manages the Data Security Broker solution components.

Data Security Broker Shield is the SQL / NOSQL proxy that functions to encrypt and decrypt data at the field or record level.

## Before you begin
{: #sb_readme_prereq}

Before you begin installing and configuring the Data Security Broker Manager and Data Security Broker Shield, ensure that you have met the following requirements:

  -  User must have an IBM Cloud account
  -  Kubernetes/ROKS cluster
  -  Create a namespace
  -  Create a IBM Key Protect or IBM Cloud Hyper Protect Crypto Services (HPCS)
  -  Create a Cloud Object Storage instance
  
## Roles
{: #sb_readme_roles}

As an IBM Cloud user, you must have the following IAM Roles to install, setup and access Data Security Broker:

| Service Name                            | Permission level       |
|-----------------------------------------|------------------------|
| Key Protect                             | Writer                 |
| Cloud Object Storage                    | Manager                |
| Kubernetes Service                      | Manager, Editor        |
| IBM Red Hat OpenShift Kubernetes Servie | Editor                 |
| Schematics                              | Manager, Administrator | 

## Required resources
{: #sb_readme_resources}

Ensure that your environment meets the following minimum system level and resource level requirements:

| Cluster                                  | Operating System       | Number of Worker nodes required |
|------------------------------------------|------------------------|---------------------------------|
| IBM Red Hat Openshift Kubernetes Cluster | RHEL7/RHEL8 and CoreOS | 2                               |
| IBM Cloud Kubernetes Cluster             | Ubuntu 18              | 2                               |

## Installing the Software
{: #sb_readme_install}

Access the IBM Cloud Catalog to install the Data Security Broker Manager and Data Security Broker Shield.

1. Install Data Security Broker Manager by following the install instructions: [Install {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_install_catalog)
2. Configure and Login to Data Security Broker Manager. For more information, see [Configure {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_configure) and [Log into {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login).
3. Create a Database, Keystore and enroll an application in Data Security Broker Manager. For more information, see [Adding a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore), [Connect to a Datastore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_db), and [Enrolling an application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app).
4. Fetch the Shield Sync ID from the Data Security Broker Manager application and provide the Shield Sync ID in the Data Security Shield installation.
5. Login to Data Security Broker Manager and start using the Data Protection Services.

## Upgrading the Software to a new version
{: #sb_readme_upgrade}

To upgrade to a new version of the Data Security Broker Manager and the Data Security Broker Shield, complete the following steps:

  1.  Log into IBM Cloud Schematic workspace (https://cloud.ibm.com/schematics/workspaces)
  2.  Search for the workspace name that you provided during the Data Security Broker Manager or Data Security Shield install and click on the workspace to open it.
  3.  Click **Settings**. In the Summary section, your version number is displayed.
  4.  If the new version is available for the Data Security Broker Manager or the Data Security Broker Shield, the **Update** button is enabled and you can click the Update button to proceed with upgrading the Data Security Broker Manager or the Data Security Broker Shield.
  5.  In the **Update Workspace resources** window, select the version of the Data Security Broker Manager or the Data Security Broker Shield, which you wish to upgrade to, and click **Update**.

**Note**: Once you click **Update**, IBM Cloud Schematic runs the terraform code in the backend to execute the newer version of the Data Security Broker Manager or the Data Security Broker Shield from the IBM Cloud Helm Catalog. After the upgrade is complete, the pods are refreshed in the namespace where you have upgraded the Data Security Broker Manager or the Data Security Broker Shield.

## Uninstlaling the Software
{: #sb_readme_uninstall}

To uninstall the Data Security Broker Manager or the Data Security Broker Shield, complete the following steps:

  1.  Log into IBM Cloud Schematic workspace (https://cloud.ibm.com/schematics/workspaces)
  2.  Search for the workspace name that you provided during the Data Security Broker Manager or Data Security Shield install and click on the workspace to open it.
  3.  Click **Actions** > **Destroy resources** to uninstall all the workloads associated with the Data Security Broker Manager or the Data Security Broker Shield.

**Note**: Once you uninstall the Data Security Broker Manager and Data Security Broker Shield workloads, you can see that the pods are being terminated and you can monitor the successfull uninstall operation through the logs.

## Source files for customer-facing documentation

Internal-only documentation: https://test.cloud.ibm.com/docs/security-broker

Customer-facing documentation: https://cloud.ibm.com/docs/security-broker









