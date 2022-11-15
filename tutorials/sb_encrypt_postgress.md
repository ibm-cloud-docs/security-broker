---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-15"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Data Protection Services Overview
{: #sb_encrypt_postgress}

## Overview:
{: #sb_encrypt_overview}

{{site.data.keyword.security_broker_short}} offers Data Protection services which enables the
provisioning of {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield and configures encryption or decryption rules against the IBM Cloud
Databases such as PostgreSQL to encrypt and decrypt the database records
or columns on the fly and migrate the existing database records, apply record or column level encryption rules.

{{site.data.keyword.security_broker_short}} supports two types of Data Protection services. They are:

1. [Data Encryption](/docs/security-broker?topic=security-broker-sb_encrypt_data)
2. [Data Masking](/docs/security-broker?topic=security-broker-sb_masking)

## Pre-requisite:
{: #sb_encrypt_prereq}

Ensure that the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}}
Shield service is installed and ready to use. For more information on
creating {{site.data.keyword.security_broker_short}} Shield service, see [Installing {{site.data.keyword.security_broker_short}} Shield](/docs/security-broker?topic=security-broker-sb_install_catalog). 
 
## Procedure:
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the {{site.data.keyword.security_broker_short}} Manager, you can perform standard encryption or data masking by defining a Data Protection policy and performing the steps below:

1. You must add a Keystore, so that the {{site.data.keyword.security_broker_short}} Manager can access and create data encryption keys (DEKs) that is used to protect your data. For more information, see [Adding a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore).

2. Connect to a database in the {{site.data.keyword.security_broker_short}} Manager. For more information, see [Connect to a Datastore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_db).

3. Enroll an Application in {{site.data.keyword.security_broker_short}} Manager. For more information, see [Enrolling an application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app).

4. Assign and customize a Default Data Protection Policy. For more information, see [Create, assign, and Customize Data Protection Policy in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_assign_policy).

5. Encrypt and Decrypt Data. For more information, see [Encrypting the data with {{site.data.keyword.security_broker_short}} on an IBM Cloud PostgreSQL Database](/docs/security-broker?topic=security-broker-sb_encrypt_data).


