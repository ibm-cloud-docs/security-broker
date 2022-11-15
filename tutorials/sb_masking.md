---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-15"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Data Masking
{: #sb_masking}

## Overview:
{: #sb_mask_overview}

{{site.data.keyword.security_broker_short}} Shield can mask encrypted data and return the data
in a user-friendly format without decryption or with partial decryption.

# Configure RBAC for an application

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

d.  **Key Value Pairs** (optional) to consume key-value pairs in a
    line-by-line format. Each key must be specified on a single line, in
    <key>:<value> format.

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
and then select **Restart Shield**. The configuration is saved for the
selected application.

8. Continue to configure user groups.

**Note:** You can edit your RBAC Configuration at any time, including
the Mode and User settings.

## Configure user groups
{: #sb_mask_ug}

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

1. In the Data Protection Policies section, expand **RBAC** and
select **User Groups**. Click **Create User Groups**.

2. In the User Groups panel, enter a **User Group Name** of 30
characters or less, and a unique **Description** of 100 characters or
less.

3. **Optional** Select the **Global** checkbox to create a group where
individual Users are ignored. Anyone connecting to the Shield has
membership to this Global group, provided their IP address is within
the **Allowed Subnets** range. If you select Global, proceed with step 5.

4. Enter usernames as a CSV-formatted list in the **Users** text box.
This is the list of client IDs which {{site.data.keyword.security_broker_short}} Shield will
consider when the User Determination is set to either **SESSION** or **SQL_COMMENT_RAW**.

5. **Optional:** Enter a range of permitted IP addresses as **Allowed
Subnets**. When subnets are configured, a user's membership depends on
the following conditions:

1.  User is specified in the Users box (User Determination is either
    SESSION or SQL_COMMENT_RAW) 

    1.  **OR** User is specified by the JWT (User Determination is
        SQL_COMMENT_JWT)

2.  **AND** User has an IP address in the permitted range. 

Multiple IP address ranges can be specified for one group, separated by
commas. Spaces between IP addresses are ok.

**Note:** If **Allowed Subnets** is empty or 0.0.0.0/0 is specified,
then **ALL IPs** are permitted for that group.

6\. Click **Save**. 

7\. Perform one of the following actions:

-   Continue to Task 3 to create an RBAC Policy.

-   Create another user group.

## **Task 3. Create an RBAC policy**

The RBAC Policy Builder allows you to define Rules---that is,
permissions for user groups. One or more groups can be given READ,
READ_WRITE, or MASK permissions. The group-to-permission mapping
constitutes a single Rule, which in turn is added to the policy. Once a
policy is established, you can apply it to selected columns in a table,
thereby determining ***who*** has access to*** what*** data.

#### To create an RBAC policy, do the following:

1\. In the Data Protection Policies section, expand **RBAC** and
select **Policies.** On the RBAC Policy Builder panel, click **Create
RBAC Policy**. You also have the option for creating another user group
before going on to create a policy.

2\. In the Policy Builder panel, enter a **Policy Name** of 30
characters or less, and a unique **Description** of 100 characters or
less.

3\. From the Default Permissions drop-down, select one of the
following. **NOTE: **The Default Permission is applied to any user or
client connection who does not belong to a user group in the given RBAC
policy. 

1.  **READ** assigns read-only permission as the default. The user sees
    clear data.

2.  **READ_WRITE** assigns read and write permissions as the default.
    The user sees clear data and writes via Shield.

3.  **MASK** assigns a data masking format as the default. The user sees
    masked data, according to the **Mask** mode specification that is
    selected here.  

4.  All Mask Modes are available for selection. To **configure a mask
    mode**, refer to
    this [article](https://support.baffle.io/hc/en-us/articles/4418260284439).  

4\. Next, add a Rule to the Policy. Each Rule consists of two pieces:
User Groups and Permission. The individual Rule maps a Permission to one
or more User Groups. 

**Note: **A policy can have an unlimited number of rules, or no rules.
An RBAC Policy with no rules, containing only the Default Permission,
can be used to apply simple data masking for all Users which connect to
the Shield.

1.  Enter a **Rule Name** of 30 characters or less.

2.  Select relevant User Groups from the drop-down list. All User Groups
    are available, but only one Rule will be considered per User. See
    step 5. 

3.  Select a **Permission** option from the
    drop-down: **READ**, **READ_WRITE**, or **MASK**. 

**NOTE: **MASK permission allows you to specify an existing Masking
mode for a given user group. In other words, upon accessing the data,
members of that group view the data in the mask format that you
specify. 

5\. RBAC policy rules must be arranged in a hierarchy. Reorder the rules
by clicking the Up and Down arrows to update the Rank number in the
policy.\
\
**Note on Rule hierarchy:** Technically, an individual database user can
have membership to more than one user group. However, this exposes a
potential contradiction where multiple rules could apply to an
individual database user. To avoid this, Rules must be arranged in a
hierarchy, where only the highest-ranked rule is considered for each
user group, and each user.

**Example:** A database user "DSBAdmin" belongs to two User Groups,
"Administrators" and "All-Users". Here is a policy with two
corresponding rules, named "Permit Admins" and "Restrict All Users".
Even though "DSBAdmin" has membership to both groups, and therefore both
rules, only the top-ranked Rule is considered. Therefore, "DSBAdmin" has
READ_WRITE permission, *not* MASK_VARCHAR permission.

6.** Optional:** Create another rule by clicking **+ Rule**. 

Rules can be collapsed, expanded and deleted. When collapsed, only the
Rule Name and Rank are visible.\
7. When you are satisfied with the policy, click **Save**. Role-Based
Access Control is fully configured, and ready to apply to columns.

8.** Optional:** After saving the policy, create another User Group or
create another RBAC Policy.

9\. Continue to Task 4, Apply an RBAC policy to columns. 

## **Task 4. Apply an RBAC policy to columns**

This task demonstrates how to select an RBAC policy for an application
and apply it to selected columns in a table. You may optionally select
an encryption mode on the same columns, to transform the underlying
data. 

#### Note:

-   Only one RBAC policy can be applied to a column. 

-   RBAC policies are application-specific and cannot be shared with
    other applications. 

-   RBAC policies have a dependency on data types, because only certain
    Mask Modes can be applied for certain data types. In the Column
    selector, only compatible RBAC Policies are available to select for
    each column.

-   Editing an RBAC policy affects all columns to which the policy is
    already applied. 

#### To apply an RBAC policy to columns, do the following:

1\. In {{site.data.keyword.security_broker_short}} Manager, navigate to
the **Applications **dashboard, select an application from the listing,
and click **Encrypt** to access the Schema Builder.

2\. In the Tree Menu, select a database, schema, and table. This
populates the column selector with available columns.

3\. Select columns to define with an RBAC policy.

4\. In the Data Protection dropdown menu, select an RBAC policy from the
list. RBAC policies have a dependency on data types, because only
certain Mask Modes can be applied for certain data types. Therefore, in
the Column selector, only compatible RBAC Policies are available to
select for each column.

5\. By default, the standard Encryption mode 'DEFAULT_CTR_DET' is
selected. When an RBAC Policy and Encryption mode are selected on the
same column, then the underlying database is encrypted as well. To apply
an RBAC policy without encrypting, use the **Clear Selections **option,
then select the RBAC policy.

6.** Optional:** Specify a Key ID for each column from the drop-down
menu or accept the default.

7\. Click** REVIEW** at the bottom left panel to review your selections.

8\. Review your policy and select a Migration Plan:

1.  **Save**: Saves the data schema for future use.

2.  **Deploy**: Establishes a data schema for an environment that wasn't
    processed through {{site.data.keyword.security_broker_short}} migration and data type
    conversion but does not migrate the data.

3.  **Deploy and Migrate**: Establishes a data schema *and* transforms
    the existing data in the data store.

> **NOTE:** If you have only configured RBAC Policies, without
> specifying encryption, then the **Deploy and Migrate** option is not
> available. This is because RBAC does not transform the underlying
> data. 

## **Apply simple masking on clear data**

This section describes a simple RBAC policy to apply basic data masking
for all users, considering each of the four tasks in this document.

#### Step 1: RBAC configuration: session

Here, we enforce RBAC for all connections to Shield, by setting the Mode
= Required. Also, we set User Determination = Session, to reference the
DB session user ID for User Group membership. However, because we are
configuring a global RBAC policy, the User Determination is not relevant
in this case.

#### Step 2: User group: All-Users

You can create a Global user group called "All-Users". We select the
Global checkbox and do not specify any Allowed Subnets. (0.0.0.0/0 is
automatically filled when this text box is left blank.) This User Group
applies to all possible connections to Shield. 

#### Step 3: RBAC policy: Default Masking

You can create two Masking policies which are nearly identical. The only
difference is that one policy applies for VARCHAR columns, and the other
applies for INT columns. The parameters are as follows:

The first policy, "Default Varchar Masking", has one Rule to
use **MASK_VARCHAR** for the **All-Users** user group. The second
policy, "Default Int Masking", has one Rule to use **MASK_INT** for
the **All-Users** user group. 

Because both rules contain the global **All-Users** group, the default
permission is irrelevant in this case.

#### Step 4: Application of Masking policies on data columns:

Finally, we select a number of columns to mask. For each column, we
remove the DEFAULT_CTR_DET selection and add one or the other RBAC
policy based on the Data Type.

On the Confirmation page, we can review the data protection schema.
Because there is no Encryption defined, and no data transformation
taking place, the option for **Deploy & Migrate** is unavailable. 

Now, we can Deploy the policy. If we connect to the Shield proxy, we can
see the Data Masking has been applied to the selected columns.

## **Working with Masking Modes**

Data Masking obfuscates data values into a predefined format that is
typically irreversible. A Masking Mode defines the format used to mask
selected data. You can create new Masking Modes and use them in a policy
or map them to a column. 

**Creating a new masking mode**

This section demonstrates how to create a new masking mode that is added
to the Data Protection Library. 

To create a masking mode, do the following:

1.  Go to the Data Protection Library and in the header, click the Plus
    (**+**) sign to begin creating a new mode.

2.  Select **Masking Mode** from the drop-down list. The Masking Mode
    Builder dialog appears.

3.  Enter a unique **Mask Mode Name** (30 characters or less) and
    optionally, a **Description** of up to 100 characters.

4.  Select one of the following options from the Mask Mode drop-down
    menu: FIXED, PATTERN, NUMERIC, CHARACTER.

5.  In the **Mask Format** field, enter the string to be used to mask
    the data. 

6.  Click **Save**. The new masking mode appears in the Data Protection
    Library, as well as a selection in the **Encryption Mode** drop-down
    menu.\
    \
    **Note**: The compatible data types are automatically associated
    with the mode when you click Save. In this way, only the modes that
    are compatible with a column's data type are shown. 

**Viewing and editing a masking mode**

This section demonstrates how to view and edit Masking Modes. However,
editing is limited to modifying the name and description of the selected
mode. 

To view the details of a masking mode, do the following:

1.  Go to the Data Protection Library and click the carrot icon (**\>**)
    next to **Masking Modes **to view the list of modes.

2.  Select a mode from the list. The details for the mode appear in the
    window on the right.

To edit a masking mode, do the following:

1.  Go to the Data Protection Library and click the carrot icon (**\>**)
    next to **Masking Modes **to view the list of modes. The details for
    the mode appear in the window on the right.

2.  Click the **Pencil** icon in the upper right corner to edit the
    mode.

3.  Modify the **Mask Mode Name **as desired.

4.  Modify the **Description** for the mode as desired.

5.  Click **Save**.
