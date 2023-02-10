---
copyright:
  years: 2022, 2022
lastupdated: "2023-02-08"

keywords: database, admin, priveleges, users, configure, operations, keyprotect

subcollection: security-broker
---

# Rotate Keys for IBM Cloud Hyper Protect Crypto Services (HPCS) in {{site.data.keyword.security_broker_short}} Manager:
{: #sb_hpcs_keyrotate}

In this section, you can find details on how to rotate the Master and Data Encryption Keys for HPCS Keystore in {{site.data.keyword.security_broker_short}} Manager.

1.  Login to {{site.data.keyword.security_broker_short}} Manager.

2.  Select **Keystores** from the left navigation and click on one of the IBM Cloud Hyper Protect Crypto Services Keystore.

3.  Remember to decrypt the data which has been encrypted using the keystore, before you perform the key rotation operation. Also, perform data backup of your data in the databases before the key rotation operation.

4.  In the right navigation, select the Master Key and click on the three dots. Click **Rotate Key**

5.  Perform the same operation for the Data Encryption Key (DEK) for the same keystore.

6.  Once the Key rotation operation is successfull, you will get a message saying **Master Key was successfully rotated** for the Master Key. For the Data Encryption Key, you will get a message saying **KeyID (ID value) was successfully rotated to KeyID (ID value)**, if the key rotation is successfull.



