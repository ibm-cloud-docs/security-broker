---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Data Protection Services 
{: #sb_encrypt_postgress}

{{site.data.keyword.security_broker_short}} offers Data Protection services which enables the
provisioning of {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield.
It also helps in configuring encryption or decryption rules against the IBM Cloud
Databases such as PostgreSQL to encrypt and decrypt the database records
or columns on the fly.
It also helps in migrating the existing database records, apply record or column level encryption rules.

{{site.data.keyword.security_broker_short}} supports two types of Data Protection services. They are:

1. [Data Encryption](/docs/security-broker?topic=security-broker-sb_encrypt_data)
2. [Data Masking](/docs/security-broker?topic=security-broker-sb_masking)

## Procedure:
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the {{site.data.keyword.security_broker_short}} Manager, you can perform standard encryption or data masking by defining a Data Protection policy and performing the steps below:

1. You must add a Keystore, so that the {{site.data.keyword.security_broker_short}} Manager can access and create data encryption keys (DEKs) that is used to protect your data. For more information, see [Adding a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore).

2. Connect to a database in the {{site.data.keyword.security_broker_short}} Manager. For more information, see [Connect to a Datastore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_db).

3. Enroll an Application in {{site.data.keyword.security_broker_short}} Manager. For more information, see [Enrolling an application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app).

4. Assign and customize a Default Data Protection Policy. For more information, see [Create, assign, and Customize Data Protection Policy in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_assign_policy).

5. Encrypt and Decrypt Data. For more information, see [Encrypting the data with {{site.data.keyword.security_broker_short}} on an IBM Cloud PostgreSQL Database](/docs/security-broker?topic=security-broker-sb_encrypt_data).


