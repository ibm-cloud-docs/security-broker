---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installing {{site.data.keyword.security_broker_short}} using the HELM chart in CLI
{: #sb_install_helm}

To work with {{site.data.keyword.security_broker_short}}, you can use HELM to install the
software using the CLI.

## Overview:
{: #sb_install_intro}

Helm is a package manager. Package managers automate the process of
installing, configuring, upgrading, and removing computer programs.

To know more about the overview, HELM charts and HELM templates, and the
HELM charts life cycle, see [Getting started with
HELM](https://helm.sh/docs/).

## Pre-requisites:
{: #sb_install_helm-prereq}

-   User must have an active IBM Cloud Account

-   User must be able to access the IBM Cloud Kubernetes cluster (IKS)
    or IBM Red Hat OpenShift Kubernetes cluster (ROKS) cluster

-   User must have installed HELM in their system

-   User must have configured the HELM chart

## Procedure:
{: #sb_install_helm_procedure}

Complete the following steps to install the {{site.data.keyword.security_broker_short}} using
HELM using the CLI:

1.  Install HELM in your local machine. To perform the HELM
    installation, see [Installing
    HELM](https://www.ibm.com/cloud/architecture/content/course/helm-fundamentals/helm-install).

2.  Configure the HELM chart to install {{site.data.keyword.security_broker_short}} and add the
    HELM chart repo to your instance of Helm:

```sh
helm repo add \<chart name\> \<location of the chart\>
```
{: codeblock}

3.  List the HELM charts that are installed in your system by using the
    following command:

```sh
helm list
```
{: codeblock}

4.  To update your repo to the latest version of HELM, use the command:

```sh
helm repo update 
```
{: codeblock}

5.  To create a new HELM chart, execute the following command:

```sh
helm create \<name of the chart\>
```
{: codeblock}

6.  Initialize the Helm CLI and the HELM linter can be used as part of
    HELM chart development and testing.

```sh
helm lint \<chart name\>
```
{: codeblock}

7.  Install the HELM chart by executing the following command:

```sh
helm install \<chart name\> \<helm chart that to be installed\>
```
{: codeblock}

8.  To override the values file using CLI, execute the following
    command:

```sh
helm install -f \<values file\> \<chart name\>
```
{: codeblock}

9.  To override the values file, using the **set** option from CLI,
    execute the following command:

```sh
helm install \--set-string
configmap.data.BM_SHIELD_SYNC_ID=U0hJRUxELTY3LjIyOC4xMjMuMjI3LTE3Mi4zMC4yMzguOS00NDMtaWJtLTYyYjFkY2M5ZjFlZTIwMzk1MDUzMjc2Yy04NDQ0
\<name of the chart\>
```
{: codeblock}

