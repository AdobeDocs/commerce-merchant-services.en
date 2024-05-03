---
title: '[!DNL Live Search] Events'
description: Learn how events collect data for [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
---
# [!DNL Live Search] Events

[!DNL Live Search] uses events to power search algorithms such as "Most Viewed", and "Viewed This, Viewed That". While LUMA users get eventing out of the box, headless and other custom implementations have to implement eventing for their own needs.

Since [!DNL Live Search] and [!DNL Product Recommendations] use the same backend algorithm, some events are shared by both services. Some Product Recommendations events are required to populate the Recommendations Dashboard.

This table describes the events used by [!DNL Live Search] strategies.

| Strategy | Products | Events | Page |
| --- | --- | --- | ---|
| Most Viewed | Live Search<br>Product Recs | page view<br>product view | Product detail page |
| Most Purchased | Live Search<br>Product Recs | page view<br>complete checkout | Cart/Checkout |
| Most added to cart | Live Search<br>Product Recs | page view<br>add to cart | Product detail page<br>Product listing page<br>Cart<br>Wish List |
| Viewed this, viewed that | Live Search<br>Product Recs | page view<br>product view | Product detail page |
| Trending | Live Search<br>Product Recs | page view<br>product view | Product detail page |
| Viewed this, bought that | Product Recs | page view<br>product view | Product detail page<br>Cart/Checkout |
| Bought this, bought that | Product Recs | page view<br>product view | Product detail page |
| Conversion: View to purchase | Product Recs | page view<br>product view | Product detail page |
| Conversion: View to purchase | Product Recs | page view<br>complete checkout | Cart/Checkout |
| Conversion: View to cart | Product Recs | page view<br>product view | Product detail page |
| Conversion: View to cart | Product Recs | page view<br>add to cart | Product detail page<br>Product listing page<br>Cart<br>Wishlist |

>[!NOTE]
>
>Data collection for the purposes of [!DNL Live Search] does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html).

## Required dashboard events

Some events are required to populate the [Live Search dashboard](performance.md)

| Dashboard area        | Events      | Join field |
| ------------------- | ------------- | ---------- |
| Unique searches       |`page-view`, `search-request-sent`,  | searchRequestId  |
| Zero results searches |`page-view`, `search-request-sent`,  | searchRequestId  |
| Zero results rate     |`page-view`, `search-request-sent`,  | searchRequestId  |
| Popular searches      |`page-view`, `search-request-sent`,  | searchRequestId  |
| Avg. click position   |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`   | searchRequestId      |
| Click-through rate    |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`   | searchRequestId, sku |
| Conversion rate       |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order`| searchRequestId, sku |

### Required contexts

All events require the `Page` and `Storefront` contexts. This should happen at the page level/storefront application layer rather than when generating individual events (for example, in a PHP storefront, the PHP application container is responsible for setting them at runtime).

## Usage

Here is a sample implementation of the `search-request-sent` event:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Caveats

Ad blockers and privacy settings can prevent events from being captured and might cause the engagement and revenue [metrics](workspace.md) to be under-reported.

Eventing does not capture every transaction happening on the merchant's site. Eventing is meant to give the merchant a general idea of events that are happening on the site.

Headless implementations must implement eventing to power the [Product Recommendations dashboard](../product-recommendations/events.md).

>[!NOTE]
>
>If [Cookie Restriction Mode](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) is enabled, Adobe Commerce does not collect behavioral data until the shopper consents to using cookies. If Cookie Restriction Mode is disabled, Adobe Commerce collects behavioral data by default.
