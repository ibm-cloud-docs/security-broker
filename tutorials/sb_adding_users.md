---
copyright:
  years: 2022, 2022
lastupdated: "2022-10-11"

keywords: users, admin, priveleges, profiles, {{site.data.keyword.security_broker_short}} Manager, SMTP

subcollection: security-broker
---

# Adding users in {{site.data.keyword.security_broker_short}} Manager
{: #sb_adding_users}

## Overview
{: #sb_users_overview}

{{site.data.keyword.security_broker_short}} Manager supports multiple users who can access the
Manager console. All users on {{site.data.keyword.security_broker_short}} Manager automatically
have administrative privileges, so that they can enroll databases and
applications, modify them, and deploy policies. However, only a user
with Super Admin privileges can add, invite, and delete new users. A
{{site.data.keyword.security_broker_short}} Manager is limited to have only one Super Admin.

## Adding a user to the {{site.data.keyword.security_broker_short}} Manager:
{: #sb_users_DSB}

Complete the following steps to add a new user to the Data Security
Broker Manager:

1.  As a Super Admin, navigate to the **Users** tab in the left
    navigation menu. Click **Add Users +** in the top right corner. Enter an
    email address to send an invite.

    ![Users](../images/add_user.svg){: caption="Figure 1. Users" caption-side="bottom"}

 **Note:** You must have configured the SMTP server to send an invite
 through email. Go the **Settings** page to configure the SMTP server
 details. Alternatively, you may select **Get invite link** to generate
 a URL that can be sent through any messaging platform.

2.  Copy and paste the invite link in a browser to start the new user
    registration.

**Note**: This invite link expires within 24 hours.

3.  {{site.data.keyword.security_broker_short}} Manager displays a confirmation message, that
    an invitation has been sent successfully. In the **Users**
    dashboard, the user details is displayed with the user's email.

## Creating a new user profile in {{site.data.keyword.security_broker_short}} Manager:
{: #sb_users_profile}

1.  Click the invite link. The {{site.data.keyword.security_broker_short}} Manager opens a user
    creation console.

2.  Enter the details for the user profile namely, **First name**,
    **Last name**, and provide a **password** and re-enter the password
    in the **Confirm password** field to complete the user registration.

3.  Upon completion, {{site.data.keyword.security_broker_short}} Manager redirects you to a
    sign-in page.

4.  Log into the {{site.data.keyword.security_broker_short}} Manager with your credentials.

5.  Navigate to the **Profile** section in the left navigation menu
    to see the list of user profiles created in the {{site.data.keyword.security_broker_short}}
    Manager.

Note: Need to insert screenshots wherever applicable.
