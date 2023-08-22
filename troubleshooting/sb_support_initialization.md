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


# What if the HTTPS certificate is not added?
{: #sb_support_initialization}
{: troubleshoot}
{: support}

The HTTPS certificate is not added and thus, initialization and setup process is failing.
{: shortdesc}

You get error messages or warnings during the initialization or the setup of {{site.data.keyword.security_broker_short}} with the following message:
{: tsSymptoms}

> Message: Untrusted certificate browser warning

HTTPS certificate has not been updated. This warning occurs when the {{site.data.keyword.security_broker_short}} Manager's pre-scanned certificate does not match the hostname of the Manager server.
{: tsCauses}

Upload an HTTPS certificate by following the instructions in [Adding HTTPS certificate](/docs/security-broker?topic=security-broker-sb_add_https) section.
{: tsResolve}


