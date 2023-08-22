---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: support, deployment models, virtual private cluster, private cluster, public cluster

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Deployment models for Data Security Broker
{: #sb_deployment_models}

You can deploy {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield on a private Virtual Private Cloud (VPC) cluster.

## Private VPC ROKS cluster
{: #private_vpc_roks}

If you are planning your deployment on a private {{site.data.keyword.redhat_openshift_full}} cluster, follow the steps below after installing {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield to get the public {{site.data.keyword.security_broker_short}} Manager URL and a private {{site.data.keyword.security_broker_short}} Shield URL.

## {{site.data.keyword.security_broker_short}} Manager on a private {{site.data.keyword.redhat_openshift_notm}} cluster
{: #private_vpc_roks_dsb_manager}

1. If you do not have access to the {{site.data.keyword.redhat_openshift_notm}} console to access the cluster, you can follow the two steps mentioned below to fetch the {{site.data.keyword.security_broker_short}} Manager URL:

   a. Using the Virtual Machine (VM) user interface deployed within the VPC.
      
      - Login to the {{site.data.keyword.redhat_openshift_notm}} cluster using ibmcloud shell, and execute the following command:

        ```sh
        oc get routes dsb-manager -n <data_security_broker_manager_deployment_projectname>
        ```
        {: codeblock}

      where **data_security_broker_manager_deployment_projectname** is the project name that you created or selected during the {{site.data.keyword.security_broker_short}} Manager installation.

      - Login to the virtual machine and open the {{site.data.keyword.security_broker_short}} Manager URL, that is obtained from the previous step.

   b. Create a public Load Balancer (LB).
      -  Login to the Red Hat Openshift cluster using ibmcloud shell, and execute the following command:

        ```sh
        oc get routes dsb-manager -n <data_security_broker_manager_deployment_projectname>
        ```
        {: codeblock}
      
      where **data_security_broker_manager_deployment_projectname** is the project name that you created or selected during the {{site.data.keyword.security_broker_short}} Manager installation.

      - Create a YAML file with the below format for the load balancer resource.

        ```sh
        apiVersion: v1
        kind: Service
        metadata:
        labels:
          app: dsb-nginx
          name: dsb-nginx-public
        spec:
          ports:
            - port: 443
            protocol: TCP
            targetPort: 8443
        selector:
            app: dsb-nginx
        type: LoadBalancer
        ```
        {: codeblock}       

      - Execute the command to apply the YAML file:
   
        ```sh
        oc apply -f <YAML> -n <data_security_broker_manager_deployment_projectname>
        ```
        {: codeblock}

      - Wait for the load balancer to get into **Active** state. This process might take from five to ten minutes.

      - Fetch the load balancer URL by executing the command:

        ```sh
        oc get svc dsb-nginx-public -n <data_security_broker_manager_deployment_projectname>
        ```
        {: codeblock}

## {{site.data.keyword.security_broker_short}} Shield on a private {{site.data.keyword.redhat_openshift_notm}} cluster
{: #private_vpc_roks_dsb_shield}

1. After you install {{site.data.keyword.security_broker_short}} Shield in a private {{site.data.keyword.redhat_openshift_notm}} cluster, by default, a public Load Balancer IP is provisioned.

2. If you require a private Load Balancer, you can use create a YAML file for the load balancer with the format mentioned below.

   ```sh
   apiVersion: v1
    kind: Service
    metadata:
      annotations:
      service.kubernetes.io/ibm-load-balancer-cloud-provider-ip-type: "private"
    labels:
      app: <dsb-deployment-name>
      name: dsb-shield-private
    spec:
      ports:
        - port: 8444
          protocol: TCP
          targetPort: 8444
    selector:
      app: <dsb-deployment-name>
    type: LoadBalancer
   ```
   {: codeblock}

   where **dsb-deployment-name** is the name of the {{site.data.keyword.security_broker_short}} Shield deployment in your project. To get your **dsb-deployment-name**, execute the following command from your project, where you have installed {{site.data.keyword.security_broker_short}} Shield.

   ```sh
   helm list -n <project_name> | grep shield
   ```
   {: codeblock} 

3. Execute the command to apply the YAML file:
   
   ```sh
   oc apply -f <YAML> -n <data_security_broker_manager_deployment_projectname>
   ```
   {: codeblock} 
   
4. Wait for the load balancer to get into **Active** state. This process might usually take from five to ten minutes.

5. Fetch the load balancer URL by executing the command:

   ```sh
   oc get svc dsb-nginx-public -n <data_security_broker_manager_deployment_projectname>
   ```
   {: codeblock}          

## Private VPC IKS cluster
{: #private_vpc_iks}

## {{site.data.keyword.security_broker_short}} Manager on a private {{site.data.keyword.containerfull}} cluster
{: #private_vpc_iks_dsb_manager}

1. After you install {{site.data.keyword.security_broker_short}} Manager in a private {{site.data.keyword.containerfull_notm}} cluster, by default, a public Load Balancer IP is provisioned.

2. If you require a private Load Balancer, you can use create a YAML file for the load balancer with the format mentioned below.

   ```sh
   apiVersion: v1
    kind: Service
      metadata:
    annotations:
      service.kubernetes.io/ibm-load-balancer-cloud-provider-ip-type: "private"
    labels:
      app: dsb-nginx
      name: dsb-nginx-private
    spec:
      ports:
      - port: 443
      protocol: TCP
      targetPort: 8443
    selector:
      app: dsb-nginx
      type: LoadBalancer
   ```
   {: codeblock} 

3. Execute the command to apply the YAML file:
   
   ```sh
   kubectl apply -f <YAML> -n <data_security_broker_manager_deployment_name_of_the_namespace>
   ```
   {: codeblock} 

   where **data_security_broker_manager_deployment_name_of_the_namespace** is the namespace name that you created or selected during the {{site.data.keyword.security_broker_short}} Manager installation.
 
4. Wait for the load balancer to get into **Active** state. This process might usually take from five to ten minutes.

5. Fetch the load balancer URL by executing the command:

   ```sh
   kubectl get svc dsb-nginx-private -n <data_security_broker_manager_deployment_nameo_of_the_namespace>
   ```
   {: codeblock}
   

## {{site.data.keyword.security_broker_short}} Shield on a private {{site.data.keyword.containerfull_notm}} cluster
{: #private_vpc_iks_dsb_shield}

1. After you install {{site.data.keyword.security_broker_short}} Shield in a private {{site.data.keyword.containerfull_notm}} cluster, by default, a public Load Balancer IP is provisioned.

2. If you require a private Load Balancer, you can use create a YAML file for the load balancer with the format mentioned below.

   ```sh
   apiVersion: v1
    kind: Service
      metadata:
    annotations:
      service.kubernetes.io/ibm-load-balancer-cloud-provider-ip-type: "private"
    labels:
      app: <dsb-deployment-name>
      name: dsb-shield-private
    spec:
      ports:
      - port: 8444
      protocol: TCP
      targetPort: 8444
    selector:
      app: <dsb-deployment-name>
      type: LoadBalancer
   ```
   {: codeblock} 

   where **dsb-deployment-name** is the name of the {{site.data.keyword.security_broker_short}} Shield deployment in your namespace. To get your **dsb-deployment-name**, execute the following command from your namespace, where you have installed {{site.data.keyword.security_broker_short}} Shield.

   ```sh
   helm list -n <namespace_name> | grep shield
   ```
   {: codeblock} 

3. Execute the command to apply the YAML file:
   
   ```sh
   kubectl apply -f <YAML> -n <data_security_broker_shield_deployment_name_of_the_namespace>
   ```
   {: codeblock} 
   
   where **data_security_broker_shield_deployment_name_of_the_namespace** is the namespace name that you created or selected during the {{site.data.keyword.security_broker_short}} Shield installation.
 
4. Wait for the load balancer to get into **Active** state. This process might usually take from five to ten minutes.

5. Copy the load balancer by executing the command:

   ```sh
   kubectl get svc dsb-nginx-private -n <data_security_broker_shield_deployment_nameo_of_the_namespace>
   ```
   {: codeblock}

## {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield in different or multiple private VPC clusters
{: #different_multiple_private_vpc}

If you are planning to install {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield in different or multiple private VPC clusters, you have two options:

1. Using VPC VPN connectivity:
   Refer to [Setting up VPC VPN connectivity](https://cloud.ibm.com/docs/containers?topic=containers-vpc-vpnaas) for more details on how to setup the VPC VPN connectivity.

2. Using Tansit Gateway:
   Refer to [IBM Cloud Transit Gateway](https://cloud.ibm.com/docs/transit-gateway?topic=transit-gateway-about) for more details on how to use the transit gateway method.
   
