---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-13"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# **Apply simple masking on clear data**
{: #sb_apply_mask}

This section describes a simple RBAC policy to apply basic data masking
for all users. Follow the steps below to apply masking on the data using {{site.data.keyword.security_broker_short}} Manager.

Step 1: **RBAC configuration:**

Configure RBAC for all connections to Shield, by setting the Mode as Required. Also, set the User Determination as Session, to reference the DB session user ID for User Group membership. However, when configuring a global RBAC policy, the User Determination is not relevant.

Step 2: **User group - All-Users:**

You can create a Global user group called "All-Users". Select the Global checkbox and do not specify any Allowed Subnets. (0.0.0.0/0 is automatically filled when this text box is left blank.) This User Group
applies to all possible connections to Shield.

Step 3: **RBAC policy - Default Masking:**

You can create two Masking policies which are nearly identical. The only
difference is that one policy applies for VARCHAR columns, and the other
applies for INT columns. The parameters are as follows:

The first policy, "Default Varchar Masking", has one Rule to
use **MASK_VARCHAR** for the **All-Users** user group. The second
policy, "Default Int Masking", has one Rule to use **MASK_INT** for
the **All-Users** user group. 

Because both rules contain the global **All-Users** group, the default
permission is irrelevant in this case.

Step 4: **Application of Masking policies on data columns:**

Finally, select a number of columns to mask. For each column, remove the DEFAULT_CTR_DET selection and add one or the other RBAC policy based on the Data Type.

On the Confirmation page, review the data protection schema. Because there is no Encryption defined, and no data transformation taking place, the option for **Deploy & Migrate** is unavailable.

Deploy the policy. If you connect to the Shield proxy, you can see that the Data Masking has been applied to the selected columns.


