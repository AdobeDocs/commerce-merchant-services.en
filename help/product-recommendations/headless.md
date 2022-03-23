---
title: Headless
description: Learn how to integrate [!DNL Product Recommendations] in a headless storefront.
---
# Headless

You can integrate [!DNL Product Recommendations] in a headless storefront using either [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) or a custom frontend technology, such as React or Vue JS.

[!DNL Product Recommendations] require [behavioral and catalog data](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) to operate. The catalog data sync process remains unchanged in a headless implementation, but changes are needed for behavioral data collection.

To integrate [!DNL Product Recommendations] in a headless storefront, you must:

1. Send behavioral data to Adobe Sensei to analyze and compute Product Recommendation results. You can also send additional data to enable product recommendation [metrics reporting](workspace.md).

1. Fetch product recommendation results and render those results on the page.

You can perform both of these actions using the available SDKs as described in the following workflow.

1. [Install](install-configure.md) the [!DNL Product Recommendations] module.

1. Install and use the [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) to fire the [behavioral events](https://devdocs.magento.com/recommendations/events.html).

    The minimum required events to return [!DNL Product Recommendations] results:

    | Event | Category |
    |--- | ---|
    |`view` | product|
    |`add-to-cart` | product|
    |`place-order` | checkout|

    To enable [metrics reporting](workspace.md), the following additional events are required:

    |Event | Category|
    |--- | ---|
    |`impression-render` | recommendation-unit|
    |`view` | recommendation-unit|
    |`rec-click` | recommendation-unit|
    |`rec-add-to-cart-click` | recommendation-unit (if an add to cart button is present in the recommendations template)|

1. When the events are fired, use the [Storefront Events Collector](https://devdocs.magento.com/shared-services/storefront-event-collector.html) to handle the events and send them to Adobe Sensei.

1. After the behavioral data is collected, you can [create](create.md) [!DNL Product Recommendations] in the Admin.

1. Use the [Recommendations SDK](https://devdocs.magento.com/recommendations/recs-api.html) to fetch the recommendation units on the storefront. The SDK returns necessary product data to render recommendation units on a page.
