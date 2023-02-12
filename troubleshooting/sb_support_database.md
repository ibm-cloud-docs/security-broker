---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-12"

keywords: users, admin, priveleges, profiles, {{site.data.keyword.security_broker_short}} Manager, SMTP

subcollection: security-broker
---

# How to resolve the Database related issues?
{: #sb_support_database}

If you get error messages or warnings during the database enrolment, check for the following troubleshooting tips:

1. Message: Database credentials are incorrect

   Ensure the Database Username and Password are correct.

2. Message: Hostname or IP address is not submitted

   Copy and paste the database endpoint precisely in the appropriate field, with no extra characters or spaces.

3. Message: SSL certificate is not accepted

   Ensure you have uploaded a valid SSL certificate.

4. Message: Max connections reached on the database

   Some database instances contain a limit on the maximum allowed connections to the server.

   - If the Postgres database is not connecting, check for the following troubleshooting tips:

   a. Specify the Postgres Database name.

   b. For PostgreSQL database servers, you must also pass the name of the database itself, which you intend to connect.

   c. The default name is postgres; however, if there is not a database named "postgres" on your server, then the connection fails.
