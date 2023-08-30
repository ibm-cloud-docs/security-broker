---
copyright:
  years: 2023
lastupdated: "2023-08-22"

keywords: users, admin, priveleges, profiles,

subcollection: security-broker
content-type: troubleshoot
---

{{site.data.keyword.attribute-definition-list}}
{:troubleshoot: data-hd-content-type='troubleshoot'}


# How to resolve the database related issues?
{: #sb_support_database}
{: troubleshoot}
{: support}

You face database-specific issues.
{: shortdesc}

You get errors or warnings during database enrolment.
{: tsSymptoms}

If you get error messages or warnings during the database enrolment, check for the following troubleshooting tips:
{: tsResolve}

1. Message: Database credentials are incorrect

   Ensure the Database Username and Password are correct.

2. Message: Hostname or IP address is not submitted

   Copy and paste the database endpoint precisely in the appropriate field, with no extra characters or spaces.

3. Message: SSL certificate is not accepted

   Ensure you have uploaded a valid SSL certificate.

4. Message: Max connections reached on the database

   Some database instances contain a limit on the maximum allowed connections to the server. For example, if the Postgres database is not connecting, check for the following troubleshooting tips:

   - Specify the Postgres Database name.
   - For PostgreSQL database servers, you must also pass the name of the database itself, which you intend to connect.
   - The default name is postgres; however, if there is not a database named "postgres" on your server, then the connection fails.
