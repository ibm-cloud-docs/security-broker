---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installing {{site.data.keyword.security_broker_short}}
{: #sb_install_com}

You can install {{site.data.keyword.security_broker_short}} in one of the following ways:

1.  Using the Manifests

2.  Using the HELM chart

3.  Using the {{site.data.keyword.security_broker_short}} User Interface

## Before you begin
{: #sb-install-before-you-begin}

Before you begin installing the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield, verify that you have met the following resource requirements with the help of the sizing guidelines given below:

## {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield Sizing Guidelines
{: #sb_sizing}

The factors that affect the sizing of the {{site.data.keyword.security_broker_short}} deployments consist of the {{site.data.keyword.security_broker_short}} Manager management console and one or more {{site.data.keyword.security_broker_short}} Shield proxies. Each component has its own resource needs depending on the anticipated workloads.

## {{site.data.keyword.security_broker_short}} Manager ##
{: #sb_sizing_dsbm}

In general, resources allocated to a {{site.data.keyword.security_broker_short}} Manager
deployment needs to be scaled with the number of managed Data Security
Broker Shields and the number of concurrent users using the Data
Security Broker Manager.

## Recommended sizing for Kubernetes or OpenShift Deployments: ##
{: #sb_sizing_dsbr}

{{site.data.keyword.security_broker_short}} Manager consists of four containers, each running
in its own pod.

They are:

1.  {{site.data.keyword.security_broker_short}} -mongodb is the database.

2.  {{site.data.keyword.security_broker_short}} -manager is the backend REST API service.

3.  {{site.data.keyword.security_broker_short}} -web is the front-end dashboard.

4.  {{site.data.keyword.security_broker_short}} -nginx is the load balancer.

All {{site.data.keyword.security_broker_short}} Manager pods must run in the same cluster, and
hence the cluster must be sized to accommodate the total resource needs
of the {{site.data.keyword.security_broker_short}} Manager pod and any other pods running in
the same cluster.

The sizing recommendation for each pod is as follows:

1.  {{site.data.keyword.security_broker_short}} -nginx:

    0.5 CPU, 1GB Memory

2.  {{site.data.keyword.security_broker_short}} -web:

    0.5 CPU, 1GB Memory

3.  {{site.data.keyword.security_broker_short}} -manager:

| Specification                        | Small | Medium | Large  | X-Large |
|--------------------------------------|-------|--------|--------|---------|
| Concurrent Users                     | 1-5   | 6-20   | 21-100 | 101+    |
| Shields                              | 1-5   | 6-20   | 21-100 | 101+    |
| CPU                                  | 2     | 4      | 8      | 16      |
| Memory                               | 4 GB  | 8 GB   | 16 GB  | 32 GB   |
| Minimum Space (in persistent volume) | 5 GB  | 5 GB   | 5 GB   | 5 GB    |
{: caption="Table 1. Resource level requirements for {{site.data.keyword.security_broker_short}}" Manager caption-side="bottom"} 


4.  {{site.data.keyword.security_broker_short}} -mangodb:

    For all sizes: 1 CPU, 2GB Mem

| Specification      | Small | Medium | Large  | X-Large |
|--------------------|-------|--------|--------|---------|
| Concurrent Users   | 1-5   | 6-20   | 21-100 | 101+    |
| Minimum Disk Space | 10 GB | 25 GB  | 50 GB  | 100 GB  |
{: caption="Table 2. Resource level requirements for {{site.data.keyword.security_broker_short}}" Mangodb caption-side="bottom"} 

## {{site.data.keyword.security_broker_short}} Shield ##
{: #sb_sizing_dsbs}

The general rule for {{site.data.keyword.security_broker_short}} Shield sizing, to handle peak
utilization scenarios, is to match the sum of all {{site.data.keyword.security_broker_short}}
Shield's memory and CPU allocations to that of the database instance.
The initial vCPU and memory requests for the pod installation can start
low and can be scaled up based on utilization, based on pod scaling
policies, and depending on the workload in a particular installation.
Resource allocation to {{site.data.keyword.security_broker_short}} Shield deployments typically
scales with the expected maximum number of concurrent connections.

## Recommended sizing for Kubernetes or OpenShift Deployments ##
{: #sb_sizing_dsbrs}

{{site.data.keyword.security_broker_short}} Shield consists of a single container that runs in
its own pod. The {{site.data.keyword.security_broker_short}} Shield pod can be in the same or
different cluster but must have network connectivity to Data Security
Broker Manager.

The recommendations for sizing {{site.data.keyword.security_broker_short}} Shield pods are as
follows:

| Peak Concurrent Sessions | 1-100 | 101-1000 | 1001-5000 | 5001-10,000 |
|--------------------------|-------|----------|-----------|-------------|
| CPU                      | 2     | 4        | 8         | 16          |
| Memory                   | 8 GB  | 16 GB    | 32 GB     | 64 GB       |
{: caption="Table 3. Resource level requirements for {{site.data.keyword.security_broker_short}}" Shield caption-side="bottom"}

## Installing {{site.data.keyword.security_broker_short}} through the Manifests:
{: #install-sb-com-manifests}

You can install {{site.data.keyword.security_broker_short}} on an IBM Cloud Kubernetes cluster (IKS) or an
IBM Red Hat OpenShift Kubernetes cluster (ROKS) through the manifests. For more information, see [Installing {{site.data.keyword.security_broker_short}} through Manifests](/docs/security-broker?topic=security-broker-sb_install_manifests).

## Installing {{site.data.keyword.security_broker_short}} through HELM charts:
{: #install-sb-com-helm}

You can also install {{site.data.keyword.security_broker_short}} using HELM charts. For more information, see [Installing {{site.data.keyword.security_broker_short}} using the HELM chart in CLI](/docs/security-broker?topic=security-broker-sb_install_helm).

## Installing {{site.data.keyword.security_broker_short}} through User Interface:
{: #install-sb-com-ui}

Alternatively, you can use the user interface (UI) to install the {{site.data.keyword.security_broker_short}}. For more information, see [Installing {{site.data.keyword.security_broker_short}} using the HELM chart in the UI](/docs/security-broker?topic=security-broker-sb_install_ui). 

