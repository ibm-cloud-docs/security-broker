---
copyright:
  years: 2022, 2023
lastupdated: "2023-02-13"

keywords: database, admin, priveleges, users, features, operations

subcollection: security-broker
---

{{site.data.keyword.attribute-definition-list}}

# About Data Masking
{: #sb_masking}

## Overview
{: #sb_mask_overview}

{{site.data.keyword.security_broker_short}} Shield can mask the encrypted data and return the data
in a user-friendly format without decryption or with partial decryption.

Data Masking converts data values into a predefined format that is typically irreversible. A Masking Mode defines the format used to mask selected data. You can create new Masking Modes and use them in a policy
or map them to a column.

## Creating a new masking mode
{: #sb_masking_newmode}

This section demonstrates how to create a new masking mode that is added to the Data Protection Library. 

To create a masking mode, do the following

1. Go to the Data Protection Library and in the header, click the Plus (**+**) sign to begin creating a new mode.

2. Select **Masking Mode** from the drop-down list. The Masking Mode Builder dialog appears.

3. Enter a unique **Mask Mode Name** (30 characters or less) and optionally, a **Description** of up to 100 characters.

4. Select one of the following options from the Mask Mode drop-down menu: FIXED, PATTERN, NUMERIC, CHARACTER.

5. In the **Mask Format** field, enter the string to be used to mask the data. 

6. Click **Save**. The new masking mode appears in the Data Protection Library, as well as a selection in the **Encryption Mode** drop-down.

   The compatible data types are automatically associated with the mode when you click Save. In this way, only the modes that are compatible with a column's data type are shown. 
   {: note}

## Viewing and editing a masking mode
{: #sb_masking_edit_modes}

This section demonstrates how to view and edit Masking Modes. However, editing is limited to modifying the name and description of the selected mode. 

To view the details of a masking mode, do the following

1. Go to the Data Protection Library and click the carrot icon (**>**) next to **Masking Modes **to view the list of modes.

2.  Select a mode from the list. The details for the mode appear in the window on the right.

To edit a masking mode, do the following

a. Go to the Data Protection Library and click the carrot icon (**>**) next to **Masking Modes** to view the list of modes. The details for the mode appear in the window on the right.

b. Click the **Pencil** icon in the upper right corner to edit the mode.

c. Modify the **Mask Mode Name**.

d. Modify the **Description** for the mode.

5.  Click **Save**.

Data Masking in the {{site.data.keyword.security_broker_short}} Manager requires you to configure RBAC policy.


