---
copyright:
  years: 2022, 2023
lastupdated: "2023-01-03"

keywords: database, admin, priveleges, users, configure, operations

subcollection: security-broker
---

# Configure Data Security Broker Manager
{: #sb_configure}

Configuring the {{site.data.keyword.security_broker_short}} Manager console is the first step
in implementing the data protection services.

## **Prerequisites:**
{: #sb_configure_prereq}

Before you begin configuring {{site.data.keyword.security_broker_short}} Manager, ensure you meet the
following requirements:

    1. {{site.data.keyword.security_broker_short}} Manager must have been installed.
    2. Load Balancer URL is required to access the {{site.data.keyword.security_broker_short}} Manager.



## To configure {{site.data.keyword.security_broker_short}} Manager, perform the following steps:
{: #sb_configure_overview}

1. To obtain the **Load_balancer_url** of the **dsb-nginx** service, perform the following steps:

    a.  Log into your IBM Cloud account.
    
    b.  Select **Resource List** from the left navigation menu. Click **Containers** to view the list of clusters.

    c.  Select the cluster where you have installed the {{site.data.keyword.security_broker_short}} Manager instance.

    d.  Click Kubernetes Dashboard to navigate to the Kubernetes Dashboard.

    e.  Select the namespace from the drop-down, on which you have installed the {{site.data.keyword.security_broker_short}} Manager.

    f.  Navigate to **Services** to view the list of {{site.data.keyword.security_broker_short}} Manager services running in the namespace.

    g.  Fetch the **LoadBalancer IP** from the **External Endpoints** column for the **dsb-nginx** service.
    
    

2. Copy the **load_balancer_url** from the Kubernetes dashboard.
3. Open a browser window and paste the **load_balancer_url** in the following format:

    ```sh
    https://<load balancer url without the port number>
    ```
    {: codeblock}    

    **Example**:  If the LoadBalancer IP is http://150.238.243.117:443/, specify the IP in the format https://150.238.243.117

    The warning **Your connection is not private** is disaplayed.

    ![Warning: Connection not private](../images/warning.svg){: caption="Warning: Connection not private" caption-side="bottom"}

4. Click **Advanced**, and click the **Proceed to link** at the bottom of the page.

5. The **Getting Started** dialog to proceed with the configuration of the {{site.data.keyword.security_broker_short}} Manager appears as shown below:

    ![Getting Started](../images/getting_started.svg){: caption="Getting Started" caption-side="bottom"}

6. Configure the basic System Settings by entering the hostname, domain name, proxy access, and click **Continue**.

    **Note**: The domain is part of the email, followed after the "@" character, that is specified during the configuration. For example, if the email specified is test@ibm.com, then the domain name must be ibm.com.

7. Create an Admin Account for the initial {{site.data.keyword.security_broker_short}} Manager administrator by specifying the email address in the **Configure Super Admin User** page. This account is   used to configure the subsequent components such as the keystore, data store connections, and {{site.data.keyword.security_broker_short}} Shields. Click **Continue**.

    ![Configure Super Admin User](../images/superadmin.svg){: caption="Configure Super Admin User" caption-side="bottom"}

8. Configure Credential Keystore to establish an encrypted credential store for any system access credential or access key that the {{site.data.keyword.security_broker_short}} Manager or {{site.data.keyword.security_broker_short}} Shield utilize. Enter the **{{site.data.keyword.security_broker_short}}** **Secret Key** in the text field. For the **Password** field, enter a secure password or passphrase to secure the actual keystore. Enter the same string that you specified for the **Password** field in the **Confirm Password** text box. Click **Finish** to complete the {{site.data.keyword.security_broker_short}} Manager configuration.

    ![Configure Credential Keystore](../images/secret_key.svg){: caption="Configure Credential Keystore" caption-side="bottom"}

    **Note**: The {{site.data.keyword.security_broker_short}} Secret Key must contain at least 10 characters, a mixture of upper and lower case, including at least one numeric character. The Secret Key is used to generate a random key to encrypt the Keystore Config Password.

9. Once you complete the configuration process for the {{site.data.keyword.security_broker_short}} Manager, the next step is to login to the {{site.data.keyword.security_broker_short}} Manager using the steps mentioned in the [Logging into {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login) section.
