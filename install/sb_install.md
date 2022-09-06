---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-06"

keywords: install, ROKS, IKS, manifests, HELM

subcollection: security-broker
---

# Installing Data Security Broker
{: #sb_install}

You can install Data Security Broker in one of the following ways:

1.  Using the manifests to install

2.  Using the HELM chart

3.  Using the Data Security Broker User Interface

## Installing Data Security Broker through the Manifests:
{: #install-sb-manifests}

You can install Data Security Broker on an IBM Cloud Kubernetes cluster or an
IBM Red Hat OpenShift Kubernetes cluster through the manifests.

## Pre-requisites:
{: #install-sb-pre-requisites}

Ensure that you have met the following conditions, before you begin the
installation:

-   Create an IBM Cloud account.

-   Install IBM Cloud Command Line Interface (CLI). For more
    information, see [How to install IBM Cloud
    CLI](https://ibm.github.io/cloud-enterprise-examples/iac/setup-environment/#install-ibm-cloud-cli).

-   Login to IBM Cloud using the CLI. For more information, see [How to
    log into IBM Cloud using the
    CLI](https://ibm.github.io/cloud-enterprise-examples/iac/setup-environment/#login-to-ibm-cloud).

-   Install OpenShift Container Platform. For more information, see [How
    to install OpenShift Container
    Platform](https://docs.openshift.com/container-platform/4.3/cli_reference/openshift_cli/getting-started-cli.html).

-   Install **kubectl**. For more information, see [How to install
    kubectl](https://kubernetes.io/docs/tasks/tools/).

-   A valid JFrog access TOKEN is required to install the Security
    Broker Manager.

-   Ensure that you have the Data Security Broker Manager images, and the
    docker images has been loaded to the container registry before
    starting the installation procedure for the Security Broker Manager.

## Install Data Security Broker on an IBM Red Hat OpenShift Kubernetes cluster:
{: #install-sb-ROKS}

[Red Hat®
OpenShift®](https://www.redhat.com/en/technologies/cloud-computing/openshift) on [IBM
Cloud](https://www.ibm.com/cloud) is a fully managed OpenShift service,
an enterprise-level [Kubernetes](https://kubernetes.io/) container
platform that enables a cloud-like experience wherever it is
deployed. For more information on Red Hat OpenShift Container platform,
see [Introduction on Red Hat OpenShift Container
platform](https://www.redhat.com/en/technologies/cloud-computing/openshift/container-platform).

## Installing Data Security Broker Shield in ROKS:
{: #install-sb-ROKS}

Log into OpenShift Container Platform and complete the steps mentioned
below to install Data Security Broker Shield on ROKS:

1.  Deploy the Data Security Broker Shield by executing the following
    command:


    ```sh
    oc create security-broker-shield-svc.yaml -n \<namespace\>
    oc create -f security-broker-shield.yaml -n \<namespace\>
    ```
    {: codeblock}

2.  Verify that the pods are launched and are in **Running** state. To
    view the status of the pods in the namespace, execute the following
    command:

    ```sh
    oc get pods -n \<namespace\>
    ```
    {: codeblock}

For example, if you specify **oc get pods -n default**, the following
output is displayed which shows the status of the pods in the default
namespace:

```sh
NAME                                    READY STATUS RESTARTS AGE

security-broker-mongodb-67768846f8-pgt24 1/1 Running 0 28d
security-broker-nginx-746dc4688c-2xrms 1/1 Running 0 28d
security-broker-shield-app1-8dbc7b859-xhlnf 1/1 Running 0 9d
security-broker-web-775dc97fdb-j5mmr 1/1 Running 0 28d
```
{: codeblock}

3.  To view and confirm the details of each pod in the namespace,
    execute the following command:

    ```sh
    oc describe pod \<pod name\>
    ```
    {: codeblock}

### Installing Data Security Broker Manager in ROKS:
{: #install-sb-manager-ROKS}

Log into OpenShift Container Platform and complete the steps mentioned
below to install Data Security Broker Manager on ROKS:

1.  Create Persistent Volume Claims (PVCs). The requirements for the
    Persistent storage volume claims are provided in the
    **security-broker-pvc.yaml** file. Create the PVC by executing the
    following command:

    ```sh
    oc create -f security-broker-pvc.yaml -n \<namespace\>
    ```
    {: codeblock}

To verify if the PVC is created successfully, execute the following
command:

    ```sh
    oc get pvc -n \<namespace\>
    ```
    {: codeblock}

2.  Deploy the Data Security Broker Manager services by executing the
    following command:

    ```sh
    oc create -f security-broker-mongodb.yaml -n \<namespace\>
    oc create -f security-broker-manager.yaml -n \<namespace\>
    oc create -f security-broker-web.yaml -n \<namespace\>
    oc create -f security-broker-nginx.yaml -n \<namespace\>
    ```
    {: codeblock}

3.  To view the status of the pods in the namespace, execute the
    following command:

    ```sh
    oc get pods -n \<namespace\>
    ```
    {: codeblock}

For example, if you specify **oc get pods -n default**, the following
output is displayed which shows the status of the pods in the default
namespace:

```sh
NAME                                     READY STATUS RESTARTS AGE

security-broker-mongodb-67768846f8-pgt24 1/1 Running 0 28d
security-broker-nginx-746dc4688c-2xrms 1/1 Running 0 28d
security-broker-shield-app1-8dbc7b859-xhlnf 1/1 Running 0 9d
security-broker-web-775dc97fdb-j5mmr 1/1 Running 0 28d
```
{: codeblock}

4.  To view and confirm the details of each pod in the namespace,
    execute the following command:

    ```sh
    oc describe pod \<pod name\>
    ```
    {: codeblock}


## Install Data Security Broker on an IBM Cloud Kubernetes cluster:
{: #install-sb-iks}

The Kubernetes command-line tool, **kubectl**, allows you to run
commands against Kubernetes clusters. You can use **kubectl** to deploy
applications, inspect and manage cluster resources, and view logs. For
more information, see including a complete list of **kubectl**
operations, see the [Command line kubectl reference
documentation](https://kubernetes.io/docs/reference/kubectl/).

### Installing Data Security Broker Shield in IKS:
{: #install-sb-shield-iks}

Log into **kubectl** and complete the steps mentioned below to install
Security Broker on ROKS:

1.  Deploy the Data Security Broker Shield by executing the following
    command:
    
    ```sh
    kubectl apply security-broker-shield-svc.yaml -n \<namespace\>
    kubectl create -f security-broker-shield.yaml -n \<namespace\>
    ```
    {: codeblock}


2.  Verify that the pods are launched and are in **Running** state. To
    view the status of the pods in the namespace, execute the following
    command:

    ```sh
    kubectl get pods -n \<namespace\>
    ```
    {: codeblock}

For example, if you specify **kubectl get pods -n default**, the
following output is displayed which shows the status of the pods in
the default namespace:

```sh
NAME READY STATUS RESTARTS AGE

Security-broker-shield-app1-8dbc7b859-xhlnf 1/1 Running 0 9d
```
{: codeblock}

3.  To view and confirm the details of each pod in the namespace,
    execute the following command:

    ```sh
    kubectl describe pod \<pod name\>
    ```
    {: codeblock}

### Installing Security Broker Manager in IKS:
{: #install-sb-manager-iks}

Log into **kubectl** and complete the steps mentioned below to install
Data Security Broker Manager on IKS:

1.  Create Persistent Volume Claims (PVCs). The requirements for the
    Persistent storage volume claims are provided in the
    **security-broker-pvc.yaml** file. Create the PVC by executing the
    following command:

    ```sh
    kubectl create -f security-broker-pvc.yaml -n \<namespace\>
    ```
    {: codeblock}

To verify if the PVC is created successfully, execute the following
command:

    ```sh
    kubectl get pvc -n \<namespace\>
    ```
    {: codeblock}

2.  Deploy the Data Security Broker Manager services by executing the following
    command:

    ```sh
    kubectl apply -f security-broker -mongodb.yaml** **-n
    \<namespace\>

    kubectl apply -f security-broker -manager.yaml -n \<namespace\>

    kubectl apply -f security-broker -web.yaml -n \<namespace\>

    kubectl apply -f security-broker -nginx.yaml -n \<namespace\>
    ```
    {: codeblock}

3.  To view the status of the pods in the namespace, execute the
    following command:

    ```sh
    kubectl get pods -n \<namespace\>
    ```
    {: codeblock}

For example, if you specify **kubectl get pods -n default**, the
following output is displayed which shows the status of the pods in
the default namespace:

```sh
NAME                                    READY STATUS RESTARTS AGE

security-broker-mongodb-67768846f8-pgt24 1/1 Running 0 28d
security-broker-nginx-746dc4688c-2xrms 1/1 Running 0 28d
security-broker-manager-app1-8dbc7b859-xhlnf 1/1 Running 0 9d
security-broker-web-775dc97fdb-j5mmr 1/1 Running 0 28d
```
{: codeblock}

4.  To view and confirm the details of each pod in the namespace,
    execute the following command:

    ```sh
    kubectl describe pod \<pod name\>
    ```
    {: codeblock}


### Accessing Security Broker Manager:
{: #access-sb-manager}

To access the Data Security Broker Manager, perform the following operation:

1.  Identify the external IP address of the Load Balancer with the
    following command.

        ```sh
        kubectl get svc security-broker-nginx
        ```
        {: codeblock}

The output of this command is displayed as shown in the example
below:

```sh
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE

Security-broker-nginx LoadBalancer 1.1.1.1 **10.10.10.10** 43:31689/TCP 18h
```
{: codeblock}

2.  Open a Web browser window and enter the **Load Balancer External
    IP** preceded by **https://**.

In the above example, the web browser address to access the Data Security
Broker Manager would be **https://10.10.10.10**.

## Installing Security Broker through HELM charts:
{: #install-sb-helm}



## Installing Security Broker through User Interface:
{: #install-sb-ui}

