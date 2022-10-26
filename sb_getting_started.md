---
copyright:
  years: 2022, 2022
lastupdated: "2022-10-26"

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


# Getting started with Data Security Broker
{: #sb_getting_started}

{{site.data.keyword.security_broker_full_notm}} is a complete data protection solution
that secures sensitive data in enterprise databases by fully integrating
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

{{site.data.keyword.security_broker_short}} offers Data Protection Services which provide a range of data
encryption, tokenization, and de-identification methods to protect data in data stores and cloud storage environments.

## Before you begin
{: #sb-before-you-begin}

Before you begin configuring the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, verify that you have met the following requirements:

- Create an IBM Cloud account.
- Database privileges for encryption and migration.

### System Requirements
{: #sb-system-requirements}

Ensure that your environment meets the following minimum system level and resource level requirements:

| Cluster                                         | Operating System | Number of Master nodes required | Number of Worker nodes required | Number of Pods required |
|-------------------------------------------------|------------------|---------------------------------|---------------------------------|-------------------------|
| IBM Red Hat OpenShift Kubernetes cluster (ROKS) | Ubuntu 18        | 1                               | 2                               | 5                       |
| IBM Cloud Kubernetes cluster (IKS)              | RHEL 7           | 1                               | 2                               | 5
{: caption="Table 2. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

## Assign permissions for IBM Cloud credentials to access {{site.data.keyword.security_broker_short}} ##
{: #sb_getting_assign_permission}

As an IBM Cloud user, you need minimum permissions to setup and access {{site.data.keyword.security_broker_short}}. 
By using the following steps and the information in the table, assign the required permissions:
1. Log into your IBM Cloud account and click **Manage -> Access (IAM)**.
2. In the Manage access and users dashboard, click **View all** in the **My user details** section.
3. In the **Access** tab, click **Assign access +**. From the Table 1, select a service and click **Next**.
4. In the **Roles and actions** section, select the specified permissions that are required.
5. Click **Add** and **Assign** to assign the permissions required.

| Service Name                            | Permission level |
|-----------------------------------------|------------------|
| Key Protect                             | Writer           |
| Cloud Object Storage                    | Manager          |
| Kubernetes Service                      | Editor           |
| IBM Red Hat OpenShift Kubernetes Servie | Editor           |
{: caption="Table 1. Permissions required for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}

## Next Steps
{: #sb_getting_next_steps}

Include the flow here.....
