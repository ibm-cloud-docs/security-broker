---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-29"

keywords: logging, debugging, platform, dashboard, observability

subcollection: security-broker
---

# Log into {{site.data.keyword.security_broker_short}} Manager
{: #sb_login}

Once you have configured the {{site.data.keyword.security_broker_short}} Manager, the next step
is log into the {{site.data.keyword.security_broker_short}} Manager to create keystore, connect
to a database, enroll an application, and perform encryption.

Complete the following steps to log into the {{site.data.keyword.security_broker_short}} Manager:

1.  Generate ab IBM OAuth token. To obtain the OAuth token, log into your IBM cloud account
    from the CLI and run the following command:

    ```sh
    ibmcloud iam oauth-tokens
    ```
    {: codeblock}

2.  Copy the OAuth token without any space or additional characters and paste it in the **Enter token** text box as shown below and click **Sign In** to log into the {{site.data.keyword.security_broker_short}} Manager:

    ![Log into {{site.data.keyword.security_broker_short}} Manager](../images/sb_login.svg){: caption="Figure 1. Log into {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}
    
