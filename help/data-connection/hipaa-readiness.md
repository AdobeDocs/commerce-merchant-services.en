---
title: HIPAA Readiness for [!DNL Commerce] Services
description: Learn how you can use the [!DNL Data Connection] extension to share [!DNL Commerce] data with Experience Platform and maintain HIPAA compliance.
role: Admin, Leader
feature: Security, Compliance
exl-id: a7344e22-e6af-4e0c-9e56-078a4fce13ef
---
# HIPAA Readiness for [!DNL Commerce] Services

The [!DNL Data Connection] extension allows you to share [!DNL Commerce] back office event data with Experience Platform and maintain HIPAA compliance.

>[!IMPORTANT]
>
>Because storefront events are generated client-side, it is the merchant's responsibility [not to send storefront event data](connect-data.md#data-collection) to Experience Platform.

In this article, you learn:

- What to install
- How to ensure data sent to Experience Platform is HIPAA-ready
- Data encryption in [!DNL Commerce]

## Installation

If you purchased the health care add-on for Adobe [!DNL Commerce], you most likely already installed the [HIPAA-Ready extension](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview#installation). To ensure that your [!DNL Commerce] back office event data is HIPAA-ready, you also need to install the [!DNL Data Connection] extension with the additional **Data Services HIPAA** extension. The **Data Services HIPAA** extension ensures that any back office data you send to Experience Platform is HIPAA-ready. Learn [how to install the extension](install.md#install-the-data-services-hipaa-extension).

>[!IMPORTANT]
>
>When you install the **Data Services HIPAA** extension, storefront event data that is used by Live Search and Product Recommendations is no longer captured. This is because storefront event data is generated client-side. To continue capturing and sending storefront event data, re-enable event collection for these services. See [general configuration](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general.html#data-services) to learn more.

## How to ensure data sent to Experience Platform is HIPAA-ready

All back office event data that the [!DNL Data Connection] extension sends to Experience Platform is considered sensitive within [!DNL Commerce]. However, it is the responsibility of the merchant to apply data usage labels to their [!DNL Commerce] schema in Experience Platform to explicitly identify particular data as sensitive. When you apply data usage labels directly to a schema, those labels are propagated to all existing and future datasets that are based on that schema.

For an overview of data usage labels and their role within the Data Governance framework, see the [data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) in Experience Platform documentation.

### Apply data usage labels to [!DNL Commerce] fields

Follow the steps in the [manage data usage labels for a schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/labels) tutorial to learn how to apply labels to your [!DNL Commerce] schema.

See the [glossary of sensitive labels](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/reference#sensitive) to learn about the available labels you can apply to the fields in your [!DNL Commerce] schema. For example, the label `RHD` identifies Protected Health Information (PHI) or information about a patient that you are contractually permitted by Adobe to upload.

When your [!DNL Commerce] data is labeled as sensitive, you can enforce policies to prevent data operations that constitute policy violations. Learn more about [policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) in Experience Platform.

## Data encryption in Commerce

Adobe [!DNL Commerce] uses block-level encryption. For storage, [!DNL Commerce] uses Amazon Elastic Block Store (EBS). All EBS volumes are encrypted using the AES-256 algorithm, which means that the data is encrypted at rest. [!DNL Commerce] data in transit is conducted over secure, encrypted connections using HTTPS [TLS v1.2](https://datatracker.ietf.org/doc/html/rfc5246).

>[!IMPORTANT]
>
>Commerce does not support column- or row-level encryption or encryption when the data is not at rest or not in transit between servers.

### Data encryption in Experience Platform

When merchants send their data to Experience Platform, that data is sent using HTTPS TLS v1.2. Learn more about how [Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption) encrypts data.

## How [!DNL Commerce] handles privacy requests

Learn how [!DNL Commerce] [handles privacy requests](handle-privacy-request.md).
