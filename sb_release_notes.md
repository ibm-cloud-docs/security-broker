---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: support, troubleshooting, data protection, data threats

subcollection: security-broker

content-type: release-note
---

{{site.data.keyword.attribute-definition-list}}

# Release notes for {{site.data.keyword.security_broker_short}}
{: #sb_release_notes}

Use this release notes to learn about the latest changes to the {{site.data.keyword.security_broker_full_notm}} documentation.
{: shortdesc}

## August 2023
{: #sb_aug2023}

### 1 August 2023
{: #sb-aug0123}
{: release-note}

Introducing {{site.data.keyword.security_broker_full_notm}} 1.70.1650 version
:   Fixes to some of the Common Vulnerabilities and Exposures (CVEs) are provided in this version along with the bug fixes.

Security enhancements
:   The following security enhancements were incorporated:
      - Added support for second-level domain name configuration for {{site.data.keyword.security_broker_short}} Manager user accounts. As part of this enhancement, {{site.data.keyword.security_broker_short}} users with an email on a sub-domain of the primary domain name can now enroll successfully.
      - Additional security enhancement has been enforced wherein, if you try to log in with an invalid OAuth token for more than 5 times, the {{site.data.keyword.security_broker_short}} Manager login gets locked and you must attempt to log in again after 30 minutes.



## 13 February 2023
{: #sb-feb1323}
{: release-note}

Introducing {{site.data.keyword.security_broker_full_notm}} **Beta** version (1.70.855)
:   {{site.data.keyword.security_broker_full_notm}} is a complete data protection solution that secures sensitive data in enterprise databases by integrating with key management and databases to provide application-level encryption. The following features are supported in the Beta version:
    - Data encryption and decryption
    - Data masking

