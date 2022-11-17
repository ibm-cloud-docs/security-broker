---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-17"

keywords: database, admin, priveleges, users, configure, operations

subcollection: security-broker
---

# Configure Data Security Broker Manager
{: #sb_configure}

Configuring the {{site.data.keyword.security_broker_short}} Manager console is the first step
in implementing the data protection services.

## **Prerequisites:**
{: #sb_configure_prereq}

Before you begin configuring {{site.data.keyword.security_broker_short}}, ensure you meet the
following requirements:

1.  Create IBM Keys Authentication -- For more information, see
    [Creating and importing encryption
    keys](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).

2.  Create a Cloud Object Store (COS) -- For more information, see
    the [IBM Cloud Object
    Storage](https://www.ibm.com/cloud/object-storage).

## To configure {{site.data.keyword.security_broker_short}} Manager, perform the following steps:
{: #sb_configure_overview}

1.  Make a note of the **load_balancer_url** from the Terraform output of the {{site.data.keyword.security_broker_short}} install.

2.  Open a browser window and enter the **load_balancer_url** from the
    Terraform output. You will receive a **Your connection is not private** warning.

3.  Click **Advanced**, then click the **Proceed to link** at the bottom of the page.

4.  The **Getting Started** dialog to proceed with the configuration of the {{site.data.keyword.        security_broker_short}} Manager appears.

5.  Configure Basic System Settings by entering the hostname and domain settings and click **Continue**.

6.  Configure Email Settings to allow Data Security Broker Manager to
    send emails to provide notifications and for password resets. Enter the SMTP server to use as well as the credential to use to authenticate to the SMTP server, and click **Continue**.

7.  Create an Admin Account for the initial Data Security Broker Manager administrator. This account is   used to configure the subsequent components such as the keystore, data store connections,
    and {{site.data.keyword.security_broker_short}} Shields. Enter the Admin user information
    and click **Continue**.

8.  Configure Credential Keystore to establish an encrypted credential store for any system access credential or access key that the {{site.data.keyword.security_broker_short}} Manager or {{site.data.keyword.security_broker_short}} Shield utilize. Select **LOCAL** for Keystore type. Enter the **Data Security Broker** **Secret Key** in the text field. 

**Note**: The Data Security Broker Secret Key must contain at least 10 characters, a mixture of upper and lower case, including at least one numeric character. The Secret Key is used to generate a random key to encrypt the Keystore Config Password. For **Config Password**, enter a secure
password or passphrase to secure the actual keystore.

9. Login to the **{{site.data.keyword.security_broker_short}}** Manager using the steps mentioned in the [Logging into {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login) section.
