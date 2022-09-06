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


# Getting started with IBM Cloud Data Security Broker
{: #sb_getting_started}

IBM Cloud Data Security Broker is a complete data protection solution
that secures sensitive data in enterprise databases by fully integrating
with key management and databases to provide application-level
encryption.
{:shortdesc: .shortdesc}

Data Security Broker Data Protection Services consists of two main
components, namely:

__Data Security Broker Manager__ is the administrative console for
the solution that integrates with enterprise key managers and databases
and manages the Data Security Broker solution components.

__Data Security Broker Shield__ is the SQL / NOSQL proxy that
functions to encrypt and decrypt data at the field or record level.

Data Security Broker Manager enforces encryption policies and
configurations by:

- Communicating with key management solutions, the Security Broker Shield, and databases
- Orchestrating configuration and deployment


Data Security Broker Shield is a stateless reverse proxy that intercepts
and encrypts application data sent to the database and decrypts
encrypted data returned by the database.

Data Security Broker Data Protection Services provide a range of data
encryption, tokenization, and de-identification methods to protect data
in data stores and cloud storage environments.

## Before you begin
{: #sb-before-you-begin}

Before you begin configuring the Data Security Broker Manager and Data
Security Broker Shield, verify that you have met the following
requirements:

- Admin privileges for your platform
- The user account used to log in to the Data Security Broker Shield host machine must have a home directory on that system
- SSH client
- Private key pair
- Database privileges for encryption and migration

### System Requirements
{: #sb-system-requirements}

Ensure that your environment meets the following minimum system level and resource level requirements:

| Data Security Component Broker | Memory | Java Version     | Virtual CPU (vCPU) |
|--------------------------------|--------|------------------|--------------------|
| Data Security Broker Manager   | 8 GB   | OpenJDK Java 1.8 | 2                  |
| Data Security Broker Shield    | 8 GB   | OpenJDK Java 1.8 | 16                 |
| IBM Postgress Database         | 256 GB | OpenJDK Java 1.8 | 4                  |
{: caption="Table 1. System Requirements for Data Security Broker" caption-side="bottom"}  

| Cluster                                         | Operating System | Number of Master nodes required | Number of Worker nodes required | Number of Pods required |
|-------------------------------------------------|------------------|---------------------------------|---------------------------------|-------------------------|
| IBM Red Hat OpenShift Kubernetes cluster (ROKS) | Ubuntu 18        | 1                               | 2                               | 5                       |
| IBM Cloud Kubernetes cluster (IKS)              | RHEL 7           | 1                               | 2   
{: caption="Table 2. Resource level requirements for Data Security Broker" caption-side="bottom"}  


