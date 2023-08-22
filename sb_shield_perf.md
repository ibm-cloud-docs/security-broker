---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: DSB Shield, Performance

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.security_broker_short}} Shield Performance
{: #sb_shield_perf}

{{site.data.keyword.security_broker_short}} Shield is an SQL proxy that is placed between the application and the database. 
{: shortdesc}

The network latency between {{site.data.keyword.security_broker_short}} Shield and the application and between {{site.data.keyword.security_broker_short}} Shield and the database should be as low as possible, when comparted with the original latency between the application and database. The network bandwidth between {{site.data.keyword.security_broker_short}} Shield and the application and database should also match the original network bandwidth available between the application and database.

One way to minimize latency between the application and {{site.data.keyword.security_broker_short}} Shield is to directly deploy {{site.data.keyword.security_broker_short}} Shield on the application host, in cases where the number of application servers are small and where sufficient CPU and memory capacity are available on each application server, and this deployment model might be a desirable approach.

In cases where there is a high concurrent workload, a single {{site.data.keyword.security_broker_short}} Shield instance might become a bottleneck. In these situations, {{site.data.keyword.security_broker_short}} recommends deployment of multiple {{site.data.keyword.security_broker_short}} Shields behind a load balancer. Each {{site.data.keyword.security_broker_short}} Shield instance is designed to handle hundreds of concurrent connections, but the actual number of connections that each {{site.data.keyword.security_broker_short}} Shield can reasonably support depends on the resource availability of the machine.

| Goal                                                       | Deployment                                  | Use case                                                                                          |   |   |   |   |   |   |   |
|------------------------------------------------------------|---------------------------------------------|---------------------------------------------------------------------------------------------------|---|---|---|---|---|---|---|
| Minimize latency between the application and Baffle Shield | DSB Shield on the application host          | Small number of application servers and Sufficient CPU and memory capacity per application server |   |   |   |   |   |   |   |
| Prevent Baffle Shield from becoming bottleneck             | Multiple DSB Shields behind a load balancer | High concurrent workload and Resourced machines     
{: caption="Table 1. {{site.data.keyword.security_broker_short}} Shield Performance" caption-side="bottom"} 

