---
copyright:
  years: 2022, 2022
lastupdated: "2022-11-17"

keywords: logging, debugging, platform, dashboard, observability

subcollection: security-broker
---

# Log into Data Security Broker Manager
{: #sb_login}

Once you have configured the Data Security Broker Manager, the next step
is log into the Data Security Broker Manager to create keystore, connect
to a database, enroll an application, and perform encryption.

Complete the following steps to log into the Data Security Broker
Manager:

1.  Log into the Data Security Broker Manager with a valid IBM OAuth
    token. To obtain the OAuth token, log into your IBM cloud account
    from the CLI and run the following command:

```sh
ibmcloud iam oauth-tokens
```
{: codeblock}

2.  Copy the OAuth token without any space or additional characters and
    paste it in the **Enter token** text box as shown below:

![Log into {{site.data.keyword.security_broker_short}} Manager](../images/sb_login.svg){: caption="Figure 1. Log into {{site.data.keyword.security_broker_short}} Manager" caption-side="bottom"}
