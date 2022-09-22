---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-22"

keywords: upgrade, delete, helm, configuration, tls certificate, docker config secret, environment variable, regions, cluster, container, app security, memory encryption, data in use

subcollection: security-broker
---

# Upgrading {{site.data.keyword.security_broker_short}} using Manifests
{: #sb_update}

After IBM Cloud® {{site.data.keyword.security_broker_short}} is installed on your cluster, you
can update it at any time.
{: shortdesc}

## Upgrading {{site.data.keyword.security_broker_short}} in ROKS
{: #upgrade-sb-ROKS}

Log into OpenShift Container Platform and complete the steps mentioned
below to upgrade {{site.data.keyword.security_broker_short}} on ROKS:

1.  Navigate to the path where you have installed the Data Security
    Broker.

2.  Download the latest images of {{site.data.keyword.security_broker_short}} in the relevant path.

3.  Perform the upgrade by executing the following deployment commands
    to deploy the latest images of {{site.data.keyword.security_broker_short}}:

    ```sh
    1. oc set image deployment/security-broker-manager security-broker
    -manager=\<image_location\>
    ```
   {: codeblock}

    ```sh
    2. oc set image deployment/ security-broker -mongodb security-broker
    -mongodb=\<image_location\>
    ```
    {: codeblock}

    ```sh
    3. oc set image deployment/ security-broker -web security-broker
    -web=\<image_location\>
    ```
    {: codeblock}

    ```sh
    4. oc set image deployment/ security-broker -nginx security-broker
    -nginx=\<image_location\>
    ```
    {: codeblock}

    ```sh
    5. oc get cm security-broker -shield-\<app_name\>-config -o yaml \| sed
    -e \'s\|\<current_version\>\|\<new_version\>\|\' \| oc apply -f -
    ```
    {: codeblock}

    ```sh
    6. oc set image deployment/ security-broker-shield-\<app_name\>
    security-broker-shield-\<app_name\>=\<image_location\>
    ```
    {: codeblock}

4.  Verify that the pods are re-launched and are in **Running** state. To
    view the status of the pods in the namespace, execute the following
    command:

    ```sh
    oc get pods -n \<namespace\>
    ```
    {: codeblock}
    
5.  Identify the external IP address of the Load Balancer with the following command:

    ```sh
    kubectl get svc security-broker-nginx
    ```
    The output of this command is displayed as shown in the example below:

    NAME           TYPE                   CLUSTER-IP       EXTERNAL-IP       PORT(S)             AGE
    Security-broker-nginx   LoadBalancer   1.1.1.1       10.10.10.10        43:31689/TCP           18h

6.  Open a Web browser window and enter the **Load Balancer External
    IP** preceded by **https://** to access the {{site.data.keyword.security_broker_short}} Manager.
    In the above example, the web browser address to access the Security Broker Manager would be https://10.10.10.10.

7.  To confirm the upgrade, login to the Security Broker Manager and
    click Help to view the version number of the {{site.data.keyword.security_broker_short}},
    which has been upgraded.

**Note**: If you are upgrading the Security Broker Shield, you need to
complete the following steps to ensure that the Security Broker Shield
which is in idle state is deleted.

a.  Login to the Security Broker Manager and Select the **Applications**
    icon in the left navigation panel and click **Application**
    **settings**.

b.  Select the Security Broker Shield which is in stopped state and
    click the Delete (**--)** button to delete the Security Broker
    Shield.

## Upgrading {{site.data.keyword.security_broker_short}} in IKS
{: #upgrade-sb-IKS}

Log into **kubectl** and complete the steps mentioned below to upgrade
{{site.data.keyword.security_broker_short}} on IKS:

1.  Navigate to the path where you have installed the Data Security
    Broker.

2.  Download the latest images of {{site.data.keyword.security_broker_short}} for the latest
    version, which you need to upgrade.

3.  Perform the upgrade by executing the following deployment commands
    to deploy the latest images of {{site.data.keyword.security_broker_short}}:

    ```sh
    kubectl set image deployment/security-broker-manager security-broker
    -manager=\<image_location\>
    ```
    {: codeblock}

    ```sh
    kubectl set image deployment/ security-broker -mongodb
    security-broker -mongodb=\<image_location\>
    ```
    {: codeblock}

    ```sh
    kubectl set image deployment/ security-broker -web security-broker
    -web=\<image_location\>
    ```
    {: codeblock}

    ```sh
    kubectl set image deployment/ security-broker -nginx security-broker
    -nginx=\<image_location\>
    ```
    {: codeblock}

    ```sh
    kubectl get cm security-broker -shield-\<app_name\>-config -o yaml
    \| sed -e \'s\|\<current_version\>\|\<new_version\>\|\' \| oc apply -f
    ```
    {: codeblock}

    ```sh
    kubectl set image deployment/ security-broker-shield-\<app_name\>
    security-broker-shield-\<app_name\>=\<image_location\>
    ```
    {: codeblock}

4.  Verify that the pods are launched and are in **Running** state. To
    view the status of the pods in the namespace, execute the following
    command:

    ```sh
    kubectl get pods -n \<namespace\>
    ```
    {: codeblock}

5.  Identify the external IP address of the Load Balancer with the following command:

    ```sh
    kubectl get svc security-broker-nginx
    ```
    The output of this command is displayed as shown in the example below:

    NAME           TYPE                   CLUSTER-IP       EXTERNAL-IP       PORT(S)             AGE
    Security-broker-nginx   LoadBalancer   1.1.1.1       10.10.10.10        43:31689/TCP           18h

6.  Open a Web browser window and enter the **Load Balancer External
    IP** preceded by **https://** to access the {{site.data.keyword.security_broker_short}} Manager.
    In the above example, the web browser address to access the Security Broker Manager would be https://10.10.10.10.

7.  Open a Web browser window and enter the **Load Balancer External
    IP** preceded by **https://** to access the Security Broker Manager.

**Note**: If you are upgrading the Security Broker Shield, you need to
complete the following steps to ensure that the Security Broker Shield
which is in idle state is deleted.

a.  Login to the Security Broker Manager and Select the **Applications**
    icon in the left navigation panel and click **Application**
    **settings**.

b.  Select the Security Broker Shield which is in stopped state and
    click the Delete (**--)** button to delete the Security Broker
    Shield.

