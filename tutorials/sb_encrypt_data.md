---
copyright:
  years: 2023
lastupdated: "2023-08-30"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Data Encryption using IBM Cloud Databases for PostgreSQL
{: #sb_encrypt_data}

## Overview
{: #sb_se_overview}

{{site.data.keyword.security_broker_short}} functions as an application-level encryption (ALE) equivalent in this mode encrypting data on a field-level basis. This is performed using {{site.data.keyword.security_broker_short}} Manager to enumerate the data schema and enable an encryption key mapping.

## Procedure
{: #sb_se_procedure}



Complete the following steps to encrypt the data with {{site.data.keyword.security_broker_short}} Manager on
an IBM Cloud PostgreSQL Database:

1. Login to {{site.data.keyword.security_broker_short}} Manager.
2. Click on an application and select the drop down which is present in the **Migration Details** field in the right side and click **Encrypt**.
3. Select the Database and the table where you have the data created and select the **Column** which needs to be encrypted. Choose the **Data Protection** policy, **Encryption mode**, and **masking mode** for the encryption process and click **Review**.
   ![Data Encryption](../images/encryption.svg "Data Encryption"){: caption="Data Encryption" caption-side="center"}
4. Choose **Deploy Policy & Migrate Data** under the **Deployment Plan** option. There are three options that you can choose to implement your data encryption policy. For more information on Deployment plans, see [Deployment Plans in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_encrypt_postgress#sb-deployment-plans). Select the Security Broker Shield service IP address in the **Migration Shield** field and click **Save** to start the encryption process.

5. The status of the application shows **Migrating** when the encryption process starts.

6. Once the encryption is complete, the status is changed to **Protected**. You can view more information by clicking **Migration Details** in the **Applications** sidebar.

If there is new data which gets inserted in the database, by default, the data is encrypted by using the default data encryption policy that is being selected by the user.
{: note}

## Reference
{: #sb_encrypt_FPE_data_types_reference}

## Format Preserving Encryption (FPE) Supported Data Types
{: #sb_encrypt_FPE_data_types}

The following tables lists the FPE supported data types for the data encryption in {{site.data.keyword.security_broker_short}} Manager:

## PostgreSQL
{: #sb_encrypt_db_psl}

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

## Counter-Mode (CTR) Supported Data Types
{: #sb_encrypt_CTR_data_types}

{{site.data.keyword.security_broker_short}} Shield only supports one word for a data type name.
**BYTEA** is a PostgreSQL data type that has the capability to store hexadecimal data which is used to store encrypted data. **BYTEA** is an equivalent of **VARBINARY** in **MySQL** or **RAW** datatype in **Oracle** database.
{: note}

**PostgreSQL**
The following table lists PostgreSQL supported data types for M_CTR mode in {{site.data.keyword.security_broker_short}} Manager. 

| **Original Data Type**                                                            | **Encrypted Data Type** |   |
|-----------------------------------------------------------------------------------|-------------------------|---|
| SMALLINT                                                                          | BYTEA                   |   |
| INT, INTEGER                                                                      | BYTEA                   |   |
| BIGINT                                                                            | BYTEA                   |   |
| REAL, FLOAT4                                                                      | BYTEA                   |   |
| FLOAT8 - Used in {{site.data.keyword.security_broker_short}} Shield  for "double precision"              | BYTEA                   |   |
| DECIMAL, NUMERIC                                                                  | BYTEA                   |   |
| VARCHAR - Used in {{site.data.keyword.security_broker_short}} Shield for "character verification"        | BYTEA                   |   |
| CHAR, CHARACTER, BPCHAR                                                           | BYTEA                   |   |
| TEXT                                                                              | BYTEA                   |   |
| JSON, JSONB                                                                       | BYTEA                   |   |
| BYTEA                                                                             | BYTEA                   |   |
| MONEY                                                                             | BYTEA                   |   |
| DATE                                                                              | BYTEA                   |   |
| TIMESTAMP - Used in {{site.data.keyword.security_broker_short}} Shield for "timestamp without time zone" | BYTEA                   |   |
| TIMESTAMPZ - Used in {{site.data.keyword.security_broker_short}} Shield for "timestamp with time zone"   | BYTEA                   |   |
| UUID                                                                              | BYTEA                   |   |
| BIT                                                                               | BYTEA                   |   |
| VARBIT - Used in {{site.data.keyword.security_broker_short}} Shield for "bit verification"               | BYTEA                   |   |
{: caption="Table 2. CTR Supported Data Types caption-side="bottom"}







