---
copyright:
  years: 2022, 2022
lastupdated: "2022-09-15"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

# Adding users in Data Security Broker Manager
{: #sb_adding_users}

## Overview
{: #sb_users_overview}

Data Security Broker Manager supports multiple users who can access the
Manager console. All users on Data Security Broker Manager automatically
have administrative privileges, so that they can enroll databases and
applications, modify them, and deploy policies. However, only a user
with Super Admin privileges can add, invite, and delete new users. A
Data Security Broker Manager is limited to have only one Super Admin.

## Adding a user to the Data Security Broker Manager:
{: #sb_users_DSB}

Complete the following steps to add a new user to the Data Security
Broker Manager:

1.  As a Super Admin, navigate to the **Users** tab in the left
    navigation menu. Click Add User + in the top right corner. Enter an
    email address to send an invite.

 **Note:** You must have configured the SMTP server to send an invite
 through email. Go the **Settings** page to configure the SMTP server
 details. Alternatively, you may select **Get invite link** to generate
 a URL that can be sent through any messaging platform.

2.  Copy and paste the invite link in a browser to start the new user
    registration.

**Note**: This invite link expires within 24 hours.

3.  Data Security Broker Manager displays a confirmation message, that
    an invitation has been sent successfully. In the **Users**
    dashboard, the user details is displayed with the user's email.

## Creating a new user profile in Data Security Broker Manager:
{: #sb_users_profile}

1.  Click the invite link. The Data Security Broker Manager opens a user
    creation console.

2.  Enter the details for the user profile namely, **First name**,
    **Last name**, and provide a **password** and re-enter the password
    in the **Confirm password** field to complete the user registration.

3.  Upon completion, Data Security Broker Manager redirects you to a
    sign-in page.

4.  Log into the Data Security Broker Manager with your credentials.

5.  Navigate to the **User Profile** section in the left navigation menu
    to see the list of user profiles created in the Data Security Broker
    Manager.

Note: Need to insert screenshots wherever applicable.
