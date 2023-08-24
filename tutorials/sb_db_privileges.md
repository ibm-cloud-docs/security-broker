---
copyright:
  years: 2023
lastupdated: "2023-08-24"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Database Privileges
{: #sb_db_priveleges}

In this section, you can find the details about minimum required database privileges for encryption using {{site.data.keyword.security_broker_short}}.
{: shortdesc}

## Database privileges for encryption and migration
{: #sb-db-priveleges-encrypt-decrypt}

To carry out encryption and migration, {{site.data.keyword.security_broker_short}} Shield requires
certain user permissions on the database. It is recommended that you create a new user on your database for {{site.data.keyword.security_broker_short}} Shield to use.

## Database privileges required for PostgreSQL 12
{: #sb-db-priveleges-postgresql}

| **Operation**                                                                   | **Details**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | **Queries used by Shield**                                                                               | **Minimum required grants**                                                                       |
|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| Proxy normal operation: Support implicit inserts, and Obtain column information | Access information_schema to get information about columns. This is needed to support queries such as implicit inserts (inserts that don’t have column names specified explicitly). [Per database or per schema or per table that is defined in {{site.data.keyword.security_broker_short}}] select ordinal_position, column_name, data_type from information_schema .COLUMNS where table_catalog=Database Name and table_schema=Schema Name, and table_name=TableName order by ordinal_position | Select grant is required for all tables that are defined in {{site.data.keyword.security_broker_short}}. | If a new database, schema or column is added to your protection plan, ensure the grant is applied |
| CheckProxyPort                                                                  | Check if the port specified for the Shield is responsive                                                                                                                                                                                                                                                                                                                                                                                                                                         | Select 1                                                                                                 | Select grant                                                                                      |
|                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                          |                                                                                                   |
{: caption="Table 1. Database privileges required for PostgreSQL 12 in {{site.data.keyword.security_broker_short}} Manager caption-side="bottom"}

