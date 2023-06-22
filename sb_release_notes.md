---
copyright:
  years: 2022, 2023
lastupdated: "2023-06-22"

keywords: support, troubleshooting, data protection, data threats

subcollection: security-broker

content-type: release-note
---

{{site.data.keyword.attribute-definition-list}}

# Release notes
{: #sb_release_notes}

Use this release notes to learn about the latest changes to the {{site.data.keyword.security_broker_full_notm}} documentation.
{: shortdesc}

## February 2023
{: #sb_date}

Review the release notes for February 2023.
{: shortdesc}

### 13 February 2023
{: #sb-feb1323}
{: release-note}

### Introducing {{site.data.keyword.security_broker_full_notm}} Beta version
{: #sb_release_version1}

{{site.data.keyword.security_broker_full_notm}} is a complete data protection solution that secures sensitive data in enterprise databases by integrating with key management and databases to provide application-level encryption.

Following features are supported in the Beta version:

- Data Encryption and Decryption
- Data Masking

## July 2023
{: #sb_date_ga}

Review the release notes for July 2023.
{: shortdesc}

### 31 July 2023
{: #sb-july3123}
{: release-note}

### Introducing {{site.data.keyword.security_broker_full_notm}} GA version
{: #sb_release_version2}

{{site.data.keyword.security_broker_full_notm}} is now generally available. For more information, see [IBM Cloud Data Security Broker](https://www.ibm.com/cloud/data-security-broker).

## Security Enhancements:
{: #release-note-security-enhancements}

- Fixes to some of the Common Vulnerabilities and Exposures (CVEs) is provided in this version.
- Added support for second-level domain name configuration for {{site.data.keyword.security_broker_short}} Manager user accounts.
- Fix to the issue, where {{site.data.keyword.security_broker_short}} users with an email on a sub-domain of the primary domain name could not enroll has been provided in this version.
- Fix to the issue where repeated login attempts with an invalid OAuth token does not lock the {{site.data.keyword.security_broker_short}} Manager is addressed. In the new version, after five attempts, the {{site.data.keyword.security_broker_short}} manager gets locked for 30 minutes.
- Fix to the issue where invalid connection parameters (API Key and Instance ID) could be passed successfully for an IBM Key Protect instance and for an IBM Cloud Hyper Protect Crypto Services (HPCS) enrollment is provided.

Also, pricing plans have been added to the {{site.data.keyword.security_broker_short}} in this version. For more information, see [Pricing plans for {{site.data.keyword.security_broker_short}}](/docs/security-broker?topic=security-broker-sb_pricing).

