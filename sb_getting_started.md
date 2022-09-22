---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

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


# Getting started with {{site.data.keyword.security_broker_full}}
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

Before you begin configuring the Data Security Broker{{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, verify that you have met the following requirements:

- Admin privileges for your platform
- The user account used to log in to the Data Security Broker Shield host machine must have a home directory on that system
- SSH client
- Private key pair
- Database privileges for encryption and migration

### System Requirements
{: #sb-system-requirements}

Ensure that your environment meets the following minimum system level and resource level requirements:

| {{site.data.keyword.security_broker_short}} Component | Memory | Java Version     | Virtual CPU (vCPU) |
|--------------------------------|--------|------------------|--------------------|
| Data Security Broker Manager   | 8 GB   | OpenJDK Java 1.8 | 2                  |
| Data Security Broker Shield    | 8 GB   | OpenJDK Java 1.8 | 16                 |
| IBM Postgress Database         | 256 GB | OpenJDK Java 1.8 | 4                  |
{: caption="Table 1. System Requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

| Cluster                                         | Operating System | Number of Master nodes required | Number of Worker nodes required | Number of Pods required |
|-------------------------------------------------|------------------|---------------------------------|---------------------------------|-------------------------|
| IBM Red Hat OpenShift Kubernetes cluster (ROKS) | Ubuntu 18        | 1                               | 2                               | 5                       |
| IBM Cloud Kubernetes cluster (IKS)              | RHEL 7           | 1                               | 2   
{: caption="Table 2. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  


