---
copyright:
  years: 2023
lastupdated: "2023-08-23"

keywords: support, getting started, data protection, data threats, Data Security Broker

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Getting started with IBM Cloud Security and Compliance Center Data Security Broker
{: #getting-started}

## Overview
{: #sb_getting_started_overview}

Protect your data in the cloud with the {{site.data.keyword.security_broker_full_notm}}, which is a complete data encryption solution that secures sensitive data in enterprise databases by integrating
with key management and databases to provide application-level encryption.
{: shortdesc}

{{site.data.keyword.security_broker_short}} is a software that makes data breaches irrelevant by ensuring data remains encrypted, not only when it is stored but also when it is being processed by databases and applications. 

{{site.data.keyword.security_broker_short}} offers Data encryption services which consists of two main
components, namely:

**IBM Cloud Security and Compliance Center Data Security Broker Manager** is the administrative console for
the solution that integrates with enterprise key managers and databases and manages the {{site.data.keyword.security_broker_short}} solution components.

**IBM Cloud Security and Compliance Center Data Security Broker Shield** is the SQL proxy that functions to encrypt and decrypt data at the field or record level.

**{{site.data.keyword.security_broker_short}} Manager** enforces encryption policies and
configurations by:

- Communicating with key management solutions, the {{site.data.keyword.security_broker_short}} Shield, and databases.
- Orchestrating configuration and deployment.

**{{site.data.keyword.security_broker_short}} Shield** is a stateless proxy that intercepts
and encrypts application data sent to the database and decrypts encrypted data.

{{site.data.keyword.security_broker_short}} provide a range of data encryption services such as data encryption, data tokenization, record level encryption, and data masking.

{{site.data.keyword.security_broker_short}} supports only PostgreSQL database.
{: note}

## Setting up your environment
{: #sb-setting_up_environment}

### Before you begin
{: #sb-before-you-begin}

Before you begin installing and configuring the {{site.data.keyword.security_broker_short}}, ensure that you have met the following requirements:

- Create an {{site.data.keyword.cloud_notm}} account.
- Set up your environment.
- Set up the minimum permissions required in the {{site.data.keyword.cloud_notm}} account.

Ensure that your environment meets the following minimum system level and resource level requirements:

| Cluster                                  | Operating System       | Number of Worker nodes required |
|------------------------------------------|------------------------|---------------------------------|
| {{site.data.keyword.redhat_openshift_full}} cluster | RHEL7/RHEL8 and CoreOS | 2                               |
| {{site.data.keyword.cloud_notm}} Kubernetes cluster             | Ubuntu 18              | 2                               |
{: caption="Table 1. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

### Minimum permissions required to install, set up, and  access {{site.data.keyword.security_broker_short}}
{: #sb_getting_assign_permission}

As an {{site.data.keyword.cloud_notm}} user, you need to set the follwoing minimum permissions to install, set up and access {{site.data.keyword.security_broker_short}}. 
By using the following steps and the information in the table, assign the required permissions:
1. Log into your {{site.data.keyword.cloud_notm}} account and click **Manage -> Access (IAM)**.
2. In the Manage access and users dashboard, click **View all** in the **My user details** section.
3. In the **Access** tab, click **Assign access +**. From the Table 2, select a service and click **Next**.
4. In the **Roles and actions** section, select the specified permissions that are required.
5. Click **Add** and **Assign** to assign the permissions required.

| Service Name                            | Permission level       |
|-----------------------------------------|------------------------|
| {{site.data.keyword.keymanagementserviceshort}}                             | Writer                 |
| {{site.data.keyword.cos_full}}                   | Manager                |
| {{site.data.keyword.containershort}}                     | Manager, Editor        |
| IBM {{site.data.keyword.redhat_openshift_notm}} {{site.data.keyword.containershort}} | Editor                 |
| {{site.data.keyword.bpshort}}                              | Manager, Administrator | 
{: caption="Table 3. Permissions required for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}

You can find details about platform roles and the actions mapped to each of the role in the table below: 

| Platform Roles | Description                                                                                                                                                        |   |   |   |
|:--------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| Administrator  | As an administrator, you can  perform all platform actions based on the resource this role is being  assigned, including assigning access policies to other users. |   |   |   |
| Editor         | As an editor, you can perform all platform actions except for managing the account and assigning access policies.                                                  |   |   |   |
| Operator       | As an operator, you can  perform platform actions required to configure and operate service  instances, such as viewing a service's dashboard.                     |   |   |   |
| Viewer         | As a viewer, you can view service instances, but you can't modify them.                                                                                            |   |   |   |
{: caption="Table 4. Platform roles and their actions" caption-side="bottom"}

## Sizing Guidelines
{: #sb_sizing_guidelines}

The factors that affect the sizing of the {{site.data.keyword.security_broker_short}} deployments consist of the {{site.data.keyword.security_broker_short}} Manager management console and one or more {{site.data.keyword.security_broker_short}} Shield proxies. Each component has its own resource needs depending on the anticipated workloads.

### {{site.data.keyword.security_broker_short}} Manager
{: #sb_sizing_dsbm}

In general, resources allocated to a {{site.data.keyword.security_broker_short}} Manager
deployment needs to be scaled with the number of managed {{site.data.keyword.security_broker_short}} Shields and the number of concurrent users using the {{site.data.keyword.security_broker_short}} Manager.

### {{site.data.keyword.security_broker_short}} Shield
{: #sb_sizing_dsbs}

The general rule for {{site.data.keyword.security_broker_short}} Shield sizing, to handle peak
utilization scenarios, is to match the sum of all {{site.data.keyword.security_broker_short}} Shield's memory and CPU allocations to that of the database instance. 
The initial vCPU and memory requests for the pod installation can start
low and can be scaled up based on utilization, based on pod scaling
policies, and depending on the workload in a particular installation.
Resource allocation to {{site.data.keyword.security_broker_short}} Shield deployments typically
scales with the expected maximum number of concurrent connections.

{{site.data.keyword.security_broker_short}} Shield consists of a single container that runs in
its own pod. The {{site.data.keyword.security_broker_short}} Shield pod can be in the same or
different cluster but must have network connectivity to {{site.data.keyword.security_broker_short}} Manager.

### Minimum system requirements for deploying in {{site.data.keyword.cloud_notm}} Kubernetes cluster (IKS) or {{site.data.keyword.redhat_openshift_full}} Kubernetes (ROKS) cluster:
{: #sb_sizing_dsbr}

| Product                            | Container/service | IKS/ROKSVersion             | vCPU | Memory | Disk Space                       |
|------------------------------------|-------------------|-----------------------------|------|--------|----------------------------------|
| Data Security Broker (DSB) Manager | DSB-manager       | IKS v 1.17+, ROKS v 4.8.54+ | 4    | 8 GB   | 5 GB                             |
| Data Security Broker (DSB) Shield  | DSB-shield        | IKS v 1.17+, ROKS v 4.8.54+ | 2    | 8 GB   | (No persistent volume necessary) |
{: caption="Table 2. Sizing guidelines" caption-side="bottom"}

After the environment is set up and you have the required roles and permissions, and sizing guidelines defined,  you can start setting installing the {{site.data.keyword.security_broker_short}} by following the instructions in the [Installing {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_install_catalog) section.

## Next Steps
{: #overview-next steps}

Now that you have an understanding of the various entities that exist within {{site.data.keyword.security_broker_short}}, and that you have setup the environment to install the {{site.data.keyword.security_broker_short}}, the following diagram details the user flows that you might be helpful when you are working with {{site.data.keyword.security_broker_short}}.

![Encryption flow](images/dsb_flowchart.svg){: caption="Figure 1. User Workflow" caption-side="bottom"}
