---
copyright:
  years: 2022, 2023
lastupdated: "2023-06-15"

keywords: database, certificate, priveleges, users, features, operations, application

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Update Database Certificate
{: #sb_update_db}

You need to update the database certificate in {{site.data.keyword.security_broker_short}} Manager before it expires. Ensure that you keep a track on the database certificate expiry date. If the database certificate expires, the connection between the application and the database is lost. 

To update the database certificate, complete the following steps in the {{site.data.keyword.security_broker_short}} Manager:

1. Click **Databases** from the left navigation and select a database.

2. Click **Update** in the Database Summary pane on the right to update the Database Certificate.

Once you update the database certificate, the {{site.data.keyword.security_broker_short}} Shield is restarted and this might result in a brief outage of connectivity between the database and the application.
{: note}

