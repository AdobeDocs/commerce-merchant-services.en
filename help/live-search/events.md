---
title: '[!DNL Live Search] Events'
description: Learn how events collect data for [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
---
# [!DNL Live Search] Events

[!DNL Live Search] uses events to power search algorithms such as "Most Viewed", and "Viewed This, Viewed That". While the [Commerce sample Luma theme](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/design/themes/themes#the-default-theme) gets eventing out of the box, headless and other custom implementations have to implement eventing for their own needs.

This table describes the events used by [!DNL Live Search] [ranking strategies](rules-add.md#intelligent-ranking).

| Ranking Strategy | Events | Page |
| --- | --- | --- |
| Most Viewed |  `page-view`<br>`product-view` | Product detail page |
| Most Purchased |  `page-view`<br>`complete-checkout` | Cart/Checkout |
| Most added to cart |  `page-view`<br>`add-to-cart` | Product detail page<br>Product listing page<br>Cart<br>Wish List |
| Viewed this, viewed that |  `page-view`<br>`product-view` | Product detail page |

>[!NOTE]
>
>Data collection for the purposes of [!DNL Live Search] does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html).

## Required dashboard events

Some events are required to populate the [Live Search dashboard](performance.md)

| Dashboard area        | Events      | Join field |
| ------------------- | ------------- | ---------- |
| Unique searches       |`page-view`, `search-request-sent`, `search-response-received` | `searchRequestId`  |
| Zero results searches |`page-view`, `search-request-sent`,  `search-response-received` | `searchRequestId`  |
| Zero results rate     |`page-view`, `search-request-sent`,  `search-response-received` | `searchRequestId`  |
| Popular searches      |`page-view`, `search-request-sent`,  `search-response-received` | `searchRequestId`  |
| Avg. click position   |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`   | `searchRequestId`      |
| Click-through rate    |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`   | `searchRequestId`, `sku`, `parentSku` |
| Conversion rate       |`page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order`| `searchRequestId`, `sku`, `parentSku` |

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

- Ad blockers and privacy settings can prevent events from being captured and might cause the engagement and revenue [metrics](performance.md) to be under-reported. Additionally, some events might not be sent due to shoppers leaving the page or network issues.
- Headless implementations must implement eventing to power intelligent merchandising.

>[!NOTE]
>
>If [Cookie Restriction Mode](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) is enabled, Adobe Commerce does not collect behavioral data until the shopper consents to using cookies. If Cookie Restriction Mode is disabled, Adobe Commerce collects behavioral data by default.
