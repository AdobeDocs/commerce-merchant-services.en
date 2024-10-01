---
title: 'HIPAA Readiness for [!DNL Data Connection]'
description: Learn how you can use the [!DNL Data Connection] extension to share [!DNL Commerce] data with the Experience Platform and maintain HIPAA compliance.
role: Admin, Leader
feature: Security, Compliance
---
# HIPAA Readiness for Data Connection

The [!DNL Data Connection] extension allows you to share Commerce data with the Experience Platform and maintain HIPAA compliance.

In this article, you learn:

- How to install the [!DNL Data Connection] extension with HIPAA support
- How to ensure data sent to the Experience Platform is HIPAA compliant
- What encryption methods exist in Commerce
- How Commerce services handles privacy requests

## Installation

**Prerequisite**

>[!BEGINSHADEBOX]

- Adobe has provisioned your Adobe Commerce account to access the HIPAA Ready extension. [Learn more](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service).
- Access to [repo.magento.com](https://repo.magento.com) to install the extension. For key generation and obtaining the necessary rights, see [Get your authentication keys](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

>[!ENDSHADEBOX]


As of `experience-platform-connector` version 3.2.0-beta4 the hipaa-ready installer specific for data sharing is part of the experience platform connector extension
https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service#installation

## How to ensure data sent to the Experience Platform is HIPAA compliant

DINT-1481
Document: apply sensitive labels to Commerce data in AEP
[Doc] Tag HIPAA sensitive fields in schema
As a Commerce+AEP Healthcare customer, I want to make sure all Commerce fields going to AEP is tagged with the HIPAA sensitive labels so appropriate policies are applied within AEP.
Open questions:
Is there a way to add this label automatically via XDM APIs? ---- Customers can apply labels to fields in the schema. There is no automated way to do this.
Can this be automated for all HIPAA clients as all Commerce customer/order will be considered PHI/sensitive? ---- No, customers will need to apply labels
Does this need any action from the HIPAA customer? ----Yes, same as above.
Data labeling docs:
https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview
Summary from meeting with AEP data collection:
A PHI field is tagged with a PHI/sensitive label in the schema or dataset in AEP. The field being tagged with sensitive label determines all other actions in AEP.
Datastream with PHI field cannot be sent to Target or Analytics. Automatically disabled/not allowed to select these applications.
Field with PHI label cannot be used in segments, destinations etc based on policies defined by customers.
No additional guardrails or actions in data collection or edge network

## What encryption methods exist in Commerce

DINT-1569
[Doc] Commerce Encryption Methods
Document how encryption at rest and encryption in transit is handled in Commerce.
For customers with other Adobe products, the encryption methods may not be the same - Explain the difference and how customers can handle it.
For example, AEP has implemented customer managed keys. For customers sending data from Commerce to AEP, customers revoking access in AEP will have to turn off the integration in Commerce.
AEP docs:
(https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption).
Commerce encryption:
https://wiki.corp.adobe.com/display/MC/Data+Encryption+in+Adobe+Commerce
DINT-1442

## How Commerce services handles privacy requests

DINT-1583
[Doc] Commerce Services handling Privacy Requests
Document how Commerce Services handle privacy requests - Access and Delete
Integration with privacy service for saas https://wiki.corp.adobe.com/display/ACDS/%5BDraft%5D+Privacy+Service+Saas+Integration+-+Architecture
Core handled by customer directly via support requests
Link to privacy service docs where applicable
Make sure privacy service docs are updated to include Commerce
