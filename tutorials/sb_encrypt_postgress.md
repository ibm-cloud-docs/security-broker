---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-20"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# How to define a Data Protection Policy and encrypt Data?
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
creating Data Security Broker Shield service, see **Link to**
**Installing Data Security Broker**.

## Procedure:
{: #sb_encrypt_procedure}

After you have completed setting up and configuring the Data Security
Broker, you can now encrypt or decrypt the data by defining a Data
Protection policy and performing the steps below:

-   Before you can enroll your applications, add databases, and enable
    encryption, you must enroll your Keystore, so that the Security
    Broker Manager can access and create data encryption keys (DEKs)
    that is used to protect your data. For more information, see **Link
    to step 2 and step 3 in Encrypting the data with Security Broker on
    an IBM Cloud PostgreSQL Database section.**

-   Enroll an Application in Data Security Broker Manager. For more
    information, see **Link to Enroll an application section.**

-   Assign and customize a Default Data Protection Policy. For more
    information, see **Link to Assign and customize a Default Data
    Protection Policy section.**

-   Encrypt and Decrypt Data. For more information, see **Link to
    Encrypt and Decrypt Data section.**

## Enrolling an Application in Data Security Broker Manager:
{: #sb_encrypt_app}

An application is the framework that links Security Broker Manager,
databases, and Security Broker Shield and instructs the Security Broker
Shield to encrypt and decrypt data.

 **Note**: A Security Broker Shield can only be enrolled with one
application.

To enroll an application in Security Broker Manager, complete the
following steps:

1.  Click the **Application** icon in the left navigation panel.

2.  Click **+APPLICATION** in the upper right corner of the window. The
    Enroll Application dialog appears.

3.  Enter an **Application Name** and **Application Description** in the
    respective fields.

4.  Perform the following tasks:\
    -- Choose the Security Broker **Shield** from the drop-down list. \
    -- Select a **Data Store** for encryption.\
    -- Select the **Keystore** to be used as a source for data
    encryption keys.  \
    -- Leave Workload Capture **Off**, unless profiling an
    application.  \
    -- Specify an **Encryption Method**, Column Level or Row Level. 

5.  Click **Enroll Application**.

## Assigning or changing a Default Data Protection Policy:
{: #sb_encrypt_dp}

**Overview:**

A Data Protection Policy consists of a combination of encryption modes
and masking rules. Default Data Protection Policies allow you to
apply default settings for encryption, Format Preserving Encryption
(FPE), or Data Masking, A policy is applied to the columns of a data
store associated with an application enrolled in Data Security Broker
Manager and linked to a Data Security Broker Shield. 

A list of Default Data Protection Policies is available in the Data
Protection Library at the bottom of the left navigation bar. Click **the
carrot icon (\<)** to expand and view the list of list **Default Data
Protection Policies, Encryption Modes, and Masking Modes.**

Need to insert screenshot

#### **To assign or change a Default Data Protection Policy, do the following:**


1.  In Data Security Broker Manager, click the **Application** icon in
    the left menu bar.

screenshot required

2.  Select an application from the list and click **Encrypt**.

screenshot required

3.  In the left navigation menu, navigate to a database and schema and
    select the table for which you want to assign or change a policy.
    The table appears on the right.

screenshot required

4.  Click the checkbox for a column and then expand the **Data
    Protection** drop-down list. By default, CTR Policy is selected.

screenshot required

5.  Perform one of the following operations:
    -- Accept the default policy or select a different default policy.
    -- Specify a new default policy and add an encryption or masking
    mode.

**Note**: Default Policy rules are **overwritten** by individual mode
selections. However, because the Default FPE policy contains only
encryption modes, and the Default Masking Policy contains only Masking
modes, selecting the opposite mode will not affect the default policy.
For example: 

-   If you select Default FPE and any Mask Mode, both are applied to
    that column.

-   If you select Default FPE and any other FPE mode, (like FPE-cc), the
    FPE-cc option **overwrites the** Default FPE option for that
    column. 

6.  Select a **Key ID** from the drop-down menu or accept the default.

7.  Click **REVIEW** at the bottom of the left panel to review your
    selections.

8.  Review your policy and select a **Migration Plan**\
    -- **Save**: Defines a policy for future migration.\
    -- **Deploy**: Establishes a data schema for an environment that was
    not processed through Data Security Broker migration and the data
    type conversion but does not migrate the data.\
    -- **Deploy and Migrate**: Defines a policy *and* migrates the
    existing data in the data store.

## Encrypting the data with Security Broker on an IBM Cloud PostgreSQL Database:
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

