---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installing {{site.data.keyword.security_broker_short}} using the HELM chart in the User Interface (UI)
{: #sb_install_ui}

## Overview:
{: #sb_install_ui_overview}

You can install the {{site.data.keyword.security_broker_short}} software by using the User
Interface (UI) available in the IBM Cloud Catalog. Refer to this link to
access the {{site.data.keyword.security_broker_short}} UI in the IBM Cloud Catalog:
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

1.  Log into the IBM Cloud Account (<https://cloud.ibm.com/>) with a
    valid username and password.

2.  Search for **{{site.data.keyword.security_broker_full_notm}}** in the **Catalog**
    search box.

3.  You can also perform a detailed search for **{{site.data.keyword.security_broker_full_notm}}**. Click **Catalog**. A list of products       appears in the Catalog.

4.  To sort the products using the type, click **Software** in the
    **Type** option, which is present in the left-hand navigation of the
    Catalog.

5.  Click **Helm Charts** from the list, which is displayed in the right
    pane of the Catalog.

6.  Select the helm chart, which is configured to install the Data
    Security Broker.

7.  Select the version of the HELM

8.  Perform the following operations to complete the deployment of the
    {{site.data.keyword.security_broker_short}} software using the Catalog UI:

    a.  In the **Select your deployment target** drop down, select IBM
        Cloud Kubernetes service.

    b.  Select **HELM chart** as the delivery method for installation in
        the **Select a delivery method** drop down.

    c.  Select the product version and click **Next**.

    d.  From the list of available clusters, select the cluster on which
        you wish to perform the installation and click **Next**.

    e.  Select a namespace for the installation.

    f.  Specify the **Name**, and select the **Resource group**,
        **Location**, and **Tags** required for the installation.

    g.  Click **Install** to complete the installation process.

