---
title: Guide Overview
description: Learn how to integrate Adobe Commerce data with Adobe Experience Platform using the [!DNL Data Connection] extension.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
---
# [!DNL Data Connection] overview

>[!IMPORTANT]
>
>The Experience Platform connector has been renamed to [!DNL Data Connection].

The [!DNL Data Connection] extension allows Adobe Commerce merchants to send [storefront](events.md#storefront-events) and [back office](events.md#back-office-events) data to the Adobe Experience Platform edge so that other Adobe Experience Cloud products, such as Adobe Analytics and Adobe Journey Optimizer, can use that Commerce data. By connecting your Commerce data to other products in the Adobe Experience Cloud, you can perform tasks such as analyze user behavior on your site, perform AB testing, and create personalized campaigns.

[Storefront events](events.md#storefront-events) capture shopper interactions, such as `View Page`, `View Product`, `Add to Cart`, and [requisition list](events.md#b2b-events) information (for B2B merchants). [Back Office](events.md#back-office-events) events capture information about the status of an order, such as if an order was placed, canceled, refunded, shipped, or completed. Captured data does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html).

The [!DNL Data Connection] extension appears in the Commerce Admin under **System** > Services > **[!DNL Data Connection]**. 

![[!DNL Data Connection] extension Admin view](assets/epc-adminui.png)

## Prerequisites {#prereqs}

To use the [!DNL Data Connection] extension, you must have the following:

- Adobe Commerce 2.4.3 or newer
- Adobe ID and Organization ID
- [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). The ACDL is required to collect storefront event data.
- Entitlements to other Adobe DX products

## Onboarding steps

1. [Install](install.md) the [!DNL Data Connection] extension.
1. [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account and [view to confirm](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) your organization ID. The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) `@AdobeOrg`.
1. [Create or update](update-xdm.md) your XDM schema with Commerce-specific field groups.
1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated. This dataset contains the Commerce data that you send.
1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups.
1. [Connect to Commerce Services](../landing/saas.md).
1. [Connect to Adobe Experience Platform](connect-data.md).

## Audience

This guide is designed for the Adobe Commerce merchant who wants to connect their Adobe Commerce data to other Adobe DX products.

### PWA Studio support

See the [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentation for information about how to use the [!DNL Data Connection] extension in a PWA Studio storefront.

### AEM support {#aem-support}

See the [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentation to learn how to send storefront event data from an AEM-rendered product page to the Experience Platform using the CIF - [!DNL Data Connection] extension.

If you need information or have questions that are not covered in this guide, use the following resources:

- [Help center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Support tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}---Submit a ticket to receive additional help.
