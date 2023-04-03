---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-23"

keywords: users, admin, priveleges, profiles, {{site.data.keyword.security_broker_short}} Manager, SMTP

subcollection: security-broker
---

# What if the Persistent Volume Claim (PVC) goes into pending state after installing {{site.data.keyword.security_broker_short}} Manager?
{: #sb_pvc_pending}

After you install {{site.data.keyword.security_broker_short}} Manager, sometimes the PVC goes into pending state as shown below:

NAME       STATUS  VOLUME  CAPACITY  ACCESS MODES  STORAGECLASS    AGE
dsb-manager-pvc  Pending                   ibmc-block-bronze  3m30s
dsb-mongodb-pvc  Pending                   ibmc-block-bronze  3m29s

- Create a YAML file and deploy the YAML file in the Kubernetes cluster, where you have installed the {{site.data.keyword.security_broker_short}} Manager. 

Example:

A sample YAML for PVC of {{site.data.keyword.security_broker_short}} Manager:

```sh
apiVersion: v1
kind: PersistentVolume
metadata:
 name: pvc-dsb-manager
spec:
 accessModes:
 - ReadWriteOnce
 capacity:
  storage: 20Gi
 flexVolume:
  driver: ibm/ibmc-block
  fsType: ext4
 persistentVolumeReclaimPolicy: Delete
 storageClassName: ibmc-block-bronze
 volumeMode: Filesystem
```
{: codeblock}

A sample YAML for PVC of {{site.data.keyword.security_broker_short}} MangoDB:

```sh
apiVersion: v1
kind: PersistentVolume
metadata:
 name: pvc-dsb-mongo
spec:
 accessModes:
 - ReadWriteOnce
 capacity:
  storage: 20Gi
 flexVolume:
  driver: ibm/ibmc-block
  fsType: ext4
 persistentVolumeReclaimPolicy: Delete
 storageClassName: ibmc-block-bronze
 volumeMode: Filesystem
```
{: codeblock}




