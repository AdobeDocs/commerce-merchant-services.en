---
title: Guide Overview
description: Learn how to integrate Adobe Commerce data with Adobe Experience Platform using the Experience Platform connector.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
---
# Experience Platform connector overview

The Experience Platform connector extension allows Adobe Commerce merchants to send data to the Adobe Experience Platform edge so other Adobe Experience Cloud products, such as Adobe Analytics and Adobe Target, can use that Commerce data. By connecting your Commerce data to other products in the Adobe Experience Cloud, you can perform tasks, such as analyze user behavior on your site, perform AB testing, and create personalized campaigns.

[Storefront events](events.md) capture shopper interactions, such as `View Page`, `View Product`, `Add to Cart`, and so on. Captured data does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html).

The Experience Platform connector appears in the Commerce Admin under **System** > Services > **Experience Platform Connector**. 

![Experience Platform connector extension Admin view](assets/epc-adminui.png)

## Prerequisites {#prereqs}

In order to use the Experience Platform connector, you must have the following:

- Adobe Commerce 2.4.3 or newer
- Adobe ID and Organization ID
- Entitlements to other Adobe DX products

## Onboarding steps

1. [Install](install.md) the Experience Platform connector extension.
1. [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account and [view](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) your organization ID. The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) `@AdobeOrg`.
1. [Connect](connect-data.md) your Adobe Commerce instance to the Adobe Experience Platform.
1. [Create or update](update-xdm.md) your XDM schema with Commerce-specific field groups.
1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) and select the XDM schema that contains the Commerce-specific field groups.
1. (Optional) [Upload shopper profiles](profile.md) to Adobe Experience Platform so storefront data can be attributed to specific shoppers to enhance their shopping experience.

## Audience

This guide is designed for the Adobe Commerce merchant who want to connect their Adobe Commerce storefront data to other Adobe DX products.

### PWA Studio support

See the [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentation for information about how to use the Experience Platform connector in a PWA Studio storefront.

### AEM support {#aem-support}

See the [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentation to learn how to send storefront event data from an AEM-rendered product page to the Experience Platform using the CIF - Experience Platform Connector.

If you need information or have questions that are not covered in this guide, use the following resources:

- [Help center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Support tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}---Submit a ticket to receive additional help.
