---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-23"

keywords: users, admin, priveleges, profiles, {{site.data.keyword.security_broker_short}} Manager, SMTP

subcollection: security-broker
---

# How to resolve the Application workflow issues?
{: #sb_workflow}

If you get error messages or warnings during the application workflow, check for the following troubleshooting tips:

1. Encrypt button is disabled: Shield is initializing, restarting, or stopped.

   The Shields enrolled in an application must all be in a **running** state to enable the Encryption operations.
   {: note}

2. Shield connection to the database fails: Database credentials are changed. The Database Username or Database Password might have been updated; from the time the connection was created in Manager.

3. Database grants are insufficient: The database credentials which the Shield uses to create a session must have a minimum set of permissions.

4. Shield does not use SSL: If the database connection uses SSL, the Shield connection must also use SSL.

5. Custom Data Protection mode is not visible in the Data Protection dropdown for selection: Custom mode is invalid for the selected datatype. Certain custom encryption modes and masking modes may only be applied on data types.

6. Multiple Data Protection modes are selected on one column: Default Data Protection is overridden: By design, default data protection policies may be applied on any column. If a custom or column-specific Encryption Mode or Masking Mode is simultaneously selected for a column, then the default policy is ignored. The custom selection is applied.

7. Option to Deploy Policy & Migrate Data is disabled: Shield is initializing, restarting, or stopped. The Shields enrolled in an application must all be in a **running** state to enable the Encryption operations. Or, if no Shields are enrolled in the application, the migration option is disabled.

   If you are experiencing any other issues with the {{site.data.keyword.security_broker_short}},
   go to the IBM Cloud [Support Center](https://cloud.ibm.com/unifiedsupport/supportcenter) and navigate
   to creating a case. Use the All products option to search for {{site.data.keyword.security_broker_full_notm}} to continue creating the case or to find more information about getting support.

