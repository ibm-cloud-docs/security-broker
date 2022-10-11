---
copyright:
  years: 2022, 2022
lastupdated: "2022-10-11"

keywords: FAQ, setup, data protection

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


# Frequently asked questions (FAQ)
{: #sb_faqs}

This FAQ provides answers to common questions about the {{site.data.keyword.security_broker_short}} service.
{: shortdesc}

**What is Data Security Broker Manager?**

Data Security Broker Manager enables encryption policies and
configurations by communicating with the Data Security Broker Shield and
the desired databases. Data Security Broker Manager constructs a privacy
schema that maps key IDs to data columns, thus enabling encryption in a
simplified manner. Data Security Broker Shield carries out
de-identification, masking, and encryption tasks for cloud databases.

Data Security Broker integrates with key management stores through a key
virtualization layer. It also provides for a local key store, so you can
use your own keys for data protection in the cloud.

**Is the instance hosted by Data Security Broker?**

Data Security Broker software is hosted entirely in the customer's
environment. Data Security Broker Manager and Data Security Broker
Shield may be hosted on-premises or on cloud platforms such as IBM
Cloud.

**What size instance is good for getting set up?**

30 gigabytes are sufficient for Data Security Broker Manager because it
controls the Shields and the memory needed stays static. Sizing for Data
Security Broker Shield depends on the number of shields and the number
of concurrent users.

**What are the prerequisites for installing Data Security Broker?**

Make sure you meet the following requirements before configuring Data
Security Broker Manager and Data Security Broker Shield:

* Admin privileges for your platform

* The user account used to log in to the Data Security Broker Shield host machine must have a home directory on that system

* SSH client

* Private key pair

* Database privileges for encryption and migration

**Do Data Security Broker Manager and Shield run on different instances?**

Technically, it is possible for the Data Security Broker Manager and
Data Security Broker Shield to both run on the same host. However, it is
recommended that separate host instances are provisioned for the Data
Security Broker Manager and Data Security Broker Shield, to accommodate
different workloads.

**Which OS is necessary to setup the Data Security Broker Shield?**

Data Security Broker Shield can be installed on instances running with
Ubuntu 18 for **IBM Cloud Kubernetes cluster** (IKS) or RedHat
Enterprise Linux (RHEL) 7 for **IBM Red Hat OpenShift Kubernetes
cluster** (ROKS).

**Why does an invalid certificate browser warning occasionally show up?**

Most web browsers will flag this connection as unsafe if Data Security
Broker Manager is not initialized with an HTTPS certificate. To avoid
the warning, configure HTTPS in the settings page in Data Security
Broker Manager.

**Where are the secrets submitted to Data Security Broker kept?**

A secure credential store is created in MongoDB by Data Security Broker
Manager. This is encrypted with a key that is configured during setup.

**Why is the Deploy Policy and Migrate Data option disabled in the Data Security Broker Manager UI?**



**Where do I get the information to connect the application to Baffle Shield?**

If you have self-registered Shields, they are added using the Shield Sync ID, after the application is set up. The Shield Sync ID is found in the Application side panel. 

**Are there any analytics reports?**

For this service, analytics reports are not applicable. 

**How do I debug if there are any problems?**

Refer to the [Logging and Debugging in {{site.data.keyword.security_broker_short}} section](/docs/security-broker?topic=security-broker-sb_logging).

**How do I add multiple Baffle Shields?**

For containerized, self-registered Shields, replicas can be configured in the YAML file and pointed to the Manager application by using the same Shield Sync ID. Horizontal scaling can be enabled to deploy multiple Shields. For standalone Shields, additional Shields can be added to a Manager application through the UI.

**How is the load balanced between Shield instances?**

Load balancing between Shield instances is managed by OpenShift load balancing policies. 

**What are the Postgres data types that are not supported by Baffle?**

Only _timestamptz_ and _timetz_ are unsupported. 

**What kind of delays should I expect with the Shield acting as a proxy?**

The environment, network latency, and network architecture that manage the database and CDSB components all play a role in this. The delay is only a few milliseconds.

**How do I add more users to the account?**

Refer to the [Adding users in {{site.data.keyword.security_broker_short}} Manager section](/docs/security-broker?topic=security-broker-sb_adding_users).

**How do I add users without SMTP accounts?**

You can choose "Get invite link" to create a URL that can be shared through any messaging service. 


