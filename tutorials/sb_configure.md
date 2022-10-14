---
copyright:
  years: 2022, 2022
lastupdated: "2022-10-14"

keywords: database, admin, priveleges, users, configure, operations

subcollection: security-broker
---

# Configuring Data Security Broker Manager
{: #sb_configure}

Configuring the Data Security Broker Manager console is the first step
in implementing data protection services.

## **Prerequisites:**
{: #sb_configure_prereq}

Before you begin configuring Data Security Broker, ensure you meet the
following requirements:

1.  Create IBM Keys Authentication -- For more information, see
    [Creating and importing encryption
    keys](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).

2.  Create a Key Protect instance -- For more information, see [Creating
    and importing encryption
    keys](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).

3.  Create a Cloud Object Store (COS) -- For more information, see
    the [IBM Cloud Object
    Storage](https://www.ibm.com/cloud/object-storage).

4.  Create HMAC keys on the COS -- For more information, see [IBM Cloud
    Object Storage](https://www.ibm.com/cloud/object-storage).

## To configure Data Security Broker Manager, perform the following steps:
{: #sb_configure_overview}

1.  Make a note of the **load_balancer_url** in the Terraform output.

2.  Open a browser window and enter the **load_balancer_url **from the
    Terraform output. You will receive a **Your connection is not
    private** warning.

3.  Click **Advanced**, then click the **Proceed to link** at the bottom
    of the page.

4.  The **Getting Started** dialog to unlock Data Security Broker
    Manager appears.

5.  Configure Basic System Settings by entering the hostname and domain
    settings and click **Continue**.

6.  Configure Email Settings to allow Data Security Broker Manager to
    send emails to provide notifications and for password resets. Enter
    the SMTP server to use as well as the credential to use to
    authenticate to the SMTP server, then click **Continue**.

7.  Create an Admin Account for the initial Data Security Broker Manager
    administrator. This account is used to configure the subsequent
    components such as the key management store, data store connections,
    and Data Security Broker Shields. Enter the Admin user information
    and click **Continue**.

8.  Configure Credential Keystore to establish an encrypted credential
    store for any system access credential or access key that the Data
    Security Broker Manager or Data Security Broker Shield utilize. Select **LOCAL** for Keystore type.  Enter the **Data Security Broker** **Secret Key** in the text field. 

**Note**: The Data Security Broker Secret Key must contain at least 10
characters, a mixture of upper and lower case, including at least* *1
number. The Secret Key is used to generate a random key to encrypt the
Keystore Config Password.  For **Config Password**, enter a secure
password or passphrase to secure the actual keystore.

9.  **Install SSL Certificate** for secure access to the Data Security
    Broker Manager web interface. Upload the certificate and key file
    for your organization or respective cloud account to enable SSL for
    the Data Security Broker Manager console.

10. Enter the login credentials for the Data Security Broker Admin
    account you created in the Data Security Broker Manager interface
    and click **SIGN IN**. 
