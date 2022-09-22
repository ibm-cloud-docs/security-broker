---
copyright:
  years: 2022, 2022
lastupdated: "2021-09-01"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Database Privileges for {{site.data.keyword.security_broker_short}}
{: #sb_db_priveleges}

In this section, you can find the details about required database
privileges for encryption and migration using Security Broker, and the
minimum required database privileges.
{: shortdesc}

## Database privileges for encryption and migration
{: #sb-db-priveleges-encrypt-decrypt}

To carry out encryption and migration, Security Broker Shield requires
certain user permissions on the database. It is recommended that you
create a new user on your database for Security Broker Shield to use.

Use the SQL client to provide the required access for the newly created
on your database for Security Broker Shield:

To create a user, execute the following command:

```sh
create user '<security_broker_user>'@'%'
```
{: codeblock}  

```sh
set password for '<security_broker_user>' = password('<password>')
```
{: codeblock}   

To provide the required admin permissions, execute the following
command:

```sh
GRANT USAGE ON *.* TO '<security_broker_user>'@'%'
```
{: codeblock} 

```sh
GRANT ALL PRIVILEGES ON shadow_information_schema.* TO '<security_broker_user>'@'%'
```
{: codeblock}

```sh
GRANT ALL PRIVILEGES ON **target database**.* TO '<security_broker_user>'@'%' WITH GRANT OPTION
```
{: codeblock}

4.  Repeat Step 3 for each database that you wish to encrypt.

After completing the above steps, the {{site.data.keyword.security_broker_short}} Shield contains the necessary permissions to perform the encryption and migration operation.

## Minimum required database privileges
{: #sb-db-min-req-priveleges}

You can view the minimum required grants for users on your database who
needs the least access privileges. Use the SQL client to issue the
following command with the admin user credentials.

From MySQL, execute the following command:

```sh
GRANT USAGE ON *.* TO '<username>'@'%'
```
{: codeblock}

```sh
GRANT ALL PRIVILEGES ON shadow_information_schema.* TO '**username**'@'%'
```
{: codeblock}

```sh
GRANT SELECT ON <target_database>.<target table> TO '<username>'@'%'
```
{: codeblock}

To confirm the user privileges, execute the following command:
```sh
show grants
```
{: codeblock}


