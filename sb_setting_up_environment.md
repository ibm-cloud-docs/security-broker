---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: deploy policy, deployment plans, encryption technology, encryption modes, data protection modes

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Setting up your environment
{: #sb-setting_up_environment}

## Before you begin
{: #sb-before-you-begin}

Before you begin installing and configuring the {{site.data.keyword.security_broker_short}}, ensure that you have met the following requirements:

- Create an {{site.data.keyword.cloud_notm}} account.
- Set up your environment.
- Set up the minimum permissions required in the {{site.data.keyword.cloud_notm}} account.

Ensure that your environment meets the following minimum system level and resource level requirements:

| Cluster                                  | Operating System       | Number of Worker nodes required |
|------------------------------------------|------------------------|---------------------------------|
| {{site.data.keyword.redhat_openshift_full}} cluster | RHEL7/RHEL8 and CoreOS | 2                               |
| {{site.data.keyword.cloud_notm}} Kubernetes cluster             | Ubuntu 18              | 2                               |
{: caption="Table 1. Resource level requirements for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}  

## Minimum permissions required to install, set up, and  access {{site.data.keyword.security_broker_short}}
{: #sb_getting_assign_permission}

As an {{site.data.keyword.cloud_notm}} user, you need to set the follwoing minimum permissions to install, set up and access {{site.data.keyword.security_broker_short}}. 
By using the following steps and the information in the table, assign the required permissions:
1. Log into your {{site.data.keyword.cloud_notm}} account and click **Manage -> Access (IAM)**.
2. In the Manage access and users dashboard, click **View all** in the **My user details** section.
3. In the **Access** tab, click **Assign access +**. From the Table 2, select a service and click **Next**.
4. In the **Roles and actions** section, select the specified permissions that are required.
5. Click **Add** and **Assign** to assign the permissions required.

| Service Name                            | Permission level       |
|-----------------------------------------|------------------------|
| {{site.data.keyword.keymanagementserviceshort}}                             | Writer                 |
| {{site.data.keyword.cos_full}}                   | Manager                |
| {{site.data.keyword.containershort}}                     | Manager, Editor        |
| IBM {{site.data.keyword.redhat_openshift_notm}} {{site.data.keyword.containershort}} | Editor                 |
| {{site.data.keyword.bpshort}}                              | Manager, Administrator | 
{: caption="Table 3. Permissions required for {{site.data.keyword.security_broker_short}}" caption-side="bottom"}

You can find details about platform roles and the actions mapped to each of the role in the table below: 

| Platform Roles | Description                                                                                                                                                        |   |   |   |
|:--------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| Administrator  | As an administrator, you can  perform all platform actions based on the resource this role is being  assigned, including assigning access policies to other users. |   |   |   |
| Editor         | As an editor, you can perform all platform actions except for managing the account and assigning access policies.                                                  |   |   |   |
| Operator       | As an operator, you can  perform platform actions required to configure and operate service  instances, such as viewing a service's dashboard.                     |   |   |   |
| Viewer         | As a viewer, you can view service instances, but you can't modify them.                                                                                            |   |   |   |
{: caption="Table 4. Platform roles and their actions" caption-side="bottom"}

