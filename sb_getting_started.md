---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-01"

keywords: support, getting started, data protection, data threats

subcollection: security-broker
---

{:codeblock: .codeblock}
{:screen: .screen}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:tip: .tip}
{:preview: .preview}
{:deprecated: .deprecated}
{:beta: .beta}
{:term: .term}
{:shortdesc: .shortdesc}
{:script: data-hd-video='script'}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:help: data-hd-content-type='help'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:java: .ph data-hd-programlang='java'}
{:javascript: .ph data-hd-programlang='javascript'}
{:swift: .ph data-hd-programlang='swift'}
{:curl: .ph data-hd-programlang='curl'}
{:video: .video}
{:step: data-tutorial-type='step'}
{:tutorial: data-hd-content-type='tutorial'}
{:release-note: data-hd-content-type='release-note'}


# Getting started with IBM Cloud {{site.data.keyword.security_broker_short}}
{: #getting_started}

Protect your data in the cloud with the {{site.data.keyword.security_broker_full_notm}}, which is a complete data protection solution that secures sensitive data in enterprise databases by integrating
with key management and databases to provide application-level encryption.
{: shortdesc}

## Before you begin
{: #sb-before-you-begin}

Before you begin installing and configuring the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, ensure that you have met the following requirements:

- Create an IBM Cloud account.
- Setup your environment.
- Setup the minimum permissions required in the IBM Cloud account.

### Setting up your environment
{: #sb-system-requirements}

Ensure that your environment meets the following minimum system level and resource level requirements:

| Cluster                                  | Operating System       | Number of Worker nodes required |
|------------------------------------------|------------------------|---------------------------------|
| IBM Red Hat Openshift Kubernetes Cluster | RHEL7/RHEL8 and CoreOS | 2                               |
| IBM Cloud Kubernetes Cluster             | Ubuntu 18              | 2                               |
{: caption="Table 1. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

## Setting up minimum permissions required to install, setup, and  access {{site.data.keyword.security_broker_short}} ##
{: #sb_getting_assign_permission}

As an IBM Cloud user, you need to set the follwoing minimum permissions to install, setup and access {{site.data.keyword.security_broker_short}}. 
By using the following steps and the information in the table, assign the required permissions:
1. Log into your IBM Cloud account and click **Manage -> Access (IAM)**.
2. In the Manage access and users dashboard, click **View all** in the **My user details** section.
3. In the **Access** tab, click **Assign access +**. From the Table 1, select a service and click **Next**.
4. In the **Roles and actions** section, select the specified permissions that are required.
5. Click **Add** and **Assign** to assign the permissions required.

| Service Name                            | Permission level       |
|-----------------------------------------|------------------------|
| Key Protect                             | Writer                 |
| Cloud Object Storage                    | Manager                |
| Kubernetes Service                      | Manager, Editor        |
| IBM Red Hat OpenShift Kubernetes Servie | Editor                 |
| Schematics                              | Manager, Administrator | 
{: caption="Table 2. Permissions required for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}

You can find more information about {{site.data.keyword.security_broker_short}} in the [About {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_about) section.

## Next Steps
{: #sb_getting_next_steps}

After the enrironment is setup and you have the required roles and permissions, you can start installing the {{site.data.keyword.security_broker_short}} by following the instructions in the [Installing {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_install_catalog) section.

The flow diagram below explains the work flow that the user has to follow to encrypt the data using {{site.data.keyword.security_broker_short}}:

![Encryption flow in {{site.data.keyword.security_broker_short}}](images/sb_userflow.svg){: caption="Figure 1. Encyrption flow in {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}
