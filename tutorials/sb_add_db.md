---
copyright:
  years: 2022, 2023
lastupdated: "2023-03-07"

keywords: database, admin, priveleges, users, features, operations, application

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Connecting to a Datastore
{: #sb_add_db}

To add and connect to a data store, complete the following steps in the {{site.data.keyword.security_broker_short}} Manager:

1. Login to {{site.data.keyword.security_broker_short}} Manager.

2. Select **Databases** from the left navigation and click **Add Database +** to add a data store.

3. In the **Add Database** dialog, enter a name and description for the database in the **Database Name** and **Database Description** fields.

4. Select the database type as **Postgres** from the **Database Type** drop-down list.

5. Enter the IP address of the database in the **Hostname or IP Address** field.

6. Specify the **Port** for the database and enter the user **Database Username** and **Database Credential**.

7. Create a new user on your database for use with IBM Cloud Security Broker. For more information, see [Database Privileges](/docs/security-broker?topic=security-broker-sb_db_priveleges) section.
   
8. You can use only a **Postgres** database and enter your database name in the **Postgres Database Name** field.
    
9. **Optional**: Select **Use SSL**, click **Add file**, and upload an SSL Certificate.

10. Click **Add Database** to complete enrolment. The new database appears in the list of configured databases.

11. Create the data that is required for encryption or decryption as tables in the new database that is created.

12. Once you have completed adding a database, the next step is to connect to a keystore. Refer to the [Add a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore) section to connect to a keystore in the {{site.data.keyword.security_broker_short}} Manager. 

