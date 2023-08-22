---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Not used ===== Install {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield
{: #sb_install_ui_procedure}

## Overview
{: #sb_install_ui_overview}

You can install the {{site.data.keyword.security_broker_short}} software by using the {{site.data.keyword.cloud}} catalog. Access the {{site.data.keyword.cloud_notm}} catalog to install the {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield.

You can install {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield only in classic clusters.
{: note}

## Pre-requisites
{: #sb_install_ui_prereq}

-   User must be able to access the {{site.data.keyword.cloud_notm}} Kubernetes cluster (IKS) or {{site.data.keyword.redhat_openshift_full}} Kubernetes (ROKS) cluster.

## Procedure
{: #sb_install_ui_procedure}

1. Log into the IBM Cloud Account (https://cloud.ibm.com) with a valid username and password.

2. Click **Catalog** and enter **{{site.data.keyword.security_broker_short}}** in the **Catalog**
    search text box. The {{site.data.keyword.security_broker_short}} components appear in the Catalog.
   
3. To sort the catalog products using the type, click **Software** in the **Type** option, which is present in the left-hand navigation.

4. The {{site.data.keyword.security_broker_short}} software comprises of two components, which is displayed in the Catalog list as **{{site.data.keyword.security_broker_short}} Manager** and **{{site.data.keyword.security_broker_short}} Shield**.

   ![{{site.data.keyword.security_broker_short}} components in IBM Cloud Catalog list](../images/catalog_items.svg){: caption="{{site.data.keyword.security_broker_short}} components in IBM Cloud Catalog list" caption-side="bottom"}

5. You must install the **{{site.data.keyword.security_broker_short}} Manager** first and then get the Shield Sync ID from the application in the **{{site.data.keyword.security_broker_short}} Manager** to install the **{{site.data.keyword.security_broker_short}} Shield**.

## Install **{{site.data.keyword.security_broker_short}} Manager**
{: #sb_install_dsbm}

Complete the following steps to install the **{{site.data.keyword.security_broker_short}} Manager** from the {{site.data.keyword.cloud_notm}} Catalog:

1. Click **{{site.data.keyword.security_broker_short}} Manager** catalog item.

2. The {{site.data.keyword.security_broker_short}} Manager catalog item opens in a seperate window. In the **Select your deployment target** drop down, select **{{site.data.keyword.containerlong}} (IKS)** or **Red Hat Openshift (ROKS)** to install the {{site.data.keyword.security_broker_short}} Manager in the IKS or ROKS cluster.

   ![{{site.data.keyword.security_broker_short}} Manager Catalog Page](../images/dep_target.svg){: caption="{{site.data.keyword.security_broker_short}} Manager Catalog Page" caption-side="bottom"}

3. The delivery method is selected as **HELM chart** by default under the **Select a delivery method** drop down.

4. Select the version of the software to install, in the **Select Version** drop-down.

5. From the list of available clusters, select the cluster on which you wish to perform the installation.

   ![List of clusters](../images/clusters.svg){: caption="List of clusters" caption-side="bottom"}

6. Select an existing namespace to deploy the {{site.data.keyword.security_broker_short}} Manager or click **Add namespace** to add a new namespace. Specify the name for the namespace and click **Add** to create a new namespace within the selected cluster.

7. Configure your workspace by specifying the following details:

a. Specify the **Name** for the workspace. The workspace name must be unique and using the name of the workspace, you can manage, update or uninstall {{site.data.keyword.security_broker_short}} Manager from the IBM Schematicss Workspace (https://cloud.ibm.com/schematics/workspaces).

   ![Configure Workspace](../images/workspace.svg){: caption="Configure Workspace" caption-side="bottom"}

b. Select the **Resource group**, **Location**, and specify the **Tags** required for configuring the workspace.

8.  lick **Install** in the **Summary** pane on the right to complete the installation process.

9. You will be navigated to the {{site.data.keyword.bpshort}} Workspace to track the installation progress. Once the installation is successful, a message **Workspace creation successfull** is displayed as shown below:

   ![Installation of {{site.data.keyword.security_broker_short}} Manager](../images/install_success.svg){: caption="Installation of {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}
   
   If you get an error message saying,  **Workspace creation failed**, refer to the Logs available in the Terraform output.
   {: note}

## Next Steps
{: #install-catalog-next steps}

After installing {{site.data.keyword.security_broker_short}} Manager, follow the steps listed below to configure and setup the {{site.data.keyword.security_broker_short}} Manager:

## Step1: Configure {{site.data.keyword.security_broker_short}} Manager
{: #install-catalog-configure}

You must configure the {{site.data.keyword.security_broker_short}} Manager console before installing the {{site.data.keyword.security_broker_short}} Shield. See [Configure {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_configure) to complete the configuration of the {{site.data.keyword.security_broker_short}} Manager and access the {{site.data.keyword.security_broker_short}} Manager console.

## Step 2: Log in to {{site.data.keyword.security_broker_short}} Manager:
{: #install-catalog-login}

Log in to the {{site.data.keyword.security_broker_short}} Manager using the steps mentioned in the [Logging into {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_login) section. 

## Step 3: Add a Database in {{site.data.keyword.security_broker_short}} Manager:
{: #install-catalog-add_db}

Refer to the [Add a Database in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_db) section to add a database in the {{site.data.keyword.security_broker_short}} Manager.

## Step 4: Add a Keystore in {{site.data.keyword.security_broker_short}} Manager:
{: #install-catalog-keystore}

Refer to the [Add a Keystore in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_add_keystore) section to connect to a keystore in the {{site.data.keyword.security_broker_short}} Manager.

## Step 5: Enroll an application in the {{site.data.keyword.security_broker_short}} Manager
{: #install-catalog-enroll}

Refer to the [Enrolling an Application in {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_enroll_app) section to enroll an application in the {{site.data.keyword.security_broker_short}} Manager.

Once you have the completed setting up the {{site.data.keyword.security_broker_short}} Manager, the next step is to install the {{site.data.keyword.security_broker_short}} Shield. Copy the **Shield Sync ID** from the {{site.data.keyword.security_broker_short}} Manager application that you have added in [Step 5](/docs/security-broker?topic=security-broker-sb_enroll_app) to use during the {{site.data.keyword.security_broker_short}} Shield installation.
{: important}

## Install {{site.data.keyword.security_broker_short}} Shield
{: #sb_install_ui_procedure}

Complete the following steps to insall the {{site.data.keyword.security_broker_short}} Shield from the IBM Cloud Catalog:

1.  Click **{{site.data.keyword.security_broker_short}} Shield** catalog item.

2.  In the **Select your deployment target** drop down, select **{{site.data.keyword.containerlong_notm}}** or **Red    Hat Openshift** to install the {{site.data.keyword.security_broker_short}} Shield in the IKS or ROKS cluster.

    ![{{site.data.keyword.security_broker_short}} Shield Catalog Page](../images/dsb_shield.svg){: caption="{{site.data.keyword.security_broker_short}} Shield Catalog Page" caption-side="bottom"}

3.  The delivery method is selected as **HELM chart** by default under the **Select a delivery method** drop down.

4.  Select the version of the software to install, in the **Select Version** drop-down.

5.  From the list of available clusters, select the cluster on which you wish to perform the installation.

    ![List of available clusters](../images/clusters.svg){: caption="List of clusters" caption-side="bottom"}

6.  Select an existing namespace to deploy the {{site.data.keyword.security_broker_short}} Shield or click **Add namespace** to add a new namespace. Specify the name for the namespace and click **Add** to create a new namespace within the selected cluster.

7.  Configure your workspace by specifying the following details:

    a.  Specify the **Name** for the workspace. The workspace name must be unique and using the name of the workspace, you can manage, update or uninstall {{site.data.keyword.security_broker_short}} Shield from the IBM Schematicss Workspace (https://cloud.ibm.com/schematics/workspaces).

    ![Configure Workspace](../images/workspace.svg){: caption="Configure Workspace" caption-side="bottom"}

    **Note**: If you are installing more than one instance of {{site.data.keyword.security_broker_short}} Manager in the same namespace, ensure that you provide unique workspace names to each of the {{site.data.keyword.security_broker_short}} Manager installation. Otherwise, you might get error which describes that the same workspace already exists in the namespace.
    
    b.  Select the **Resource group**, **Location**, and specify the **Tags** required for configuring the workspace. 

8. Copy the Shield Sync ID from the {{site.data.keyword.security_broker_short}} Manager application.

    ![Shield Sync ID from Application](../images/shield_syncid.svg){: caption="Shield Sync ID from Application" caption-side="bottom"}

9. Provide the Shield Sync ID and Shield name under **Set the Input Variables** section. 

**Note**: Shield Name is mandatory if you are installing multiple Shields.

    ![Shield Sync ID](../images/shield_name.svg){: caption="Shield Sync ID" caption-side="bottom"}

10. Click **Install** in the **Summary** pane on the right to complete the installation process.

11. You will be navigated to the IBM Schematicss Workspaces to track the installation progress. Once the installation is successful, a message **Workspace creation successfull** is displayed as shown below:

    ![Installation of {{site.data.keyword.security_broker_short}} Shield](../images/install_success.svg){: caption="Installation of {{site.data.keyword.security_broker_short}} Shield" caption-side="bottom"}

**Note**: If you get an error message like **Workspace creation failed**, refer to the Logs available in the Terraform output.

**Next steps**:

Once you have successfully installed {{site.data.keyword.security_broker_short}} Shield, you can explore the data encryption services in the {{site.data.keyword.security_broker_short}} Manager.

Refer to the [Data Encryption Services](/docs/security-broker?topic=security-broker-sb_encrypt_postgress) section to perform the data encryption services offered by {{site.data.keyword.security_broker_short}} Manager.





