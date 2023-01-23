---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: database, admin, priveleges, users, configure, operations, keyprotect

subcollection: security-broker
---

# Configure IBM Key Protect
{: #sb_ibm_keyprotect}

In this section, you can find details on how to configure IBM Key Protect and add it as a keystore in {{site.data.keyword.security_broker_short}} Manager.

## Overview
{: #sb_ibm_keyprotect_overview}

The [IBM® Key Protect for IBM Cloud®](https://www.ibm.com/cloud/key-protect) service enables you to
provision and store encrypted keys across your IBM Cloud environment. IBM Key Protect provides full encryption visibility and control, allowing you to see and manage data encryption and the entire key
lifecycle from a single location.

## Procedure
{: #sb_ibm_keyprotect_procedure}

Complete the following steps to configure IBM Key Protect. After
completing this procedure, you can add IBM Key Protect as a keystore in
{{site.data.keyword.security_broker_short}} Manager.

## **To configure IBM Key Protect, do the following:**
{: #sb_configure_keyprotect_procedure}

1.  Get an IBM Instance ID in one of the following ways:

    -   Using the IBM CLI -- enter the following command in a shell
        window:\
        **ibmcloud resource service-instance \'Key Protect-dsb-1\'**

    -   Using the IBM Cloud web console -- navigate to **Services and
        software** and select the Key Protect instance. The GUID is
        displayed in the sidebar, and  is what you use for the
        instanceID.

2.  Create and retrieve API Key, in the following way: 

    -   Open a web browser and navigate
        to:[https://cloud.ibm.com/iam/apikeys](https://cloud.ibm.com/iam/apikeys).

    -   Select **Create an IBM Cloud API Key** and name the key.

    -   Copy or download the key after it's created.

3.  Create Cloud Object Storage in the resource group.

4.  Create a Bucket in the COS instance, for example: bm-ibm-bucket

5.  Generate Service Credentials for the COS Bucket.

6.  In Object Storage, click on **Service Credentials **in the side
    panel. Then click **New Credential**.

7.  Enable HMAC and click **Add**.

## **Add IBM Key Protect as a keystore in {{site.data.keyword.security_broker_short}} Manager**
{: #sb_configure_keyprotect_add}

Complete the following steps to complete the process for using IBM Key
Protect as a keystore in {{site.data.keyword.security_broker_short}} Manager.

**To add IBM Key Protect as a keystore, perform the following steps:**

1.  In the {{site.data.keyword.security_broker_short}} Manager console, click the key icon in
    the left navigation bar. The Keystore window appears.** **

2.  Click **+Keystore**. The Add Keystore dialog appears.

3.  Enter a keystore Name and select **IBM Key Protect **in the Keystore
    Type drop-down menu.

4.  Enter the Instance ID, that you have created for the **KeyProtect
    Instance**.

5.  For **App Namespace**, enter a string to identify the application.

6.  For** IBM Key Protect Alias**, enter a unique string value.

7.  For the **IAM API Key**, use the key that you have created.

8.  For **IBM region**, specify the region for the IBM Key Protect
    instance.

9.  For the IBM Cloud Object Storage URL, specify the IBM endpoint URL
    for COS, for
    example: https://s3.us-south.cloud-object-storage.appdomain.cloud

10. Enter the **cos_hmac_keys** for the Access Key ID and Secret Key.

11. Click **Add Keystore**.
    Note: The key will not appear in IBM Key Protect until Data Security
    Broker Shield has been connected and data encryption migration has
    occurred.


