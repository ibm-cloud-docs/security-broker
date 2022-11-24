---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-24"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

## Apply an RBAC policy to columns
{: #sb_apply_rbac_policy}

This task demonstrates how to select an RBAC policy for an application
and apply it to selected columns in a table. You may optionally select
an encryption mode on the same columns, to transform the underlying
data. 

**Note**:

-   Only one RBAC policy can be applied to a column. 

-   RBAC policies are application-specific and cannot be shared with
    other applications. 

-   RBAC policies have a dependency on data types, because only certain
    Mask Modes can be applied for certain data types. In the Column
    selector, only compatible RBAC Policies are available to select for
    each column.

-   Editing an RBAC policy affects all columns to which the policy is
    already applied. 

**To apply an RBAC policy to columns, do the following**:

1. In {{site.data.keyword.security_broker_short}} Manager, navigate to
the **Applications **dashboard, select an application from the listing,
and click **Encrypt** to access the Schema Builder.

2. In the Tree Menu, select a database, schema, and table. This populates the column selector with available columns.

3. Select columns to define with an RBAC policy.

4. In the Data Protection dropdown menu, select an RBAC policy from the list. RBAC policies have a dependency on data types, because only certain Mask Modes can be applied for certain data types. Therefore, in the Column selector, only compatible RBAC Policies are available to select for each column.

5. By default, the standard Encryption mode 'DEFAULT_CTR_DET' is selected. When an RBAC Policy and Encryption mode are selected on the same column, then the underlying database is encrypted as well. To apply
an RBAC policy without encrypting, use the **Clear Selections **option, then select the RBAC policy.

6.**Optional:** Specify a Key ID for each column from the drop-down menu or accept the default.

7. Click **REVIEW** at the bottom left panel to review your selections.

8. Review your policy and select a Migration Plan:

1.  **Save**: Saves the data schema for future use.

2.  **Deploy**: Establishes a data schema for an environment that was not rocessed through {{site.data.keyword.security_broker_short}} migration and data type conversion but does not migrate the data.

3.  **Deploy and Migrate**: Establishes a data schema *and* transforms the existing data in the data store.

**NOTE:** If you have only configured RBAC Policies, without
specifying encryption, then the **Deploy and Migrate** option is not
available. This is because RBAC does not transform the underlying
data. 

