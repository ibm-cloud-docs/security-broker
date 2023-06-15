---
copyright:
  years: 2022, 2023
lastupdated: "2023-06-15"

keywords: database, admin, priveleges, users, migration, shield, migration properties

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Data Migration using {{site.data.keyword.security_broker_short}} Manager
{: #sb_data_migration}

In this section, you can find details on how to add or select specific {{site.data.keyword.security_broker_short}} Shield that is used for migration and set migration properties in {{site.data.keyword.security_broker_short}} Manager.

This option is only available when you select **Deploy Policy & Migrate Data** as the Data Protection Policy.
{: note}

1.  Login to {{site.data.keyword.security_broker_short}} Manager.

2.  Select an application and click **Encrypt** to open the Encryption Schema Builder window.

3.  Under the **Migration Shield** dropdown, select the {{site.data.keyword.security_broker_short}} Shield you need to use for migration.

    Only the Shields enrolled with the application are available for selection.
    {: note}

4.  Click **+Migration Shield**. The Add {{site.data.keyword.security_broker_short}} Shield dialog appears. Make a note in the Shield description that this shield was added for migration.

5.  Specify the necessary options and click Add {{site.data.keyword.security_broker_short}} Shield.

6.  Click Save to initiate your data protection policy. The migration process begins, and it takes place on your selected migration Shield. The new migration Shield is now visible on the Shields dashboard.

You can also modify the below Migration Properties for the Migration Plan:

- Batch Size - 2000, 50000, 100000
- Failure Scope - Server, Database, Table
- Parallel Processing - On or Off
- Clear Temp Tables - On or Off
- Migration Shield - only appears if there are multiple {{site.data.keyword.security_broker_short}} Shields





