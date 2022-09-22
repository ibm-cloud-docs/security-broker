---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Data Encryption using Data Security Broker
{: #sb_encrypt_postgress}

## Overview:
{: #sb_encrypt_overview}

Data Security Broker offers Data Protection services which enables the
provisioning of Security Broker Manager and Security Broker Shield and
configures encryption or decryption rules against the IBM Cloud
Databases such as PostgreSQL to encrypt and decrypt the database records
or columns on the fly and migrate the existing database records,
apply record or column level encryption rules.

## Pre-requisite:
{: #sb_encrypt_prereq}

Ensure that the Data Security Broker Manager and Data Security Broker
Shield service is installed and ready to use. For more information on
creating Data Security Broker Shield service, see [Installing Data Security Broker Shield](/docs/security-broker/install?topic=sb_install_com). 
 
## Procedure:
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the Data Security
Broker, you can now encrypt or decrypt the data by defining a Data
Protection policy and performing the steps below:

-   Before you can enroll your applications, add databases, and enable
    encryption, you must enroll your Keystore, so that the Security
    Broker Manager can access and create data encryption keys (DEKs)
    that is used to protect your data. For more information, see [Adding a Keystore in Data Security Broker Manager](/docs/security-broker/tutorials?topic=sb_encrypt_data#step2) and [Connect to a Datastore in Data Security Broker Manager](/docs/security-broker/tutorials?topic=sb_encrypt_data#step3).

-   Enroll an Application in Data Security Broker Manager. For more
    information, see [Enrolling an application in Data Security Broker Manager](/docs/security-broker/tutorials?topic=sb_enroll_app).

-   Assign and customize a Default Data Protection Policy. For more
    information, see [Create, assign, and Customize Data Protection Policy in Data Security Broker Manager](/docs/security-broker/tutorials?topic=sb_data_policy).

-   Encrypt and Decrypt Data. For more information, see [Encrypting the data with Security Broker on an IBM Cloud PostgreSQL Database](/docs/security-broker/tutorials?topic=sb_encrypt_data).
