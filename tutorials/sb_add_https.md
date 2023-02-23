---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-23"

keywords: database, admin, priveleges, users, features, operations, application

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Adding HTTPs certificate:
{: #sb_add_https}

To add or update an HTTPS certificate, follow the steps below:

1. Copy the certificate files (certificate and key) into a specific directory. 
2. Find the pod name of the {{site.data.keyword.security_broker_short}} Manager using the command in the Kubernetes cluster: 

   ```sh
   kubectl get pods
   ```
   {: codeblock}   

3. Login to the pod using the command:

   ```sh
   kubectl exec -it <pod_name> -- sh
   ```
   {: codeblock}      

4. Navigate to the directory, where you have copied the certificate file, for example, /opt/baffle/dsb-manager and check if the SSL directory is present. If the directory is not present, then create a directory with the certificate files.
5. Exit the pod.
6. Copy certificate and key file to the pod using command: 

   ```sh
   kubectl cp <source_file> <pod_name>:/opt/baffle/baffle-manager/ssl
   ```
   {: codeblock}   
   
7. Once the certificate files are copied, select the **Refresh** button in the **HTTPS Certificate**
section in the **Settings** page of {{site.data.keyword.security_broker_short}} Manager.



