---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-04"

keywords: database, admin, priveleges, users, configure, operations, keyprotect

subcollection: security-broker
---

# Configure HPCS
{: #sb_hpcs}

This guide shows you how to add [IBM CloudTM Hyper Protect Crypto Services (HPCS)](https://www.ibm.com/cloud/hyper-protect-crypto) as a keystore in Baffle Manager and configure HPCS. A reference for the necessary parameter settings is provided following the walkthrough procedure.

[IBM CloudTM Hyper Protect Crypto Services](https://www.ibm.com/cloud/hyper-protect-crypto) offers a cloud hardware security module (HSM) and key management service. It aims to give you control over your cloud hardware security models and cloud data encryption keys as it is the only service in the market built on FIPS 140-2 Level 4-certified hardware.

The service, which is based on IBM LinuxONE technology, helps to guarantee that only you have access to your keys. Using a dedicated customer-controlled HSM that provides single-tenant key management and key vaulting makes it simple to create encryption keys. You can also bring your own encryption keys to manage instead. Your applications can incorporate cryptographic operations like digital signing and validation because the managed cloud HSM supports industry standards like PKCS #11.


## Configure IBM Cloud Hyper Protect Crypto Services (HPCS)

Configure IBM Cloud Hyper Protect Crypto Services by following these steps. You can then add IBM Cloud<sup>TM</sup> Hyper Protect Crypto Services as a keystore in Baffle Manager once this process is finished.


#### Follow these steps to configure IBM Cloud Hyper Protect Crypto Services (HPCS):



1. Get an IBM Instance ID in one of the following ways:
    * Using the IBM CLI – enter the following command in a shell window: \
`ibmcloud resource service-instance 'HPCS-Baffle-1'`
    * Using the IBM Cloud web console – navigate to Services and software and select the HPCS instance. The GUID is displayed in the sidebar and is what you use for the `instanceID`.
2. Create and retrieve API Key, in the following way: 
    * Open a  web browser and navigate to:[ https://cloud.ibm.com/iam/apikeys](https://cloud.ibm.com/iam/apikeys).
    * Select Create an IBM Cloud API Key and name the key.
    * Copy or download the key after it’s created.
3. Create Cloud Object Storage in the resource group.
4. Create a Bucket in the COS instance, for example:  `bm-ibm-bucket`
5. Generate Service Credentials for the COS Bucket.
6. In Object Storage, click on Service Credentials in the side panel. Then click New Credential.
7. Enable HMAC and click Add. 

    NOTE: The `cos_hmac_keys` give you the AWS S3 `access_key_id` and `secret_access_key`.

8. Continue with adding IBM Cloud Hyper Protect Crypto Services as a keystore in Baffle Manager.


## Add IBM Cloud Hyper Protect Crypto Services as a keystore in Baffle Manager

Use IBM Cloud Hyper Protect Crypto Services as a keystore in Baffle Manager by completing the subsequent steps.


#### Do the following to add IBM Cloud Hyper Protect Crypto Services as a keystore:



1. In the Baffle Manager console, click the key icon in the left navigation bar. The Keystore window appears. 

    NOTE: If this is the first time you are enrolling a keystore, the `baffle_credential_store` will be the only keystore that appears in the list.

2. Click +Keystore. The Add Keystore dialog appears.
3. Enter a keystore Name and select IBM Cloud Hyper Protect Crypto Services in the Keystore Type drop-down menu.
4. Enter the Instance ID (from step 1 of configuring IBM Cloud Hyper Protect Crypto Services) for the KeyProtect Instance.
5. For App Namespace, enter a string to identify the application.
6. For IBM Cloud Hyper Protect Crypto Services Alias, enter a unique string value.
7. For the IAM API Key, use the key you created in step 2 of configuring IBM Cloud Hyper Protect Crypto Services.
8. For IBM region, specify the region for the IBM Cloud Hyper Protect Crypto Services instance. See [Available IBM region listing](https://docs.baffle.io/v1/docs/configure-ibm-key-protect-and-add-it-as-a-keystore-baffle#available-ibm-region-listing) for more information.
9. For the IBM Cloud Object Storage URL, specify the IBM endpoint URL for COS, for example: https://s3.us-south.cloud-object-storage.appdomain.cloud
10. Enter the `cos_hmac_keys` from step 7 (from configuring IBM Cloud Hyper Protect Crypto Services) for the Access Key ID and Secret Key.
11. When completed, click Add Keystore. \
 \
NOTE: The key will not appear in IBM Cloud Hyper Protect Crypto Services until Baffle Shield has been connected and data encryption migration has occurred. 


## Available IBM region listing


<table>
  <tr>
   <td>Region
   </td>
   <td>Public endpoints
   </td>
  </tr>
  <tr>
   <td>Dallas
   </td>
   <td>us-south
   </td>
  </tr>
  <tr>
   <td>Washington DC
   </td>
   <td>us-east
   </td>
  </tr>
  <tr>
   <td>London
   </td>
   <td>eu-gb
   </td>
  </tr>
  <tr>
   <td>Frankfurt
   </td>
   <td>eu-de
   </td>
  </tr>
  <tr>
   <td>Sydney
   </td>
   <td>au-syd
   </td>
  </tr>
  <tr>
   <td>Tokyo
   </td>
   <td>jp-tok
   </td>
  </tr>
  <tr>
   <td>Osaka
   </td>
   <td>jp-osa
   </td>
  </tr>
</table>


 


### More information

For more information on the following topics, see the related IBM documentation.



* Create IBM Keys Auth – For more information, see the [IBM documentation](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).
* Deploy a Kubernetes cluster – For more information, see the [IBM documentation](https://www.ibm.com/cloud/kubernetes-service/kubernetes-tutorials?p1=Search&p4=43700055610570248&p5=e&gclid=Cj0KCQjwhr2FBhDbARIsACjwLo2cv9JePdgZ5FxTA_c0iw9t_6uJ03KCZoNyiXhnLK3HW02THbC5zAYaApeZEALw_wcB&gclsrc=aw.ds).
* Create an HPCS instance – For more information, see the [IBM documentation](https://cloud.ibm.com/docs/key-protect?topic=key-protect-tutorial-import-keys).
* Create a Cloud Object Store (COS) – For more information, see the [IBM documentation](https://www.ibm.com/cloud/object-storage).
* Create HMAC keys on the COS – For more information, see the [IBM documentation](https://www.ibm.com/cloud/object-storage).


# Next Steps:



* Continue with [Connect to a Data Store](https://support.baffle.io/hc/en-us/articles/1500002595601-Task-3-Connect-to-a-Data-Store).