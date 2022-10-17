---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installing {{site.data.keyword.security_broker_short}} using the IBM Cloud Catalog
{: #sb_install_catalog}

## Overview:
{: #sb_install_ui_overview}

You can install the {{site.data.keyword.security_broker_short}} software by using the IBM Cloud Catalog. Refer to this link to access the {{site.data.keyword.security_broker_short}} in the IBM Cloud Catalog:
<https://cloud.ibm.com/catalog/content/ibmcloud-security-broker> (Need
to correct the link when the software is available in the Catalog).

To know more about the overview, HELM charts and HELM templates, and the
HELM charts life cycle, see [Getting started with
HELM](https://helm.sh/docs/).

## Pre-requisites:
{: #sb_install_ui_prereq}

-   User must have an active IBM Cloud Account

-   User must be able to access the IBM Cloud Kubernetes cluster (IKS)
    or IBM Red Hat OpenShift Kubernetes cluster (ROKS) cluster

## Procedure:
{: #sb_install_ui_procedure}

1.  Log into the IBM Cloud Account (https://cloud.ibm.com) with a valid username and password.

2.  Click **Catalog**. Enter **{{site.data.keyword.security_broker_short}}** in the **Catalog**
    search text box. A list of products appears in the Catalog.

3.  To sort the products using the type, click **Software** in the **Type** option, which is present in the left-hand navigation of the Catalog.

4.  You will find two catalog items for **{{site.data.keyword.security_broker_short}}**-Manager and **{{site.data.keyword.security_broker_short}}**-Shield as a result of the Catalog search.

5. You must install the **{{site.data.keyword.security_broker_short}}**-Manager first and then get the Shield Sync ID from the **{{site.data.keyword.security_broker_short}}**-Manager to install the **{{site.data.keyword.security_broker_short}}** Shield.

6.  Click **{{site.data.keyword.security_broker_short}}**-Manager catalog item.

7.  Perform the following operations to complete the installation of the
    {{site.data.keyword.security_broker_short}}-Manager using the Catalog:

    a.  In the **Select your deployment target** drop down, select **IBM Cloud Kubernetes service** or **Red Hat Openshift**.

    b.  Select **HELM chart** as the delivery method for installation in the **Select a delivery method** drop down.

    c.  Select the product version.

    d.  From the list of available clusters, select the cluster on which you wish to perform the installation and click **Next**.

    e.  Select a namespace to perform the installation.

    f.  Specify the **Name**, and select the **Resource group**, **Location**, and **Tags** required for configuring the workspace for the installation.

    g.  Set the deployment values and Click **Install** to complete the installation process.

## Configure **{{site.data.keyword.security_broker_short}}** Manager:
{: #install-catalog-configure}

You must configuring the Data Security Broker Manager console before installing the **{{site.data.keyword.security_broker_short}}** Shield. See [Configuring {{site.data.keyword.security_broker_short}} Manager](/docs/security-broker?topic=security-broker-sb_configure)to complete the configuration of the **{{site.data.keyword.security_broker_short}}** Manager and access the **{{site.data.keyword.security_broker_short}}** Manager console.






