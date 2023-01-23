---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: database, admin, priveleges, users, configure, operations, keyprotect

subcollection: security-broker
---

# Configure IBM Cloud Hyper Protect Crypto Services (HPCS)
{: #sb_hpcs}

In this section, you can find details on how to configure HPCS and add [IBM Cloud Hyper Protect Crypto Services (HPCS)](https://www.ibm.com/cloud/hyper-protect-crypto) as a keystore in {{site.data.keyword.security_broker_short}} Manager.

## Overview
{: #sb_hpcs_overview}

[IBM Cloud Hyper Protect Crypto Services](https://www.ibm.com/cloud/hyper-protect-crypto) offers a cloud hardware security module (HSM) and key management service. It aims to give you control over your cloud hardware security models and cloud data encryption keys as it is the only service in the market built on FIPS 140-2 Level 4-certified hardware.

The HPCS service, which is based on IBM LinuxONE technology, helps to guarantee that only you have access to your keys. Using a dedicated customer-controlled HSM that provides single-tenant key management and key vaulting makes it simple to create encryption keys. You can also bring your own encryption keys to manage instead.


## Configure HPCS instance:
{: #sb_configure_hpcs}

Configure IBM Cloud Hyper Protect Crypto Services by following the steps below.

1. Get an IBM HPCS Instance ID in one of the following ways:
    * Using the IBM CLI – Login to your IBM CLI and execute the following command: 

```sh
ibmcloud resource service-instance 'HPCS-DSB-1'
```
{: codeblock}

**Note**: If you are using the IBM Cloud web console, navigate to **Services and Software** and select the HPCS instance. The **GUID** is displayed in the sidebar and the **instanceID** is the same as the **GUID**.
2. Create and retrieve API Key, in the following way: 
    a) Open a  web browser and navigate to [https://cloud.ibm.com/iam/apikeys](https://cloud.ibm.com/iam/apikeys).
    b) Select **Create an IBM Cloud API Key** and provide a name for the key.
    c) Copy or download the key after it is created.
3. Create Cloud Object Storage in the resource group.
4. Create a Bucket in the COS instance, for example:  **dsb-ibm-bucket**
5. Generate Service Credentials for the COS Bucket.
6. In Object Storage, click on **Service Credentials** in the side panel. Click **New Credential**.
7. Enable **HMAC** and click **Add**.
8. The next step is to add the IBM Cloud Hyper Protect Crypto Services as a keystore in {{site.data.keyword.security_broker_short}} Manager.


## Add IBM Cloud Hyper Protect Crypto Services as a keystore in {{site.data.keyword.security_broker_short}} Manager
{: #sb_add_hpcs_DSB}

You can add the IBM Cloud Hyper Protect Crypto Services instance as a keystore in {{site.data.keyword.security_broker_short}} Manager by completing the following steps.

1. Log into {{site.data.keyword.security_broker_short}} Manager.
2. Select **Keystores** from the left navigation and click **Add Keystore +**.
3. Specify a name for the Keystore in the **Keystore name** field and provide a valid description in the **Description** field and select **IBM Cloud Hyper Protect Crypto Services** in the **Keystore Type** drop-down list.
4. Enter the Instance ID for the HPCS KeyProtect Instance, which is obtained from the Step 1 in configuring the HPCS instance.
5. For App Namespace, enter a string to identify the application.
6. For IBM Cloud Hyper Protect Crypto Services Alias, get the Alias name of the Key which has been created in the HPCS instance.
7. For the IAM API Key, use the key you created using Step 2 in Configuring the HPCS section.
8. For IBM region, specify the region for the IBM Cloud Hyper Protect Crypto Services instance. See [Available IBM region listing](https://docs.baffle.io/v1/docs/configure-ibm-key-protect-and-add-it-as-a-keystore-baffle#available-ibm-region-listing) for more information.
9. For the IBM Cloud Object Storage URL, specify the IBM endpoint URL for COS, for example: https://s3.us-south.cloud-object-storage.appdomain.cloud
10. Enter the **cos_hmac_keys** for the Access Key ID and Secret Key.
11. Click **Add Keystore**.

