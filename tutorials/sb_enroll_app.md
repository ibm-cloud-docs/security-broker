---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: database, admin, priveleges, users, features, operations, application

subcollection: security-broker
---

# Enrolling an Application in {{site.data.keyword.security_broker_short}} Manager
{: #sb_enroll_app}

An application is the framework that links {{site.data.keyword.security_broker_short}} Manager,
databases, and {{site.data.keyword.security_broker_short}} Shield and instructs the {{site.data.keyword.security_broker_short}} Shield to encrypt and decrypt data.

A {{site.data.keyword.security_broker_short}} Shield is limited to be enrolled with one application. But you can associate one application with multiple {{site.data.keyword.security_broker_short}} Shields.
{: note}

To enroll an application in Security Broker Manager, complete the following steps:

1. Log in to {{site.data.keyword.security_broker_short}} Manager.
2. Click the **Applications** icon in the left navigation panel.

3. Click **Enroll Application +** in the upper right corner of the window. The **Enroll Application** dialog appears.

4. Enter an **Application Name** and **Application Description** in the
    respective fields.

5. Perform the following tasks:
   - Choose the {{site.data.keyword.security_broker_short}} Shield from the drop-down list.
   - Select a **Data Store** for encryption.
   - Select the **Keystore** to be used as a source for data encryption keys.  
   - Specify an **Encryption Method** as Column Level or Row Level. 
 
6. Click **Enroll Application**. After the application is enrolled, it is displayed under the Applications in the {{site.data.keyword.security_broker_short}} Manager.

   The Shield Sync ID is used when you install {{site.data.keyword.security_broker_short}} Shield. Ensure that you have the Shield Sync ID handy during the {{site.data.keyword.security_broker_short}} Shield installation.
   {: note}

7. Once you have completed enrolling an application, you can proceed with the data encyrption. Refer to the [Data Encryption using IBM Cloud PostgreSQL Database](/docs/security-broker?topic=security-broker-sb_encrypt_data) section to start protecting your data.

