---
copyright:
  years: 2023
lastupdated: "2023-08-23"

keywords: uninstall, delete, helm, configuration, tls certificate, docker config secret, environment variable, regions, cluster, container, app security, memory encryption, data in use

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Uninstalling through IBM Cloud Catalog
{: #sb_uninstall}

If you no longer need to use {{site.data.keyword.security_broker_short}}, you can uninstall all the workloads that are associated with the {{site.data.keyword.security_broker_short}} using the [IBM Cloud Schematics workspace](https://cloud.ibm.com/schematics/workspaces).
{: shortdesc}

## Pre-requisite
{: #unistall-prereq}

The user must be aware of the workspace name which is provided during the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield installation process.

## Uninstalling {{site.data.keyword.security_broker_short}} Manager
{: #unistall-sb-IKS}

Log into IBM Cloud Schematics workspace and follow the steps below to uninstall the {{site.data.keyword.security_broker_short}} Manager:

1. Search for the workspace name that you provided during the {{site.data.keyword.security_broker_short}} Manager install and click on the workspace to open it.

2. Select **Actions** -> **Destroy Resources** to destroy the workloads associated with the {{site.data.keyword.security_broker_short}} Manager.   

3. Follow the same process for the {{site.data.keyword.security_broker_short}} Shield to uninstall the workloads associated with the {{site.data.keyword.security_broker_short}} Shield. Remember to work with the correct workspace name, which is provided during the {{site.data.keyword.security_broker_short}} Shield install.

Once you uninstall the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield workloads, you can see that the pods are being terminated and you can monitor the successfull uninstall operation through the logs.
