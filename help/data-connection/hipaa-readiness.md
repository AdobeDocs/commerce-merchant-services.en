---
title: 'HIPAA Readiness for [!DNL Data Connection]'
description: Learn how you can use the [!DNL Data Connection] extension to share [!DNL Commerce] data with the Experience Platform and maintain HIPAA compliance.
role: Admin, Leader
feature: Security, Compliance
---
# HIPAA Readiness for Data Connection

The [!DNL Data Connection] extension allows you to share [!DNL Commerce] back office event data with the Experience Platform and maintain HIPAA compliance.

>[!IMPORTANT]
>
>Storefront event data is not HIPAA compliant. It is the merchant's responibility to not send storefront event data to Experience Platform.

In this article, you learn:

- How to ensure data sent to the Experience Platform is HIPAA-compliant
- What encryption methods exist in [!DNL Commerce]
- How [!DNL Commerce] handles privacy requests

## Installation

Merchants that have purchased the health care add-on for Adobe [!DNL Commerce] need to install the [HIPAA-Ready extension](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service#installation). Merchants also need to make sure they are using Data Connection version `3.2.1` (???? not sure what EPC version is compatible) or later.

## How to ensure data sent to the Experience Platform is HIPAA compliant

All back office event data that the [!DNL Data Connection] extension sends to the Experience Platform is considered sensitive. To ensure that back office event data is HIPAA-compliant, merchants need to apply a PHI/sensitive label in the schema or dataset in Experience Platform.

Learn how to [apply sensitive labels](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) to your data in Experience Platform.

When that data is labeled as sensitive, that data cannot be sent to Adobe [!DNL Target] or Adobe [!DNL Analytics] (these applications are disabled). Additionally, you cannot use this data in segments or destinations.

## What encryption methods exist in Commerce

DINT-1569
[Doc] Commerce Encryption Methods
 (just an fyi...user don't take any action...it's how it's encrypted in aep...higher standard of encryption)
Document how encryption at rest and encryption in transit is handled in Commerce.
For customers with other Adobe products, the encryption methods may not be the same - Explain the difference and how customers can handle it.
For example, AEP has implemented customer managed keys. For customers sending data from Commerce to AEP, customers revoking access in AEP will have to turn off the integration in Commerce.
AEP docs:
(https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption).
Commerce encryption:
https://wiki.corp.adobe.com/display/MC/Data+Encryption+in+Adobe+Commerce
DINT-1442

## How Commerce handles privacy requests

Learn how [!DNL Commerce] [handles privacy requests](handle-privacy-request.md).
