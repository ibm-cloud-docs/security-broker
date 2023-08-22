---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: deploy policy, deployment plans, encryption technology, encryption modes, data protection modes

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Deployment Plans in {{site.data.keyword.cloud_notm}} {{site.data.keyword.security_broker_short}}
{: #sb-deployment-plans}

When you assign and customize default Data Protection Policies with {{site.data.keyword.security_broker_short}} Manager, there are three options that you can choose to
implement your data encryption policy:

## Save Policy
{: #sb-save-policy}

**Save Policy** option is selected by default. This option saves your selected data, but does not execute encryption or data protection on your database. Your policy remains saved with the application until a new policy is saved to overwrite it. You can use the saved policy to deploy or migrate it later.

## Deploy Policy
{: #sb-deploy-policy}

**Deploy Policy** option saves your policy and deploys your configured {{site.data.keyword.security_broker_short}} Shield as a proxy for the configured database. You can connect to your {{site.data.keyword.security_broker_short}} Shield endpoint, as if it was your database endpoint, to access your database.
Any data that passes through your {{site.data.keyword.security_broker_short}} Shield proxy is
encrypted in the database, if that data is defined in your policy.

## Deploy Policy and Migrate Data
{: #sb-deploy-migrate-data}

**Deploy Policy & Migrate Data** option saves your policy, deploys it, and migrates your existing selected tables and columns through the specified {{site.data.keyword.security_broker_short}} Shield to encrypt the data. 
{{site.data.keyword.security_broker_short}} Shield acts as a proxy for the configured database, and the data is encrypted as well.

This option is disabled for applications, which does not have a {{site.data.keyword.security_broker_short}} Shield associated with it.
{: note}

