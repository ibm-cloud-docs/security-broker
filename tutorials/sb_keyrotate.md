---
copyright:
  years: 2022, 2023
lastupdated: "2023-05-26"

keywords: database, admin, priveleges, users, configure, keyrotate, keyprotect, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Rotate Keys for IBM Key Protect or IBM Cloud Hyper Protect Crypto Services (HPCS) in {{site.data.keyword.security_broker_short}} Manager
{: #sb_ibm_keyrotate}

In this section, you can find details on how to rotate the Master and Data Encryption Keys for IBM Key Protect or HPCS Keystore in {{site.data.keyword.security_broker_short}} Manager.

1.  Login to {{site.data.keyword.security_broker_short}} Manager.

2.  Select **Keystores** from the left navigation and click on one of the Keystore.

3.  In the right navigation, select the Master Key and click on the three dots. Click **Rotate Key**

4.  Perform the same operation for the Data Encryption Key (DEK) for the same keystore.

5.  Once the Key rotation operation is successfull, you will get a message saying "Master Key was successfully rotated" for the Master Key. For the Data Encryption Key, you will get a message saying "KeyID (ID value) was successfully rotated to KeyID (ID value), if the key rotation is successfull.

If key rotation is performed on an encrypted column, all other columns that have a referential relationship with the encrypted column must have their keys rotated to the same new key as well.
{: note}






