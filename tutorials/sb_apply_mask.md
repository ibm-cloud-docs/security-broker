---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-24"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

## **Apply simple masking on clear data**
{: #sb_apply_mask}

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

