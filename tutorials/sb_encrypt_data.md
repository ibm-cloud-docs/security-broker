---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Encrypting the data with {{site.data.keyword.security_broker_short}} on an IBM Cloud PostgreSQL Database
{: #sb_encrypt_ibm_postgress}

Complete the following steps to encrypt the data with Security Broker on
an IBM Cloud PostgreSQL Database:

1.  Login to Security Broker Manager by specifying the Security Broker
    admin user and password.

Insert screen shot when ready

2.  Before you can enroll your applications, add databases, and enable
    encryption, you must enroll your Keystore, so that the Security
    Broker Manager can access and create data encryption keys (DEKs)
    that is used to protect your data. Follow the steps below to enroll
    a Keystore that you can use with Security Broker Shields and
    databases.

a)  Select **Keystores** from the left navigation and click
    **+Keystore**.

b)  Specify a name for the Keystore in the **Keystore name** field and
    provide a valid description in the **Description** field.

c)  Select the Keystore Type as **IBM Key Protect** from the **Keystore
    Type** dropdown menu. Enter values for the **Instance ID**, **App
    Namespace**, **IBM Key Protect Alias**, and **IAM API Key**. Select
    the region in the **IBM Region** drop down and choose the Data
    Encryption Key (DEK) Storage type from the **DEK Storage Type** drop
    down. For information on how to create encryption keys, see
    [Creating and importing encryption
    keys](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).

**Note**: Keystore parameters are specific to each Keystore type or
vendor. Each of the following keystores has a specific set of required
credentials and parameters.

d)  Click **Add Keystore** to create a Keystore.
{: #step2}

3.  To add and connect to a data store, complete the following steps:

a)  Select **Databases** from the left navigation and click **Add
    Database +** to add a data store.

b)  In the **Add Database** dialog, enter a name and description for the
    database in the **Database Name** and **Database Description**
    fields.

c)  Select the database type as **Postgres** from the **Database Type**
    drop-down list.

d)  Enter the IP address of the database in the **Hostname or IP
    Address** field.

e)  Specify the **Port** for the database and enter the user **Database
    Username** and **Database Credential**.

**Note**:

-   Create a new user on your database for use with IBM Cloud Security
    Broker. For more information, see **Database Privileges** (Provide
    link to Database Privileges topic).

-   For IBM Cloud use a **Postgres** database and enter your database
    name in the **Postgres Database Name** field.

f)  Optional: Select **Use SSL**, click **Add file**, and upload an SSL
    Certificate.

g)  Click **Add Database** to complete enrolment. The new database
    appears in the list of configured databases.

h)  Create the data that is required for encryption or decryption as
    tables in the new database that is created.
    {: #step3}

4.  An application is the framework that links Security Broker Manager,
    databases, and Security Broker Shield and instructs the Security
    Broker Shield to encrypt and decrypt data. Complete the steps below
    for enrolling an application in Security Broker Manager:

a)  Select the **Applications** icon in the left navigation panel and
    click **Enroll Application +**. The **Enroll Application** dialog
    appears.

b)  Enter the name and description for the application in the
    **Application Name** and **Application Description** fields.

c)  Select a **Data Store** for encryption.

d)  Select the **Keystore** to be used as a source for data encryption
    keys.

e)  To perform column level encryption, select **Column level** from the
    **Encryption Method** drop down list.

f)  To perform record level encryption, select **Record Level** as the
    **Encryption Method**. Click **Upload Entity Schema**, select your
    TOML BES file, and click **Open** and upload the entity schema file.

**Note**: You must select **RLE** as the Key ID for data that uses
record level encryption as an Encryption Method. From the **Key ID**
drop-down menu, select **RLE**. You must select RLE as the Key ID for
all the required records to ensure that that the record level
encryption is applied to all the required records in the table.

g)  Click **Enroll Application**.


5.  Click on an application and select the drop down which is present in
    the **Migration Details** field in the right side and click
    **Encrypt**.

Insert screen shot when ready


6.  Select the Database and the table where you have the data created
    and select the **Column** which needs to be encrypted. Choose the
    **Data Protection** policy, **Encryption mode**, and **masking
    mode** for the encryption process and click **Review.** For more
    details on the encryption and data protection policies, refer to
    **Encryption and Data Protection Modes in Security Broker** section
    (Provide a link to the Encryption and Data Protection Modes in Data
    Security Broker table which is present in the About the service
    topic).

Insert screen shot when ready


7.  Choose **Deploy Policy & Migrate Data** under the **Deployment
    Plan** option. There are three options that you can choose to
    implement your data encryption policy. For more information on
    Deployment plans, see **Deployment Plans in IBM Cloud Data Security
    Broker (**Provide a link to the deployment plan section present in
    the About the service topic**)**. Select the Security Broker Shield
    service IP address in the **Migration Shield** field and click
    **Save** to start the encryption process.

8.  The status of the application shows **Migrating** when the
    encryption process starts.

9.  Once the encryption is complete, the status is changed to
    **Protected**. You can view more information by clicking **Migration
    Details** in the **Applications** sidebar.

Insert screen shot when ready


**Note**: If there is new data which gets inserted in the database, by
default, the data is encrypted by using the default data encryption
policy that is being selected by the user.


