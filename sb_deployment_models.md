---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-20"

keywords: support, deployment models, virtual private cluster, private cluster, public cluster

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Deployment models for Data Security Broker
{: #sb_deployment_models}

You can deploy {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield on a private Virtual Private Cloud (VPC) cluster.

## Private VPC ROKS cluster
{: #private_vpc_roks}

If you are planning your deployment on a private ROKS cluster, follow the steps below after installing {{site.data.keyword.security_broker_short}} Manager and {{site.data.keyword.security_broker_short}} Shield to get the public {{site.data.keyword.security_broker_short}} Manager URL and a private {{site.data.keyword.security_broker_short}} Shield URL.

## {site.data.keyword.security_broker_short}} Manager on a private ROKS cluster
{: #private_vpc_roks_dsb_manager}

1. If you do not have access to the Red Hat Openshift Console UI to access the cluster, you can follow the two steps mentioned below to arrive at the {{site.data.keyword.security_broker_short}} Manager URL:

   a. Using the Virtual Machine (VM) user interface deployed within the VPC.
      
      - Login to the Red Hat Openshift cluster using ibmcloud shell, and execute the following command:
        ```sh
        oc get routes dsb-manager -n <data_security_broker_manager_deployment_projectname>
        ```
        {: codeblock}

      where **data_security_broker_manager_deployment_projectname** is the project name that you created or selected during the {{site.data.keyword.security_broker_short}} Manager installation.
      - Login to the Virtual Machine and open the URL, where you have the web browser installed.

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

        - Wait for the load balancer to get into **Active** state. This process might usually take from five to ten minutes.

        - Copy the load balancer by executing the command:
          ```sh
          oc get svc dsb-nginx-public -n <data_security_broker_manager_deployment_projectname>
          ```
          {: codeblock}

## {site.data.keyword.security_broker_short}} Shield on a private ROKS cluster
{: #private_vpc_roks_dsb_shield}



## Private VPC IKS cluster
{: #private_vpc_iks}

## {site.data.keyword.security_broker_short}} Manager on a private IKS cluster
{: #private_vpc_iks_dsb_manager}

## {site.data.keyword.security_broker_short}} Shield on a private IKS cluster
{: #private_vpc_iks_dsb_shield}


