---
copyright:
  years: 2023
lastupdated: "2023-08-24"

keywords: database, admin, priveleges, users, configure, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Configure {{site.data.keyword.security_broker_short}} Manager
{: #sb_configure}

Configuring the {{site.data.keyword.security_broker_short}} Manager console is the first step
to log in and implement the data encryption services.

## Prerequisites
{: #sb_configure_prereq}

Before you begin configuring {{site.data.keyword.security_broker_short}} Manager, ensure you meet the
following requirements:

- {{site.data.keyword.security_broker_short}} Manager must have been installed.
- Load Balancer URL is required to access the {{site.data.keyword.security_broker_short}} Manager.

    To obtain the **Load_balancer_url** of the **dsb-nginx** service, perform the following steps. 
 
    - Log into your IBM Cloud account.
    
    - Select **Resource List** from the left navigation menu. Click **Containers** to view the list of clusters.

    - Select the cluster where you have installed the {{site.data.keyword.security_broker_short}} Manager instance.

## {{site.data.keyword.containerlong}}
{: #sb_lb_iks}

- If you have installed the {{site.data.keyword.security_broker_short}} Manager in a public {{site.data.keyword.containerfull_notm}} cluster, follow the below steps:

- Click **Kubernetes Dashboard** from the cluster, where you have installed {{site.data.keyword.security_broker_short}} Manager.
 
- Select the namespace from the drop-down, on which you have installed the {{site.data.keyword.security_broker_short}} Manager.

- Navigate to **Services** to view the list of {{site.data.keyword.security_broker_short}} Manager services running in the namespace.

- Fetch the **LoadBalancer IP** from the **External Endpoints** column for the **dsb-nginx** service.

## {{site.data.keyword.redhat_openshift_full}}
{: #sb_lb_roks}

- If you have installed the {{site.data.keyword.security_broker_short}} Manager in a public {{site.data.keyword.redhat_openshift_notm}} cluster, click **Openshift web console** from the cluster.

- Click **Projects** in the left navigation menu and select the project from the drop-down, on which you have installed the {{site.data.keyword.security_broker_short}} Manager.

- Navigate to **Networking -> Routes** to view the list of {{site.data.keyword.security_broker_short}} Manager services running in the project.

- Fetch the **{{site.data.keyword.security_broker_short}} Manager URL** from the **Locations** column for the **dsb-nginx** service.

If you have installed the {{site.data.keyword.security_broker_short}} in a private VPC cluster, follow the instructions in the [Deployment models for {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_deployment_models) section to fetch the {{site.data.keyword.security_broker_short}} Manager URL.

## To configure {{site.data.keyword.security_broker_short}} Manager, perform the following steps
{: #sb_configure_overview}
 
1. Copy the **load_balancer_url** from the Kubernetes dashboard for the IKS cluster or from the Openshift   web console for the ROKS cluster.
2. Open a browser window and paste the **load_balancer_url** in the following format:

    ```sh
    https://<load balancer url without the port number>
    ```
    {: pre}    

    **Example**:  If the LoadBalancer IP is http://150.238.243.117:443/, specify the IP in the format https://150.238.243.117

    The warning **Your connection is not private** is displayed.

3. Click **Advanced**, and click the **Proceed to link** at the bottom of the page.

4. The **Getting Started** dialog to proceed with the configuration of the {{site.data.keyword.security_broker_short}} Manager appears.
   
5. Configure the basic System Settings by entering the Init Password, Organization name, Domain name, and Proxy access, and click **Continue**.

   - The Init Password field must contain the same password that you specified for the **secrets.initPass** parameter during the {{site.data.keyword.security_broker_short}} Manager installation.
   - The domain name is part of the email, followed after the "@" character. For example, if the email specified is **test@xyz.example.com**, the domain name must be specified as **example.com**. The domain name that you enter must match in step 1 and step 2 or the domain name in step 2 can be a subset of the domain name specified in the step 1.
   - The proxy access name is the name that is responsible for the connectivity from Proxy to {{site.data.keyword.security_broker_short}} Manager (the IP, or DNS, or the Service Name). For example, **dsb-nginx**.
   {: note}
    
6. Create an Admin Account for the initial {{site.data.keyword.security_broker_short}} Manager administrator by specifying the email address in the **Configure Super Admin User** page. This account is   used to configure the subsequent components such as the keystore, data store connections, and {{site.data.keyword.security_broker_short}} Shields. Click **Continue**.

7. Once you complete the configuration process for the {{site.data.keyword.security_broker_short}} Manager, the next step is to log in to the {{site.data.keyword.security_broker_short}} Manager using the steps mentioned in the [Login to {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login) section.
