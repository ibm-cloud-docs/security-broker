---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-24"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Configure RBAC for an application
{: #sb_configure_rbac}

Role-Based Access Control (RBAC) allows you to create policies that
specify permissions for groups of users who access a Data Security
Broker Shield. To configure RBAC, you need to add and manage user's
client addresses, user IDs to defined groups. You need to map each user
group to a permission (such as READ, READ_WRITE, or MASK) and a column
in a table. In other words, RBAC policies determine **who can see what** data. 

This RBAC configuration process is divided among four tasks:

1.  Specify RBAC Configuration

2.  Add User Groups

3.  Create an RBAC policy

4.  Apply an RBAC policy to columns

## Specify RBAC configuration
{: #sb_mask_rbac}

To specify RBAC configuration for an application, complete the following steps:

1. In {{site.data.keyword.security_broker_short}} Manager, navigate to **Applications**, select an application from the list, and click **Encrypt** to access the Encryption Schema Builder.

2. In the Data Protection Policies section, expand **RBAC** and select **RBAC Configuration**.

3. In the RBAC Configuration window on the right, click **Complete Configuration**.

4. In the window on the right, select a Mode from the drop-down list:

-   **Disable** switches off RBAC for the whole application.
    Definitions of policies and groups do not change but the shield
    does not use these policies. You can select this mode to start and
    define users and policies.

-   **Supported** switches on RBAC but does not require it for all
    connections to the Shield.

-   **Required** switches on RBAC and requires it for all sessions or
    transactions on the Shield. If the session or transaction is not
    found in a defined RBAC Policy, then that session is dropped by the
    Shield. 

5. Select an option for User Determination from the drop-down list:

-   **SESSION** signifies that the users connecting to the Shield are
    determined by the session user ID, as defined in the specified User
    Groups.

-   **SQL_COMMENT_RAW** signifies that users connecting to the Shield
    are determined by user IDs specified in SQL comments. An SQL Comment
    Prefix field appears. This field defines the prefix string for SQL
    Comments containing the User ID. Here is an example SQL query with
    the appropriate comment:
    
```sh
select * from public.table1 *+ User:user_name *
```
{: codeblock}    

-   You can specify an arbitrary string as the SQL Comment Prefix, but
    the user ID must be defined in User Groups.

-   **SQL_COMMENT_JWT** signifies users connecting to the Shield are
    determined by a JWT specified in SQL comments. An SQL Comment Prefix
    field appears. This field defines the refix string for SQL Comments
    containing the JWT.

 The JWT serves as an authenticator for the User Group. Individual User
 IDs are ignored in this RBAC mode; instead, the Role argument in the
 JWT must match a User Group Name, in order to determine group
 membership. The following options are available:

a.  **SQL Comment Prefix** -- for the prefix string for SQL Comments
    containing the JWT

b.  **JWT TID** (optional) for consuming the tenant identifier 

c.  **JWT AUD** (optional) for consuming the audience identifier 

d.  **Key Value Pairs** (optional) to consume key-value pairs in a line-by-line format. Each key must be specified on a single line, in key:value format.

e.  **JWT secret key** is required field for an HS256 key

f.  **JWKS Provider URL** is required field for a URL, for an RS256 key

**Note**: At least one of the previous two fields is required. If you
submit either a JWT secret key or JWKS Provider URL, you can proceed
without submitting the other field. The {{site.data.keyword.security_broker_short}} Shield
determines which algorithm to use.

g.  **JWKS Cache Capacity** (optional) integer value - default is 10000.
    This field is only used with RS256 keys specified by the JWKS
    Provider URL.  

6. Click **Save**. A confirmation dialog appears.

**Note**: When you update your RBAC configuration, all {{site.data.keyword.security_broker_short}} Shields enrolled with the application must be restarted. This
will cause a temporary outage of connectivity between the {{site.data.keyword.security_broker_short}} Manager application and the database.

7. Click the **Yes, restart {{site.data.keyword.security_broker_short}} Shields** checkbox
and then select **Restart Shield**. The configuration is saved for the selected application.

8. Continue to configure user groups.

**Note:** You can edit your RBAC Configuration at any time, including
the Mode and User settings.

