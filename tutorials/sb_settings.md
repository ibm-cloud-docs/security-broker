---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: domain name, host name, https certificate, logger, smtp, settings

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# Settings
{: #sb_settings}

## Overview
{: #sb_settings_overview}

You can use the Settings page to change the basic system settings in the {{site.data.keyword.security_broker_short}} Manager.

1. Log into the {{site.data.keyword.security_broker_short}} Manager.

2. Navigate to the **Settings** icon in the left navigation

3. Click the **Edit** icon to change the system settings. Modify the **Organization name**, and **domain settings**, and click **Save**.

## HTTPS Certificate
{: #sb_https}

HTTPs Certificate allows you to enable SSL for the {{site.data.keyword.security_broker_short}} Manager console. This ensures that you have secure access to the {{site.data.keyword.security_broker_short}} Manager web interface.

When you try to log into the {{site.data.keyword.security_broker_short}} Manager after the
set up, you get a warning: **Untrusted certificate browser warning**.

The warning appears when you have not uploaded an HTTPS certificate. HTTPS certificate is a digital certificate that authenticates a website's identity and enables an encrypted connection.
{: note}

Upload an HTTPS certificate by following the instructions in [Adding HTTPS certificate](/docs/security-broker?topic=security-broker-sb_add_https) section.



## Logger
{: #sb_logger}

Complete the following steps to configure the Logger settings for the {{site.data.keyword.security_broker_short}} Manager:

1. In the **Settings** page, click **Logger +** to configure a new logger.
   
2. Specify a name for the logger according to Java logger naming convention. A dot is used to separate    names, that enforces a hierarchy.
3. Select a Log Level from the dropdown. These levels define the severity and granularity of the events which is captured by this logger. The options include:
    a. TRACE (Fine-tuned debugging messages)
    b. DEBUG (General debugging messages)
    c. INFO (Informational events)
    d. WARN (Events that might lead to an error)
    e. ERROR (Error messages)
    
4. Click Save to complete the **Logger** configuraion.



