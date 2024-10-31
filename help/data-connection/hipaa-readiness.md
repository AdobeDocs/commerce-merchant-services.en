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
>Storefront event data is not HIPAA compliant. It is the merchant's responibility to [not send storefront event data](connect-data.md#data-collection) to Experience Platform.

In this article, you learn:

- How to ensure data sent to the Experience Platform is HIPAA-compliant
- What encryption methods exist in [!DNL Commerce]
- How [!DNL Commerce] handles privacy requests

## Installation

Merchants that have purchased the health care add-on for Adobe [!DNL Commerce] need to install the [HIPAA-Ready extension](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service#installation). Merchants who want to send back office event data to Experience Platform need to make sure they are using the [latest version](release-notes.md) of the [!DNL Data Connection] extension, which is compatible with the HIPAA-Ready extension.

## How to ensure data sent to the Experience Platform is HIPAA-compliant

All back office event data that the [!DNL Data Connection] extension sends to the Experience Platform is considered sensitive. However, it is the responsibility of the merchant to apply data usage labels to their [!DNL Commerce] schema in Experience Platform to explictly identify particular data as sensitive. When you apply data usage labels directly to a schema, those labels are propagated to all existing and future datasets that are based on that schema.

For an overview of data usage labels and their role within the Data Governance framework, see [data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) in the Experience Platform documentation.

### Apply data usage labels to Commerce fields

Follow the steps in the [manage data usage labels for a schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/labels) tutorial to learn how to apply labels to your [!DNL Commerce] schema.

See the [glossary of sensitive labels](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/reference#sensitive) to learn about the available labels you can apply to the fields in your [!DNL Commerce] schema. For example, the label `RHD` identifies Protected Health Information (PHI) or information about a patient that you are contractually permitted by Adobe to upload.

When your [!DNL Commerce] data is labeled as sensitive, you can enforce those policies to prevent data operations that constitute policy violations. Learn more about [policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) in Experience Platform.

## How Commerce handles data encryption

Adobe Commerce uses block-level encryption. For storage, Commerce uses Amazon Elastic Block Store (EBS). All EBS volumes are encrypted using the AES-256 algorithm, which means that the data is encrypted at rest. Commerce data in transit is conducted over secure, encrypted connections using HTTPS [TLS v1.2](https://datatracker.ietf.org/doc/html/rfc5246).

>[!IMPORTANT]
>
>Commerce does not support column- or row-level encryption or encryption when the data is not at rest or not in transit between servers.

### Data encryption in Experience Platform

When merchants send their data to the Experience Platform, that data is sent using HTTPS TLS v1.2. Learn more about how [Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption) encrypts data.

## How Commerce handles privacy requests

Learn how [!DNL Commerce] [handles privacy requests](handle-privacy-request.md).
