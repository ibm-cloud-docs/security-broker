---
copyright:
  years: 2023
lastupdated: "2023-08-22"

keywords: FAQ, set up, data protection

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# FAQs for {{site.data.keyword.security_broker_short}}
{: #sb_faqs}

This section provides answers to common questions about the {{site.data.keyword.security_broker_short}} service.
{: shortdesc}

## What is {{site.data.keyword.security_broker_short}} Manager?
{: #faq-dsb-whatis}
{: faq}

{{site.data.keyword.security_broker_short}} Manager enables encryption policies and
configurations by communicating with the {{site.data.keyword.security_broker_short}} Shield and
the desired databases. {{site.data.keyword.security_broker_short}} Manager constructs a privacy
schema that maps key IDs to data columns, thus enabling encryption in a
simplified manner. {{site.data.keyword.security_broker_short}} Shield carries out
de-identification, masking, and encryption tasks for cloud databases.

{{site.data.keyword.security_broker_short}} integrates with key management stores through a key
virtualization layer. It also provides for a local key store, so you can
use your own keys for data protection in the cloud.

## Is the instance hosted by {{site.data.keyword.security_broker_short}}?
{: #faq-host}
{: faq}

{{site.data.keyword.security_broker_short}} software is hosted entirely in the customer's
environment. {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}}
Shield may be hosted on-premises or on cloud platforms such as IBM
Cloud.

## What size instance is good for getting set up?
{: #faq-instance-size}
{: faq}

30 gigabytes are sufficient for {{site.data.keyword.security_broker_short}} Manager because it
controls the Shields and the memory needed stays static. Sizing for Data
Security Broker Shield depends on the number of shields and the number
of concurrent users.

## What are the prerequisites for installing {{site.data.keyword.security_broker_short}}?
{: #faq-prereq}
{: faq}

Make sure you meet the following requirements before configuring Data
Security Broker Manager and {{site.data.keyword.security_broker_short}} Shield:

- Admin privileges for your platform

- The user account used to log in to the {{site.data.keyword.security_broker_short}} Shield host machine must have a home directory on that system

- SSH client

- Private key pair

- Database privileges for encryption and migration

## Do {{site.data.keyword.security_broker_short}} Manager and Shield run on different instances?
{: #faq-dsb-instances}
{: faq}

Technically, it is possible for the {{site.data.keyword.security_broker_short}} Manager and
{{site.data.keyword.security_broker_short}} Shield to both run on the same host. However, it is
recommended that separate host instances are provisioned for the Data
Security Broker Manager and {{site.data.keyword.security_broker_short}} Shield, to accommodate
different workloads.

## Which OS is necessary to set up the {{site.data.keyword.security_broker_short}} Shield?
{: #faq-os}
{: faq}

{{site.data.keyword.security_broker_short}} Shield can be installed on instances running with
Ubuntu 18 for **IBM Cloud Kubernetes cluster** (IKS) or RedHat
Enterprise Linux (RHEL) 7 for **IBM Red Hat OpenShift Kubernetes
cluster** (ROKS).

## Why does an invalid certificate browser warning occasionally show up?
{: #faq-invalid-certificate}
{: faq}

Most web browsers will flag this connection as unsafe if Data Security
Broker Manager is not initialized with an HTTPS certificate. To avoid
the warning, configure HTTPS in the settings page in Data Security
Broker Manager.

## Where are the secrets submitted to {{site.data.keyword.security_broker_short}} kept?
{: #faq-secrets}
{: faq}

A secure credential store is created in MongoDB by {{site.data.keyword.security_broker_short}}
Manager. This is encrypted with a key that is configured during set up.

## Why is the Deploy Policy and Migrate Data option disabled in the {{site.data.keyword.security_broker_short}} Manager UI?
{: #faq-page-setup}
{: faq}

The application in which you are trying to perform the encryption or decryption does not have a {{site.data.keyword.security_broker_short}} Shield attached to it. Associate a {{site.data.keyword.security_broker_short}} Shield to the application before performing the encryption or decryption process.

## Where do I get the information to connect the application to {{site.data.keyword.security_broker_short}} Shield?
{: #faq-connect-app}
{: faq}

If you have self-registered Shields, they are added using the Shield Sync ID, after the application is set up. The Shield Sync ID is found in the Application side panel. 

## Are there any analytics reports?
{: #faq-analystics}
{: faq}

For this service, analytics reports are not applicable. 

## How do I debug if there are any problems?
{: #faq-debug}
{: faq}

Refer to the [Logging and Debugging in {{site.data.keyword.security_broker_short}} section](/docs/security-broker?topic=security-broker-sb_logging).

## How do I add multiple {{site.data.keyword.security_broker_short}} Shields?
{: #faq-multi-shields}
{: faq}

Yes, you can install multiple instances of the {{site.data.keyword.security_broker_short}} Shields using the IBM Cloud Catalog. Ensure that you have specified different Shield names during the installation for each Shield.

## How is the load balanced between Shield instances?
{: #faq-load-balance}
{: faq}

Load balancing between Shield instances is managed by OpenShift load balancing policies. 

## What kind of delays should I expect with the Shield acting as a proxy?
{: #faq-delay-proxy}
{: faq}

The environment, network latency, and network architecture that manage the database and CDSB components all play a role in this. The delay is only a few milliseconds.

## How do I add more users to the account?
{: #faq-user}
{: faq}

Refer to the [Adding users in {{site.data.keyword.security_broker_short}} Manager section](/docs/security-broker?topic=security-broker-sb_adding_users).

## What is the impact of encryption on indexing?
{: #faq-index-impact}
{: faq}

If the index column is encrypted, in standard encryption mode, sorting on that encrypted column will not work, by design, as the encrypted value has no relationship to the cleartext data.  All operations will work once the data is extracted from the encrypted database as the proxy will decrypt it.

## What is the impact of encryption on search?
{: #faq-search-impact}
{: faq}

For exact match searches, where a query is looking for a specific value, it will work as long as the user issuing the query is authorized since they will be able to obtain the key to decrypt the value.
For partial match searches, like wildcard searches where only a part of the ciphertext is to be identified, the search will fail as the query will run on encrypted data that has no relationship to the plaintext. 

These limitations are identical to any application encryption approach where the application makes API calls to encrypt and decrypt the data.  Both of these queries, sorting on encrypted indexes and wildcard searches, will work with the Baffle advanced encryption mode where the decryption happens in a secure way on the server side itself using Postgres extensions.

## What are some known issues with respect to Key Management services?
{: #faq-key_mgt}
{: faq}

You must have a place to store your secret key or key file. You can use IBM Key Protect. IBM Key Protect provides full encryption visibility and control, allowing you to see and manage data encryption and the entire key lifecycle from a single location. Alternatively, you can secure the information with a password,
but this reduces security, depending on the level of your password's strength.

During Keystore enrollment, {{site.data.keyword.security_broker_short}} Manager will accept a Key Protect alias that refers to a destroyed or disabled Master Key. Destroyed Keys are unusable, and {{site.data.keyword.security_broker_short}} migration will fail in this case. As a workaround, ensure that the Keystore Alias does not refer to a destroyed Master Key.
{: note}

## What if there is a performance hit?
{: #faq-perf_hit}
{: faq}

Data encryption consumes more time and resources than data decryption. This overhead is normally negligible. If the proxy (Shield) has an appropriately sized CPU and Memory, there should not be
any noticeable performance penalties. Most users experience a 10--20% reduction in the overall application performance. This can be mitigated by horizontal scaling. In the event of failure, Shield can be
horizontally scaled by adding more of them behind a load balancer.

## What if I lose my key file?
{: #faq-key_file}
{: faq}

If your key file is lost, your data is also lost. So, make a backup of your data and your key.

## What are the limitations with respect to the database operations carried out on encrypted versions of the data?
{: #faq-db_operations}
{: faq}

The information is kept in encrypted form in the database and the database engine and, consequently, the database administrator is never permitted to see the information in form of the plaintext.

Many of today's server and network technologies allow for easier configuration and implementation to minimize the impact on utilization. Implementing encryption of data in transit from endpoint to endpoint
both remotely and internally is mandatory in today's cyber risk environment.

The following are considered equality check operators and are supported:

- =
- &lt;\>
- IS NULL
- IS NOT NULL
- IN
- NOT
- JOIN (all types)
- GROUP BY
- DISTINCT

Indexes can be created on encrypted columns, but the ciphertext is used to create the index and not the underlying cleartext values.

## How do I upgrade my {{site.data.keyword.security_broker_short}} Manager?
{: #faq-upgrade_db_manager}
{: faq}

Upgrades from previous versions of {{site.data.keyword.security_broker_short}} Manager is no longer available. Any credentials that were previously stored in MongoDB, in earlier versions, cannot be
upgraded to new versions.

## What are the unsupported data types for encryption?
{: #faq-unsupported_data_types}
{: faq}
The **timestamptz** and **timetz** data types are not supported for the PostgreSQL Database in {{site.data.keyword.security_broker_short}}.








