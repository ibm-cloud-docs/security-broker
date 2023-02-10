---
copyright:
  years: 2022, 2022
lastupdated: "2023-02-08"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Create an RBAC policy
{: #sb_rbac_policy}

The RBAC Policy Builder allows you to define Rules, which is, the permissions for user groups. One or more groups can be given READ, READ_WRITE, or MASK permissions. The group-to-permission mapping
constitutes a single Rule, which in turn is added to the policy. Once a
policy is established, you can apply it to the selected columns in a table,
thereby determining ***who*** has access to **what** data.

To create an RBAC policy, do the following:

1. In the Data Protection Policies section, expand **RBAC** and select **Policies.**

On the RBAC Policy builder panel, click **Create RBAC Policy**. You also have the option for creating another user group before creating a policy.

2. In the Policy Builder panel, enter a **Policy Name** of 30 characters or less, and a unique **Description** of 100 characters or less.

3. From the Default Permissions drop-down, select one of the following. 

**NOTE:** The Default Permission is applied to any user or client connection who does not belong to a user group in the given RBAC policy. 

a.  **READ** assigns read-only permission as the default. The user sees
    clear data.

b.  **READ_WRITE** assigns read and write permissions as the default.
    The user sees clear data and writes via Shield.

c.  **MASK** assigns a data masking format as the default. You can see the masked data, according to the **Mask** mode specification that is selected.  

d.  All Mask Modes are available for selection.

4. Add a Rule to the Policy. Each Rule consists of two pieces:

User Groups and Permission. The individual Rule maps a Permission to one
or more User Groups. 

**Note**: A policy can have an unlimited number of rules, or no rules.
An RBAC Policy with no rules, containing only the Default Permission,
can be used to apply simple data masking for all Users which connect to
the Shield.

a.  Enter a **Rule Name** of 30 characters or less.

b.  Select relevant User Groups from the drop-down list. All User Groups
    are available, but only one Rule will be considered per User. See
    step 5. 

c.  Select a **Permission** option from the
    drop-down: **READ**, **READ_WRITE**, or **MASK**. 

**Note**: MASK permission allows you to specify an existing Masking
mode for a given user group. In other words, upon accessing the data,
members of that group view the data in the mask format that you
specify. 

5. RBAC policy rules must be arranged in a hierarchy. Reorder the rules by clicking the Up and Down arrows to update the Rank number in the policy.

**Note on Rule hierarchy:** Technically, an individual database user can have membership to more than one user group. However, this exposes a potential contradiction where multiple rules could apply to an
individual database user. To avoid this, Rules must be arranged in a hierarchy, where only the highest-ranked rule is considered for each user group, and each user.

**Example:** A database user "DSBAdmin" belongs to two User Groups, "Administrators" and "All-Users". Here is a policy with two
corresponding rules, named "Permit Admins" and "Restrict All Users".
Even though "DSBAdmin" has membership to both groups, and therefore both
rules, only the top-ranked Rule is considered. Therefore, "DSBAdmin" has
READ_WRITE permission, *not* MASK_VARCHAR permission.

6.**Optional:** Create another rule by clicking **+ Rule**. 

Rules can be collapsed, expanded and deleted. When collapsed, only the
Rule Name and Rank are visible.

7. When you are satisfied with the policy, click **Save**. Role-Based Access Control is fully configured, and ready to apply to columns.

8. **Optional:** After saving the policy, create another User Group or create another RBAC Policy.

9. Continue with applying an RBAC policy to the database columns. 

