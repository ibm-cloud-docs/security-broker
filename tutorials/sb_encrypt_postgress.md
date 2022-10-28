---
copyright:
  years: 2022, 2022
lastupdated: "2022-10-28"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Data Protection Services
{: #sb_encrypt_postgress}

## Overview:
{: #sb_encrypt_overview}

{{site.data.keyword.security_broker_short}} offers Data Protection services which enables the
provisioning of Security Broker Manager and Security Broker Shield and
configures encryption or decryption rules against the IBM Cloud
Databases such as PostgreSQL to encrypt and decrypt the database records
or columns on the fly and migrate the existing database records,
apply record or column level encryption rules.

## Pre-requisite:
{: #sb_encrypt_prereq}

Ensure that the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}}
Shield service is installed and ready to use. For more information on
creating {{site.data.keyword.security_broker_short}} Shield service, see [Installing {{site.data.keyword.security_broker_short}} Shield](/docs/security-broker?topic=security-broker-sb_install_com). 
 
## Procedure:
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the Data Security
Broker, you can now encrypt or decrypt the data by defining a Data
Protection policy and performing the steps below:

-   Before you can enroll your applications, add databases, and enable
    encryption, you must enroll your Keystore, so that the Security
    Broker Manager can access and create data encryption keys (DEKs)
    that is used to protect your data. For more information, see [Adding a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_encrypt_data#adding-keystore-in-data-security-broker-manager) and [Connect to a Datastore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_encrypt_data#connecting-to-a-datastore).

-   Enroll an Application in {{site.data.keyword.security_broker_short}} Manager. For more
    information, see [Enrolling an application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app).

-   Assign and customize a Default Data Protection Policy. For more
    information, see [Create, assign, and Customize Data Protection Policy in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_assign_policy).

-   Encrypt and Decrypt Data. For more information, see [Encrypting the data with {{site.data.keyword.security_broker_short}} on an IBM Cloud PostgreSQL Database](/docs/security-broker?topic=security-broker-sb_encrypt_data).

## Format Preserving Encryption (FPE) Supported Data Types:
{: #sb_encrypt_FPE_data_types}

The following tables lists the FPE supported data types by database:

**PostgreSQL**:

| **Original Data Type** | **FPE Data Type**                         |
|------------------------|-------------------------------------------|
| smallint               | fpe-int                                   |
| int                    | fpe-int                                   |
| integer                | fpe-int                                   |
| bigint                 | fpe-int                                   |
| bytea                  | fpe-int                                   |
| numeric                | fpe-decimal                               |
| decimal                | fpe-decimal                               |
| numeric (s,p)          | fpe-decimal                               |
| decimal (s,p)          | fpe-decimal                               |
| money                  | fpe-decimal                               |
| var                    | - fpe-decimal - fpe-alphanum - fpe-latin1 |
| char                   | - fpe-win1252 - fpe-cc                    |
| text                   | - fpe-email1 - fpe-email2                 |
| date                   | fpe-datetime                              |
| time                   | fpe-datetime                              |
| timestamp              | fpe-datetime                              |
| uuid                   | fpe-hexadecimal                           |
{: caption="Table 1. FPE Supported Data Types caption-side="bottom"}

## Counter-Mode (CTR) Supported Data Types:
{: #sb_encrypt_CTR_data_types}

**Note**: {{site.data.keyword.security_broker_short}} Shield only supports one word for a data type name.
**BYTEA** is a PostgreSQL data type that has the capability to store hexadecimal data which is used to store encrypted data. **BYTEA** is an equivalent of **VARBINARY** in **MySQL** or **RAW** datatype in **Oracle** database.

**PostgreSQL**:
The following table lists PostgreSQL supported data types for M_CTR mode in {{site.data.keyword.security_broker_short}} Manager. 

| **Original Data Type**                                                            | **Encrypted Data Type** |   |
|-----------------------------------------------------------------------------------|-------------------------|---|
| SMALLINT                                                                          | BYTEA                   |   |
| INT, INTEGER                                                                      | BYTEA                   |   |
| BIGINT                                                                            | BYTEA                   |   |
| REAL, FLOAT4                                                                      | BYTEA                   |   |
| FLOAT8 - Used in Data Security Broker Shield  for "double precision"              | BYTEA                   |   |
| DECIMAL, NUMERIC                                                                  | BYTEA                   |   |
| VARCHAR - Used in Data Security Broker Shield for "character verification"        | BYTEA                   |   |
| CHAR, CHARACTER, BPCHAR                                                           | BYTEA                   |   |
| TEXT                                                                              | BYTEA                   |   |
| JSON, JSONB                                                                       | BYTEA                   |   |
| BYTEA                                                                             | BYTEA                   |   |
| MONEY                                                                             | BYTEA                   |   |
| DATE                                                                              | BYTEA                   |   |
| TIMESTAMP - Used in Data Security Broker Shield for "timestamp without time zone" | BYTEA                   |   |
| TIMESTAMPZ - Used in Data Security Broker Shield for "timestamp with time zone"   | BYTEA                   |   |
| UUID                                                                              | BYTEA                   |   |
| BIT                                                                               | BYTEA                   |   |
| VARBIT - Used in Data Security Broker Shield for "bit verification"               | BYTEA                   |   |
{: caption="Table 2. CTR Supported Data Types caption-side="bottom"}
