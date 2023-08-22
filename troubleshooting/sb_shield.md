---
copyright:
  years: 2023
lastupdated: "2023-08-22"

keywords: users, admin, priveleges, profiles,

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}
{:troubleshoot: data-hd-content-type='troubleshoot'}


# How to resolve issues that occur during Shield enrollment?
{: #sb_shield}
{: troubleshoot}
{: support}

You face issues during {{site.data.keyword.security_broker_short}} Shield enrollment.
{: shortdesc}

Error messages or warnings displayed during Shield enrollment.
{: tsSymptoms}

If you get error messages or warnings during the Shield enrollment, check for the below scenarios:
1. Hostname or IP address is not submitted: Copy and paste the Shield host endpoint precisely in the appropriate field, with no extra characters or spaces.

2. Shield host is already in use by {{site.data.keyword.security_broker_short}}: Multiple Shields may be hosted on the same endpoint, but only if the port number is unique. If the same port number is reused, the connection fails.

3. Public IPv4 address is configured: If all {{site.data.keyword.security_broker_short}} resources are running in the same environment, then it is recommended to use the private IP address. Alternatively, submit the DNS endpoint for the instance.

4. Insufficient permissions to write to the temporary directory: The Host User must have write permissions for a temporary directory on the Shield host. The default directory is **/tmp**. If the Host User does not have permissions for **/tmp**, submit an alternative temporary path in the appropriate field.
{: tsResolve}





