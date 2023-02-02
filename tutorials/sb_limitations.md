---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Known issues (Limitations)
{: #sb_limitations}

Use this topic to find the details of the limitations that are applicable to the {{site.data.keyword.security_broker_short}} software.

## Application-level Encryption:
{: #sb_app_level}

{{site.data.keyword.security_broker_short}} encryption gives database applications a no-code
way to implement application-level encryption. Application-level
encryption can be implemented by including a database proxy that
intercepts and encrypts sensitive data in accordance with the
pre-established data protection policy.

{{site.data.keyword.security_broker_short}} encryption has some restrictions, like any other approaches to the application-level encryption implementation. 
The various aspects of the application level encryption limitations are explained below:

**Performance hit**: Data encryption consumes more time and resources
than data decryption. This overhead is normally negligible. If the proxy
(Shield) has an appropriately sized CPU and Memory, there should not be
any noticeable performance penalties. Most users experience a 10--20%
reduction in the overall application performance. This can be mitigated
by horizontal scaling. In the event of failure, Shield can be
horizontally scaled by adding more of them behind a load balancer.

**Key management**: You must have a place to store your secret key or
key file. You can use IBM Key Protect. IBM Key Protect provides full encryption visibility and control,
allowing you to see and manage data encryption and the entire key lifecycle from a single location. Alternatively, you can secure the information with a password,
but this reduces security, depending on the level of your password's
strength.

**Accessibility**: If your key file is lost, your data is also lost. So,
make a backup of your data and your key.

**Database operations carried out on encrypted versions of the data**:
The information is kept in encrypted form in the database and the
database engine and, consequently, the database administrator is never
permitted to see the information in form of the plaintext.

Many of today's server and network technologies allow for easier
configuration and implementation to minimize the impact on utilization.
Implementing encryption of data in transit from endpoint to endpoint
both remotely and internally is mandatory in today's cyber risk
environment.

The following are considered equality check operators and are supported:

* =
* &lt;\>
* IS NULL
* IS NOT NULL
* IN
* NOT
* JOIN (all types)
* GROUP BY
* DISTINCT

Indexes can be created on encrypted columns, but the ciphertext will be
used to create the index and not the underlying cleartext values.

## Unsupported Data Types
{: #sb_unsupported_data_types}

Only **timestamptz** and **timetz** data types are not supported for the PostgreSQL Database in {{site.data.keyword.security_broker_short}}. 
