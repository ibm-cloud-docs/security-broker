---
copyright:
  years: 2022, 2023
lastupdated: "2023-08-22"

keywords: about the service, deploy policy, deployment plans, encryption technology, encryption modes, data protection modes

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

## Encryption Models supported by Data Security Broker:
{: #sb-encryption-models}

{{site.data.keyword.security_broker_short}} supports data encryption services that can be configured
in four main modes.

### Data Encryption: 
{: #sb-standard-encrypt}

{{site.data.keyword.security_broker_short}} functions as an application-level encryption (ALE) software in this mode for encrypting data on a field-level basis. This is performed using {{site.data.keyword.security_broker_short}} Manager to enumerate the data schema and enable an encryption key mapping.

### Data Tokenization:
{: #sb-data-tokenization}

{{site.data.keyword.security_broker_short}} supports length preserving and data type preserving tokenization method to anonymize data at the field level databases or in semi-structured data files.

### Record Level Encryption:
{: #sb-RLE}

{{site.data.keyword.security_broker_short}} can be configured for record level encryption to support multiple keys within a single column that are mapped to respective data owners or entities. This
encryption mode can be used effectively in multi-tenant or shared data environments where segmenting of the data can be challenging. In this mode, data shredding can be enabled by deleting public keys and private keys for a respective entity.

### Data Masking: 
{: #sb-data-masking}

{{site.data.keyword.security_broker_short}} can enable simplified data masking to prevent decryption of data and sensitive file information based on configuration or deleted keys. This mode can minimize data
exposure in public cloud environment and provides a better control of data exfiltration to external parties.

