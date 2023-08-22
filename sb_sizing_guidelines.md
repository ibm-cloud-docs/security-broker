---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: sizing guidelines, manager, broker, minumum sizing

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

## Sizing Guidelines
{: #sb_sizing_guidelines}

The factors that affect the sizing of the {{site.data.keyword.security_broker_short}} deployments consist of the {{site.data.keyword.security_broker_short}} Manager management console and one or more {{site.data.keyword.security_broker_short}} Shield proxies. Each component has its own resource needs depending on the anticipated workloads.

## {{site.data.keyword.security_broker_short}} Manager
{: #sb_sizing_dsbm}

In general, resources allocated to a {{site.data.keyword.security_broker_short}} Manager
deployment needs to be scaled with the number of managed {{site.data.keyword.security_broker_short}} Shields and the number of concurrent users using the {{site.data.keyword.security_broker_short}} Manager.

## {{site.data.keyword.security_broker_short}} Shield
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

## Minimum system requirements for deploying in {{site.data.keyword.cloud_notm}} Kubernetes cluster (IKS) or {{site.data.keyword.redhat_openshift_full}} Kubernetes (ROKS) cluster:
{: #sb_sizing_dsbr}

| Product                            | Container/service | IKS/ROKSVersion             | vCPU | Memory | Disk Space                       |
|------------------------------------|-------------------|-----------------------------|------|--------|----------------------------------|
| Data Security Broker (DSB) Manager | DSB-manager       | IKS v 1.17+, ROKS v 4.8.54+ | 4    | 8 GB   | 5 GB                             |
| Data Security Broker (DSB) Shield  | DSB-shield        | IKS v 1.17+, ROKS v 4.8.54+ | 2    | 8 GB   | (No persistent volume necessary) |
{: caption="Table 2. Sizing guidelines" caption-side="bottom"}

## Next Steps
{: #sb_getting_next_steps}

After the environment is set up and you have the required roles and permissions, and sizing guidelines defined,  you can start setting installing the {{site.data.keyword.security_broker_short}} by following the instructions in the [Installing {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_install_catalog) section.
