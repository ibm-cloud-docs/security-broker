---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-01"

keywords: uninstall, delete, helm, configuration, tls certificate, docker config secret, environment variable, regions, cluster, container, app security, memory encryption, data in use

subcollection: security-broker
---

{:codeblock: .codeblock}
{:screen: .screen}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:tip: .tip}
{:preview: .preview}
{:deprecated: .deprecated}
{:beta: .beta}
{:term: .term}
{:shortdesc: .shortdesc}
{:script: data-hd-video='script'}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:help: data-hd-content-type='help'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:java: .ph data-hd-programlang='java'}
{:javascript: .ph data-hd-programlang='javascript'}
{:swift: .ph data-hd-programlang='swift'}
{:curl: .ph data-hd-programlang='curl'}
{:video: .video}
{:step: data-tutorial-type='step'}
{:tutorial: data-hd-content-type='tutorial'}
{:release-note: data-hd-content-type='release-note'}


# Uninstalling {{site.data.keyword.security_broker_short}} through Manifests
{: #sb_uninstall}

If you no longer need to use IBM Cloud® Security Broker, you can delete
the namespace to delete all the services, and the objects associated
with the namespace.
{: shortdesc}

## Uninstalling {{site.data.keyword.security_broker_short}} in IKS:
{: #unistall-sb-IKS}

Log into OpenShift Container Platform and follow the steps below to uninstall the {{site.data.keyword.security_broker_short}}:

1.  Get the list of namespaces available in the cluster by executing the following command:

```sh
oc get namespace
```
{: codeblock}

2.  Identify the namespace, where you have the {{site.data.keyword.security_broker_short}} installed.

3.  Delete the namespace, where the {{site.data.keyword.security_broker_short}} is present by executing the following command:

```sh
oc delete -f namespace \<name of the namespace where Data Security
Broker is installed\>
```
{: codeblock}

4.  Verify if the namespace is deleted by listing all the namespaces available in the cluster by executing the following command:

```sh
oc get namespace
```
{: codeblock}

## Uninstalling {{site.data.keyword.security_broker_short}} in ROKS:
{: #uninstall-sb-ROKS}

Log into **kubectl** and complete the and follow the steps below to uninstall the {{site.data.keyword.security_broker_short}}:

1.  Get the list of namespaces available in the cluster by executing the following command:

```sh
kubectl get namespace
```
{: codeblock}

2.  Identify the namespace, where you have the {{site.data.keyword.security_broker_short}} installed.

3.  Delete the namespace, where the {{site.data.keyword.security_broker_short}} is present by executing the following command:

```sh
kubectl delete -f namespace \<name of the namespace where Data Security
Broker is installed\>
```
{: codeblock}

4.  Verify if the namespace is deleted by listing all the namespaces available in the cluster by executing the following command:

```sh
kubectl get namespace
```
{: codeblock}

## Uninstalling {{site.data.keyword.security_broker_short}} using HELM:
{: #sb_uninstall_helm}

1. List the HELM charts that is available in your system by executing the following command:

```sh
helm list
```
{: codeblock}

2. Uninstall the {{site.data.keyword.security_broker_short}} service using HELM by providing the name of the HELM chart, which is configured during the installation process:

```sh
helm uninstall <chart name>
```
{: codeblock}

3. Verify if the service is uninstalled by checking if the corresponding HELM chart, which is used to install the {{site.data.keyword.security_broker_short}} is deleted by listing all the HELM charts available in the system by executing the following command:

```sh
helm list
```
{: codeblock}



