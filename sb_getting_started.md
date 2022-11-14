---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-14"

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


# Getting started with IBM Cloud Data Security Broker
{: #sb_getting_started}

{{site.data.keyword.security_broker_full_notm}} is a complete data protection solution
that secures sensitive data in enterprise databases by integrating
with key management and databases to provide application-level
encryption.
{: shortdesc}

{{site.data.keyword.security_broker_short}} offers Data Protection Services which consists of two main
components, namely:

__{{site.data.keyword.security_broker_short}} Manager__ is the administrative console for
the solution that integrates with enterprise key managers and databases
and manages the {{site.data.keyword.security_broker_short}} solution components.

__{{site.data.keyword.security_broker_short}} Shield__ is the SQL / NOSQL proxy that
functions to encrypt and decrypt data at the field or record level.

{{site.data.keyword.security_broker_short}} Manager enforces encryption policies and
configurations by:

- Communicating with key management solutions, the {{site.data.keyword.security_broker_short}} Shield, and databases.
- Orchestrating configuration and deployment.

{{site.data.keyword.security_broker_short}} Shield is a stateless reverse proxy that intercepts
and encrypts application data sent to the database and decrypts encrypted data returned by the database.

{{site.data.keyword.security_broker_short}} offers Data Protection Services which provide a range of data protection services such as data encryption, data tokenization, record level encryption, and data masking.

## Before you begin
{: #sb-before-you-begin}

Before you begin installing and configuring the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, ensure that you have met the following requirements:

- Create an IBM Cloud account.
- Database privileges for performing encryption.

### System Requirements
{: #sb-system-requirements}

Ensure that your environment meets the following minimum system level and resource level requirements:
| Cluster                                  | Operating System       | Number of Worker nodes required |
|------------------------------------------|------------------------|---------------------------------|
| IBM Red Hat Openshift Kubernetes Cluster | RHEL7/RHEL8 and CoreOS | 2                               |
| IBM Cloud Kubernetes Cluster             | Ubuntu 18              | 2                               |
{: caption="Table 2. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

## Minimum permissions required to install, setup, and  access {{site.data.keyword.security_broker_short}} ##
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
{: caption="Table 1. Permissions required for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}

## Next Steps
{: #sb_getting_next_steps}

Now that the software is installed on your cluster, you can start protecting your data by following the steps mentioned in the flow diagram below:

![Encryption flow in {{site.data.keyword.security_broker_short}}](images/sb_flow.svg){: caption="Figure 1. Encyrption flow in {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}
