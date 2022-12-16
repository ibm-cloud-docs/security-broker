---
copyright:
  years: 2022, 2022
lastupdated: "2022-12-16"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Database Privileges
{: #sb_db_priveleges}

In this section, you can find the details about minimum required database
privileges for encryption using {{site.data.keyword.security_broker_short}}.
{: shortdesc}

## Database privileges for encryption and migration
{: #sb-db-priveleges-encrypt-decrypt}

To carry out encryption and migration, {{site.data.keyword.security_broker_short}} Shield requires
certain user permissions on the database. It is recommended that you
create a new user on your database for {{site.data.keyword.security_broker_short}} Shield to use.

## Database privileges required for PostgreSQL 12:
{: #sb-db-priveleges-postgresql}

|**Operation**|**Details**|**Queries used by Shield**|**Minimum required grants**|**Additional information**|
| - | - | - | :- | - |
|Proxy normal operation:- Support implicit inserts Obtain column information|Access information\_schema to get information about columns. This is needed to support queries such as implicit inserts (inserts that don’t have column names specified explicitly).|[Per database/schema/table that is defined in DSB]select ordinal\_position, column\_name, data\_type from information\_schema .COLUMNS where table\_catalog=<Dat abase> and table\_schema=<Sche ma> and table\_name=<TableN ame> order by ordinal\_position;|Select grant is required for all tables that are defined in DSB.|If a new database, schema or column is added to your protection plan, ensure the grant is applied beforehand|
|CheckProxyPort|Check if the port specified for the Shield is alive and responsive|Select 1|Select grant||
{: caption="Table 1. Database privileges required for PostgreSQL 12 in {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}

