---
title: Collect Data
description: Learn how events collect data for product recommendations.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
---
# Collect Data

When you install and configure SaaS-based Adobe Commerce features such as [Product Recommendations](install-configure.md) or [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), the modules deploy behavioral data collection to your storefront. This mechanism collects anonymized behavioral data from your shoppers and powers product recommendations. For example, the `view` event is used to compute the `Viewed this, viewed that` recommendation type, and the `place-order` event is used to compute the `Bought this, bought that` recommendation type.

>[!NOTE]
>
>Data collection for the purposes of Product recommendations does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html).

The following events are not specific to Product Recommendations, but are required to return results:

- `view`
- `add-to-cart`
- `place-order`

The [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lists all the events deployed to your storefront. From that list, however, there is a subset of events specific to Product Recommendations. These events collect data when shoppers interact with recommendation units on the storefront and power the metrics used to help you analyze how well your recommendations are performing.

| Event | Description | [Used for metrics?](workspace.md) |
| --- | --- | --- |
|`impression-render` | The recommendation unit is rendered on the page. | Yes|
|`rec-add-to-cart-click` | The customer clicks the **Add to cart** button for an item in the recommendation unit. | Yes, when an **Add to cart** button is present in the recommendations template.|
|`rec-click` | The customer clicks a product in the recommendation unit. | Yes|
|`view` | The recommendation unit becomes viewable on the page, such as by scrolling into view. | Yes|

If your storefront is implemented with PWA Studio, refer to the [PWA documentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). If you use a custom frontend technology such as React or Vue JS, refer to the user guide to learn how to integrate Product Recommendations in a [headless](headless.md) environment.

## Caveats

Ad blockers and privacy settings can prevent the `magento/product-recommendations` module from capturing events and might cause the engagement and revenue [metrics](workspace.md) to be underreported.

Eventing does not capture every transaction happening on the merchant's site. Eventing is meant to give the merchant a general idea of events that are happening on the site.

Headless implementations must implement eventing to power the Product Recommendations dashboard.

>[!NOTE]
>
>If [Cookie Restriction Mode](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) is enabled, Adobe Commerce does not collect behavioral data until the shopper consents to using cookies. If Cookie Restriction Mode is disabled, Adobe Commerce collects behavioral data by default.
