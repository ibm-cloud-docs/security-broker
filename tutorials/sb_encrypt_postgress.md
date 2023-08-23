---
copyright:
  years: 2023
lastupdated: "2023-08-23"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Data Encryption Services 
{: #sb_encrypt_postgress}

{{site.data.keyword.security_broker_short}} offers Data Encryption services which enables the
provisioning of {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield.
It also helps in configuring encryption or decryption rules against the IBM Cloud
Databases such as PostgreSQL to encrypt and decrypt the database records
or columns on the fly.
It also helps in migrating the existing database records, apply record or column level encryption rules.

{{site.data.keyword.security_broker_short}} supports two types of Data Encryption services. They are:

1. [Data Encryption](/docs/security-broker?topic=security-broker-sb_encrypt_data)
2. [Data Masking](/docs/security-broker?topic=security-broker-sb_masking)

## Deployment Plans in {{site.data.keyword.cloud_notm}} {{site.data.keyword.security_broker_short}}
{: #sb-deployment-plans}

When you assign and customize default Data Protection Policies with {{site.data.keyword.security_broker_short}} Manager, there are three options that you can choose to
implement your data encryption policy:

### Save Policy
{: #sb-save-policy}

**Save Policy** option is selected by default. This option saves your selected data, but does not execute encryption or data protection on your database. Your policy remains saved with the application until a new policy is saved to overwrite it. You can use the saved policy to deploy or migrate it later.

### Deploy Policy
{: #sb-deploy-policy}

**Deploy Policy** option saves your policy and deploys your configured {{site.data.keyword.security_broker_short}} Shield as a proxy for the configured database. You can connect to your {{site.data.keyword.security_broker_short}} Shield endpoint, as if it was your database endpoint, to access your database.
Any data that passes through your {{site.data.keyword.security_broker_short}} Shield proxy is
encrypted in the database, if that data is defined in your policy.

### Deploy Policy and Migrate Data
{: #sb-deploy-migrate-data}

**Deploy Policy & Migrate Data** option saves your policy, deploys it, and migrates your existing selected tables and columns through the specified {{site.data.keyword.security_broker_short}} Shield to encrypt the data. 
{{site.data.keyword.security_broker_short}} Shield acts as a proxy for the configured database, and the data is encrypted as well.

This option is disabled for applications, which does not have a {{site.data.keyword.security_broker_short}} Shield associated with it.
{: note}

## Encryption Models supported by Data Security Broker
{: #sb-encryption-models}

{{site.data.keyword.security_broker_short}} supports data encryption services that can be configured
in four main modes.

### Data Encryption
{: #sb-standard-encrypt}

{{site.data.keyword.security_broker_short}} functions as an application-level encryption (ALE) software in this mode for encrypting data on a field-level basis. This is performed using {{site.data.keyword.security_broker_short}} Manager to enumerate the data schema and enable an encryption key mapping.

### Data Tokenization
{: #sb-data-tokenization}

{{site.data.keyword.security_broker_short}} supports length preserving and data type preserving tokenization method to anonymize data at the field level databases or in semi-structured data files.

### Record Level Encryption
{: #sb-RLE}

{{site.data.keyword.security_broker_short}} can be configured for record level encryption to support multiple keys within a single column that are mapped to respective data owners or entities. This
encryption mode can be used effectively in multi-tenant or shared data environments where segmenting of the data can be challenging. In this mode, data shredding can be enabled by deleting public keys and private keys for a respective entity.

### Data Masking: 
{: #sb-data-masking}

{{site.data.keyword.security_broker_short}} can enable simplified data masking to prevent decryption of data and sensitive file information based on configuration or deleted keys. This mode can minimize data
exposure in public cloud environment and provides a better control of data exfiltration to external parties.

## Procedure
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the {{site.data.keyword.security_broker_short}} Manager, you can perform standard encryption or data masking by defining a Data Protection policy. Ensure that you complete the steps below before you can use the data encryption services offered by {{site.data.keyword.security_broker_short}}.

1. You must add a Keystore, so that the {{site.data.keyword.security_broker_short}} Manager can access and create data encryption keys (DEKs) that is used to protect your data. For more information, see [Adding a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore).

2. Connect to a database in the {{site.data.keyword.security_broker_short}} Manager. For more information, see [Connect to a Datastore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_db).

3. Enroll an Application in {{site.data.keyword.security_broker_short}} Manager. For more information, see [Enrolling an application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app).

4. Assign and customize a Default Data Protection Policy. For more information, see [Create, assign, and Customize Data Protection Policy in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_assign_policy).

5. Encrypt and Decrypt Data. For more information, see [Encrypting the data with {{site.data.keyword.security_broker_short}} on an IBM Cloud PostgreSQL Database](/docs/security-broker?topic=security-broker-sb_encrypt_data).


