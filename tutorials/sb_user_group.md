---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-24"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

## Configure user groups
{: #sb_user_group}

User Groups allow you to define groups of database-level users and
permitted IP addresses, based on the desired role and permission level.
User groups are mapped to permissions to create an RBAC policy.
User groups are also shared across all applications on your {{site.data.keyword.security_broker_short}} Manager. If a group's membership is modified, the change
is persisted in every policy and application where the group is
selected.

**Note**:

-   The Users list can be changed at any time. You are simply changing
    the membership of a given User Group. There is no impact on the rest
    of the RBAC configuration, other user groups, or policies.

-   Allowed Subnet(s) can be changed at any time. You are changing the
    allowed subnets for a given User Group. There is no impact on the
    rest of the RBAC configuration, other user groups, or policies. 

To configure RBAC user groups, perform the following:

1. In the Data Protection Policies section, expand **RBAC** and select **User Groups**. Click **Create User Groups**.

2. In the User Groups panel, enter a **User Group Name** of 30 characters or less, and a unique **Description** of 100 characters or less.

3. **Optional**: Select the **Global** checkbox to create a group where individual Users are ignored. 

Anyone connecting to the Shield has membership to this Global group, provided their IP address is within
the **Allowed Subnets** range. If you select Global, proceed with step 5.

4. Enter usernames as a CSV-formatted list in the **Users** text box. 

This is the list of client IDs which {{site.data.keyword.security_broker_short}} Shield will consider when the User Determination is set to either **SESSION** or **SQL_COMMENT_RAW**.

5. **Optional:** Enter a range of permitted IP addresses as **Allowed Subnets**. When subnets are configured, a user's membership depends on the following conditions:

a.  User is specified in the Users box (User Determination is either
    SESSION or SQL_COMMENT_RAW) or User is specified by the JWT (User Determination is
    SQL_COMMENT_JWT) and User has an IP address in the permitted range. 

Multiple IP address ranges can be specified for one group, separated by commas. Spaces between IP addresses are fine.

**Note:** If **Allowed Subnets** is empty or 0.0.0.0/0 is specified, then **ALL IPs** are permitted for the user group.

6. Click **Save**. 

7. Perform one of the following actions:

-   Continue to create an RBAC Policy.

-   Create another user group.

