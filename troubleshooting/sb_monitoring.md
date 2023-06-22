---
copyright:
  years: 2022, 2023
lastupdated: "2023-06-22"

keywords: DSB monitoring

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.security_broker_short}} Monitoring
{: #sb_monitoring}

You can monitor {{site.data.keyword.security_broker_short}} with IBM Cloud® Monitoring dashboard. For more information about IBM Cloud Monitoring, see the IBM Cloud Monitoring [Getting started tutorial](https://cloud.ibm.com/docs/monitoring?topic=monitoring-getting-started).

You can setup the following monitoring for {{site.data.keyword.security_broker_short}}:

- Configuring the alert tool for the IKS/ROKS cluster deployment.
- Configuring alert rules when there is no pod availability for deployment.
- Adding customized alerts from the Alerts Library.

## Configuring the alert tool for IKS/ROKS cluster deployment:
{: #sb_monitor_iks_roks}

You can configure the alert tool through which the alerts will be sent, for any issues in the clusters.

1. Login to the IBM Cloud account.
2. Select **Kubernetes** -> **Clusters** from the left navigation menu to open the [Kubernetes Clusters Dashboard](https://cloud.ibm.com/kubernetes/clusters), to view the the list of clusters.
2. Select the cluster where you have installed {{site.data.keyword.security_broker_short}}.
3. Click **Launch** under **Monitoring** in the **Integrations** section to open the IBM Cloud Monitor Dashboard.
4. Select Integrations -> **Notification Channels** in the left navigation menu.
5. Click **Add Notification Channel** and select the alert tool from the list of tools available, which will be used to send the alerts for any issues in the cluster.

## Configure Alerts for pod unavailability during deployment:
{: #sb_monitor_pods}

You can configure alerts when the pods are not available in a cluster for the {{site.data.keyword.security_broker_short}} by following the steps below:

1. Navigate to the **IBM Cloud Monitor** dashboard.
2. In the left navigation menu, select **Alerts** and click **New Alert** to configure an alert.
3. Select **PromQL** as the **Alert type** and enter the condition mentioned below in the **Condition** text box and click **Run Query**.

   ```sh
   kube_deployment_status_replicas_available{namespace="<your_dsb_manager_namespace>", deployment="dsb-manager"} < 1
   ```
   {: codeblock}

   **Note**: The above condition is used to configure an alert when there is no pod available for the {{site.data.keyword.security_broker_short}} Manager pod deployment. You can specify the different condition for different types of pods for the {{site.data.keyword.security_broker_short}} deployment and configure alerts for the corresponding pods.
   {: note}

   Use the following conditions to configure alerts for different pod deployment:

   **dsb-mangodb alert condition**:
   ```sh
   kube_deployment_status_replicas_available{namespace="<your_dsb_manager_namespace>", deployment="dsb-mongodb"} < 1
   ```
   {: codeblock}

   **dsb-nginx alert condition**:
   ```sh
   kube_deployment_status_replicas_available{namespace="<your_dsb_manager_namespace>", deployment="dsb-nginx"} < 1
   ```
   {: codeblock}

   **dsb-web alert condition**:
   ```sh
   kube_deployment_status_replicas_available{namespace="<your_dsb_manager_namespace>", deployment="dsb-web"} < 1
   ```
   {: codeblock}

   **dsb-shield alert condition**:
   ```sh
   kube_deployment_status_replicas_available{namespace="<your_dsb_manager_namespace>", deployment="dsb-shield-app1"} < 1dsb-nginx: 
   ```
   {: codeblock}

4. Under **Notifications**, select an alert tool, which is already configured, in the **Notification Channel** drop-down list.
5. Specify the alert name, alert severity, and description for the alert under **Settings** for the alert.
6. Click Save to configure the Prometheus Alert.

## Adding customized alerts from the Alerts Library
{: #sb_monitor_alert_library}

In this section, you can find information on how to add pre-defined alerts, which are available in the Alerts Library. One such example is to configure an alert when the Container Status remains in the Waiting status for a long time.

## Configure Alerts to check the Container status:
{: #sb_monitor_alert_container_status}

