---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-21"

keywords: users, admin, priveleges, profiles, Data Security Broker Manager, SMTP

subcollection: security-broker
---

# Troubleshooting scenarios for IBM Cloud Data Security Broker
{: #sb_support}

This section describes the common error scenarios and troubleshooting
steps for Data Security Broker.

You can find troubleshooting tips on the following sections:

1.  Initialization

2.  Database enrolment

3.  Shield enrolment

4.  Keystore enrolment

5.  Application workflow

## Initialization and setup:
{: #sb_init}

If you get error messages or warnings during the initialization or the
setup of Data Security Broker, check for the following troubleshooting
tips:

1.  Untrusted certificate browser warning: HTTPS certificate has not
    been updated: This warning occurs when the Data Security Broker
    Manager's pre-scanned certificate does not match the hostname of the
    Manager server. Upload an HTTPS certificate in the **Settings** page
    of the Data Security Broker Manager.

## Database enrollment:
{: #sb_database}

If you get error messages or warnings during the database enrolment,
check for the following troubleshooting tips:

1.  Database credentials are incorrect: Ensure the Database Username and
    Password are correct.

2.  Hostname or IP address is not submitted: Copy and paste the database
    endpoint precisely in the appropriate field, with no extra
    characters or spaces.

3.  SSL certificate is not accepted: Ensure you have uploaded a valid
    SSL certificate.

4.  Max connections reached on the database: Some database instances
    contain a limit on the maximum allowed connections to the server.

5.  If the Postgres database is not connecting, check for the following
    troubleshooting tips:

-   Specify the Postgres Database name.

-   For PostgreSQL database servers, you must also pass the name of the
    database itself, which you intend to connect.

-   The default name is postgres; however, if there is not a database
    named "postgres" on your server, then the connection fails.

## Shield enrollment:
{: #sb_shield}

If you get error messages or warnings during the Shield enrollment,
check for the below scenarios:

1.  Hostname or IP address is not submitted: Copy and paste the Shield
    host endpoint precisely in the appropriate field, with no extra
    characters or spaces.

2.  Shield host is already in use by Data Security Broker: Multiple
    Shields may be hosted on the same endpoint, but only if the port
    number is unique. If the same port number is reused, the connection
    fails.

3.  Public IPv4 address is configured: If all Data Security Broker
    resources are running in the same environment, then it is
    recommended to use the private IP address. Alternatively, submit the
    DNS endpoint for the instance.

4.  Insufficient permissions to write to the temporary directory: The
    Host User must have write permissions for a temporary directory on
    the Shield host. The default directory is **/tmp**. If the Host User
    does not have permissions for **/tmp**, submit an alternative
    temporary path in the appropriate field.

## Keystore enrollment:
{: #sb_keystore}

If you get error messages or warnings during the Keystore enrolment,
check for the following troubleshooting tips:

1.  Permissions are insufficient: Ensure the user credentials which is
    connect to the configured Keystore have adequate permissions.

## Application workflow:
{: #sb_app}

If you get error messages or warnings during the application workflow,
check for the following troubleshooting tips:

1.  A Shield is not available for enrollment in an application: The
    Shield is already enrolled in another application. Shields may only
    be used in one application at a time.

2.  Encrypt button is disabled: Shield is initializing, restarting, or
    stopped.

**Note**: The Shields enrolled in an application must all be in a
**running** state to enable the Encryption operations.

3.  Shield connection to the database fails: Database credentials are
    changed. The Database Username or Database Password might have been
    updated; from the time the connection was created in Manager.

4.  Database grants are insufficient: The database credentials which the
    Shield uses to create a session must have a minimum set of
    permissions.

5.  Shield does not use SSL: If the database connection uses SSL, then
    the Shield connection must also use SSL.

6.  Custom Data Protection mode is not visible in the Data Protection
    dropdown for selection: Custom mode is invalid for the selected
    datatype. Certain custom encryption modes and masking modes may only
    be applied on data types.

7.  Multiple Data Protection modes are selected on one column: Default
    Data Protection is overridden: By design, default data protection
    policies may be applied on any column. If a custom or
    column-specific Encryption Mode or Masking Mode is simultaneously
    selected for a column, then the default policy is ignored. The
    custom selection is applied.

8.  Option to Deploy Policy & Migrate Data is disabled: Shield is
    initializing, restarting, or stopped. The Shields enrolled in an
    application must all be in a **running** state to enable the
    Encryption operations. Or, if no Shields are enrolled in the
    application, the migration option is disabled.

If you are experiencing any other issues with the Data Security Broker,
go to the IBM Cloud [Support Center](https://cloud.ibm.com/unifiedsupport/supportcenter) and navigate
to creating a case. Use the All products option to search for IBM Cloud Data Security Broker to continue creating the case or to find more information about getting support.

