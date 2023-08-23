---
copyright:
  years: 2023
lastupdated: "2023-08-23"

keywords: support, getting started, data protection, data threats, Data Security Broker

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Getting started with IBM Cloud Security and Compliance Center Data Security Broker
{: #getting_started}

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


