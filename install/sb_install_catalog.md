---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-03"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installating Data Security Broker Manager and Data Security Broker Shield
{: #sb_install_catalog}

## Overview:
{: #sb_install_ui_overview}

You can install the {{site.data.keyword.security_broker_short}} software by using the IBM Cloud Catalog. Refer to this link to access the {{site.data.keyword.security_broker_short}} in the IBM Cloud Catalog:
<https://cloud.ibm.com/catalog/content/ibmcloud-security-broker> (Need
to correct the link when the software is available in the Catalog).

## Pre-requisites:
{: #sb_install_ui_prereq}

-   User must have an active IBM Cloud Account

-   User must be able to access the IBM Cloud Kubernetes cluster (IKS)
    or IBM Red Hat OpenShift Kubernetes cluster (ROKS) cluster

## Before you begin
{: #sb-install-before-you-begin}

Before you begin installing the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, verify that you have met the following resource requirements with the help of the sizing guidelines given below:

## Data Security Broker Manager and Data Security Broker Shield Sizing Guidelines
{: #sb_sizing}

The factors that affect the sizing of the Data Security Broker deployments consist of the Data Security Broker Manager management console and one or more Data Security Broker Shield proxies. Each component has its own resource needs depending on the anticipated workloads.

## Data Security Broker Manager ##
{: #sb_sizing_dsbm}

In general, resources allocated to a Data Security Broker Manager
deployment needs to be scaled with the number of managed Data Security
Broker Shields and the number of concurrent users using the Data
Security Broker Manager.

## Recommended sizing for Kubernetes or OpenShift Deployments: ##
{: #sb_sizing_dsbr}

Data Security Broker Manager consists of four containers, each running
in its own pod.

They are:

1.  Data Security Broker -mongodb is the database.

2.  Data Security Broker -manager is the backend REST API service.

3.  Data Security Broker -web is the front-end dashboard.

4.  Data Security Broker -nginx is the load balancer.

All Data Security Broker Manager pods must run in the same cluster, and
hence the cluster must be sized to accommodate the total resource needs
of the Data Security Broker Manager pod and any other pods running in
the same cluster.

The sizing recommendation for each pod is as follows:

1.  Data Security Broker -nginx:

    0.5 CPU, 1GB Memory

2.  Data Security Broker -web:

    0.5 CPU, 1GB Memory

3.  Data Security Broker -manager:

| Specification                        | Small | Medium | Large  | X-Large |
|--------------------------------------|-------|--------|--------|---------|
| Concurrent Users                     | 1-5   | 6-20   | 21-100 | 101+    |
| Shields                              | 1-5   | 6-20   | 21-100 | 101+    |
| CPU                                  | 2     | 4      | 8      | 16      |
| Memory                               | 4 GB  | 8 GB   | 16 GB  | 32 GB   |
| Minimum Space (in persistent volume) | 5 GB  | 5 GB   | 5 GB   | 5 GB    |
{: caption="Table 1. Resource level requirements for {{site.data.keyword.security_broker_short}}" Manager caption-side="bottom"} 


4.  Data Security Broker -mangodb:

    For all sizes: 1 CPU, 2GB Mem

| Specification      | Small | Medium | Large  | X-Large |
|--------------------|-------|--------|--------|---------|
| Concurrent Users   | 1-5   | 6-20   | 21-100 | 101+    |
| Minimum Disk Space | 10 GB | 25 GB  | 50 GB  | 100 GB  |
{: caption="Table 2. Resource level requirements for {{site.data.keyword.security_broker_short}}" Mangodb caption-side="bottom"} 

## Data Security Broker Shield ##
{: #sb_sizing_dsbs}

The general rule for Data Security Broker Shield sizing, to handle peak
utilization scenarios, is to match the sum of all Data Security Broker
Shield's memory and CPU allocations to that of the database instance.
The initial vCPU and memory requests for the pod installation can start
low and can be scaled up based on utilization, based on pod scaling
policies, and depending on the workload in a particular installation.
Resource allocation to Data Security Broker Shield deployments typically
scales with the expected maximum number of concurrent connections.

## Recommended sizing for Kubernetes or OpenShift Deployments ##
{: #sb_sizing_dsbrs}

Data Security Broker Shield consists of a single container that runs in
its own pod. The Data Security Broker Shield pod can be in the same or
different cluster but must have network connectivity to Data Security
Broker Manager.

The recommendations for sizing Data Security Broker Shield pods are as
follows:

| Peak Concurrent Sessions | 1-100 | 101-1000 | 1001-5000 | 5001-10,000 |
|--------------------------|-------|----------|-----------|-------------|
| CPU                      | 2     | 4        | 8         | 16          |
| Memory                   | 8 GB  | 16 GB    | 32 GB     | 64 GB       |
{: caption="Table 3. Resource level requirements for {{site.data.keyword.security_broker_short}}" Shield caption-side="bottom"}

## Procedure:
{: #sb_install_ui_procedure}

1.  Log into the IBM Cloud Account (https://cloud.ibm.com) with a valid username and password.

2.  Click **Catalog**. Enter **{{site.data.keyword.security_broker_short}}** in the **Catalog**
    search text box. A list of products appears in the Catalog.

3.  To sort the products using the type, click **Software** in the **Type** option, which is present in the left-hand navigation of the Catalog.

4.  You will find two catalog items for **{{site.data.keyword.security_broker_short}}**-Manager and **{{site.data.keyword.security_broker_short}}**-Shield as a result of the Catalog search.

5. You must install the **{{site.data.keyword.security_broker_short}}**-Manager first and then get the Shield Sync ID from the **{{site.data.keyword.security_broker_short}}**-Manager to install the **{{site.data.keyword.security_broker_short}}** Shield.

## Install **{{site.data.keyword.security_broker_short}}**-Manager:
{: #sb_install_dsbm}

Complete the following steps to insall the **{{site.data.keyword.security_broker_short}}** Manager from the IBM Cloud Catalog:

1.  Click **{{site.data.keyword.security_broker_short}}**-Manager catalog item.

2.  In the **Select your deployment target** drop down, select **IBM Cloud Kubernetes service** or **Red    Hat Openshift**.

3.  Select **HELM chart** as the delivery method for installation in the **Select a delivery method** drop down.

4.  Select the product version.



8.  Set the deployment values and Click **Install** to complete the installation process.

## Configure **{{site.data.keyword.security_broker_short}}** Manager:
{: #install-catalog-configure}

You must configuring the Data Security Broker Manager console before installing the **{{site.data.keyword.security_broker_short}}** Shield. See [Configuring {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_configure) to complete the configuration of the **{{site.data.keyword.security_broker_short}}** Manager and access the **{{site.data.keyword.security_broker_short}}** Manager console.

## Login to **{{site.data.keyword.security_broker_short}}** Manager:
{: #install-catalog-login}

Login to the **{{site.data.keyword.security_broker_short}}** Manager using the steps mentioned in the [Logging into {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login) section. 

## Enroll an application in the **{{site.data.keyword.security_broker_short}}** Manager:
{: #install-catalog-enroll}

Refer to the [Enrolling an Application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app) to enroll the application in the **{{site.data.keyword.security_broker_short}}** Manager.

## Install **{{site.data.keyword.security_broker_short}}** Shield:
{: #sb_install_ui_procedure}

Complete the following steps to insall the **{{site.data.keyword.security_broker_short}}** Shield from the IBM Cloud Catalog:

(Need to complete the steps here....Work in progress)



