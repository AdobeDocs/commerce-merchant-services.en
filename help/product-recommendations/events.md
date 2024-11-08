---
title: Collect Data
description: Learn how events collect data for [!DNL Product Recommendations].
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
---
# Collect Data

When you install and configure SaaS-based Adobe Commerce features such as [[!DNL Product Recommendations]](install-configure.md) or [[!DNL Live Search]](../live-search/install.md), the modules deploy behavioral data collection to your storefront. This mechanism collects anonymized behavioral data from your shoppers and powers [!DNL Product Recommendations]. For example, the `view` event is used to compute the `Viewed this, viewed that` recommendation type, and the `place-order` event is used to compute the `Bought this, bought that` recommendation type.

>[!NOTE]
>
>Data collection for the purposes of [!DNL Product Recommendations] does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. Learn [more](https://www.adobe.com/privacy/experience-cloud.html).

## Healthcare customers

If you are a healthcare customer and you installed the [Data Services HIPAA extension](../data-connection/hipaa-readiness.md#installation), which is part of the [Data Connection](../data-connection/overview.md) extension, storefront event data that is used by [!DNL Product Recommendations] is no longer captured. This is because storefront event data is generated client-side. If you want to continue to capture and send storefront event data, you can re-enable event collection for [!DNL Product Recommendations]. See [general configuration](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general.html#data-services) to learn more.

## Data types and events

There are two types of data used in Product Recommendations:

- **Behavioral** - Data from a shopper's engagement on your site, such as product views, items added to a cart, and purchases.
- **Catalog** - Product metadata, such as name, price, availability, and so on.

When you install the `magento/product-recommendations` module, Adobe Sensei aggregates the behavioral and catalog data, creating Product Recommendations for each recommendation type. The Product Recommendations service then deploys those recommendations to your storefront in the form of a widget that contains the recommended product _items_.

Some recommendation types use behavioral data from your shoppers to train machine learning models to build personalized recommendations. Other recommendation types use catalog data only and do not use any behavioral data. If you want to quickly start using Product Recommendations on your site, you can use the following, catalog-only recommendation types:

- `More like this`
- `Visual similarity`

### Cold start

When can you start using recommendation types that use behavioral data? It depends. This is referred to as the _Cold Start_ problem.

The _Cold Start_ problem refers to the time it takes for a model to train and become effective. For product recommendations, this means waiting for Adobe Sensei to gather enough data to train its machine learning models before deploying recommendation units on your site. The more data the models have, the more accurate and useful the recommendations are. Since data collection happens on a live site, it's best to start this process early by installing and setting up the `magento/production-recommendations` module.

The following table provides some general guidance for the amount of time that it takes to collect enough data for each recommendation type:

| Recommendation type | Training Time | Notes |
|---|---|---|
|Popularity-based (`Most viewed`, `Most purchased`, `Most added to cart`) | Varies | Depends on volume of events - views are most common, and therefore learns faster; then adds to cart, then purchases|
|`Viewed this, viewed that` | Requires more training |Product views are decently high in volume|
|`Viewed this, bought that`, `Bought this, bought that`| Requires the most training |Purchase events are the most rare events on a commerce site, especially compared to product views|
|`Trending` | Requires three days of data to establish a popularity baseline| Trending is a measure of recent momentum in a product's popularity compared with its own popularity baseline. A product's trending score is computed using a foreground set (recent popularity over 24 hours) and a background set (popularity baseline over 72 hours). If the popularity of an item increases significantly within a 24 hour period as compared with its baseline popularity, then it receives a high trending score. Every product has this score, and the items with the highes score  at any time comprise the set of top trending products. |

Other variables that can impact the time needed to train:

- Higher traffic volume contributes to faster learning
- Some recommendation types train faster than others
- Adobe Commerce recomputes behavioral data every four hours. Recommendations become more accurate the longer they are used on your site.

To help you visualize the training progress of each recommendation type, the [create recommendation](create.md#readiness-indicators) page displays readiness indicators.

While data is being collected on your live site and the machine learning models are training, you can finish other testing and configuration tasks needed to set up recommendations. By the time you're done with this work, the models will have enough data to create useful recommendations, allowing you to deploy them to your storefront.

If your site doesn't get enough traffic (views, purchases, trends) for most product SKUs, there might not be enough data to complete the learning process. This can make the readiness indicator in the Admin seem stuck. The readiness indicators are meant to provide merchants with another data point in choosing what recommendations type is better for their store. The numbers are a guide and may never reach 100%. [Learn more](create.md#readiness-indicators) about readiness indicators.

### Backup recommendations {#backuprecs}

If the input data is insufficient for providing all requested recommendation items in a unit, Adobe Commerce provides backup recommendations to populate recommendation units. For example, if you deploy the `Recommended for you` recommendation type to your homepage, a first-time shopper on your site has not generated enough behavioral data to accurately recommended personalized products. In this case, Adobe Commerce surfaces items based on the `Most viewed` recommendation type to this shopper.

In the case of insufficient input data collection, the following recommendation types fallback to `Most viewed` recommendation type:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### Events

The [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lists all the events deployed to your storefront. From that list, however, there is a subset of events specific to [!DNL Product Recommendations]. These events collect data when shoppers interact with recommendation units on the storefront and power the metrics used to help you analyze how well your recommendations are performing.

| Event | Description |
| --- | --- |
|`impression-render` | Sent when the recommendation unit is rendered on the page. If a page has two recommendation units (bought-bought, view-view), then two `impression-render` events are sent. This event is used to track the metric for impressions. |
|`rec-add-to-cart-click` | The shopper clicks the **Add to cart** button for an item in the recommendation unit. |
|`rec-click` | The shopper clicks a product in the recommendation unit. |
|`view` | Sent when the recommendation unit becomes at least 50 percent viewable, such as by scrolling down the page. For example, if a recommendation unit has two lines, a `view` event is sent when one line plus one pixel of the second line becomes visible to the shopper. If the shopper scrolls the page up and down several times, the `view` event is sent as many times as the shopper sees the whole recommendation unit again on the page.|

>[!NOTE]
>
>Product Recommendation metrics are optimized for Luma storefronts. If your storefront is implemented with PWA Studio, refer to the [PWA documentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). If you use a custom frontend technology such as React or Vue JS, learn how to integrate [Product Recommendations in a headless](headless.md) environment.

#### Required dashboard events

The following events are required to populate the [[!DNL Product Recommendations] dashboard](workspace.md)

| Dashboard column | Events    | Join field  |
| ---------------- | --------- | ----------- |
| Impressions      |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId`  |
| Views            |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId`  |
| Clicks           |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | `unitId`  |
| Revenue          |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| LT Revenue       |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR              |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | `unitId`, `sku`, `parentSku` |
| vCTR             |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

The following events are not specific to Product Recommendations, but are required for Adobe Sensei to interpret shopper data correctly:

- `view`
- `add-to-cart`
- `place-order`

#### Recommendation Type

This table describes the events used by each recommendation type.

| Recommendation Type | Events | Page |
| --- | --- | --- |
| Most Viewed | `page-view`<br>`product-view` | Product detail page |
| Most Purchased | `page-view`<br>`complete-checkout` | Cart/Checkout |
| Most added to cart | `page-view`<br>`add-to-cart` | Product detail page<br>Product listing page<br>Cart<br>Wish List |
| Viewed this, viewed that | `page-view`<br>`product-view` | Product detail page |
| Viewed this, bought that | Product Recs | `page-view`<br>`product-view` | Product detail page<br>Cart/Checkout |
| Bought this, bought that | Product Recs | `page-view`<br>`product-view` | Product detail page |
| Trending | `page-view`<br>`product-view` | Product detail page |
| Conversion: View to purchase | Product Recs | `page-view`<br>`product-view` | Product detail page |
| Conversion: View to purchase | Product Recs | `page-view`<br>`complete-checkout` | Cart/Checkout |
| Conversion: View to cart | Product Recs | `page-view`<br>`product-view` | Product detail page |
| Conversion: View to cart | Product Recs | `page-view`<br>`add-to-cart` | Product detail page<br>Product listing page<br>Cart<br>Wishlist |

#### Caveats

- Ad blockers and privacy settings can prevent events from being captured and might cause the engagement and revenue [metrics](workspace.md#column-descriptions) to be under-reported. Additionally, some events might not be sent due to shoppers leaving the page or network issues.
- [Headless implementations](headless.md) must implement eventing to power the Product Recommendations dashboard.
- For configurable products, Product Recommendations use the image of the parent product in the recommendation unit. If the configurable product does not have an image specified, the recommendation unit will be empty for that specific product.

>[!NOTE]
>
>If [Cookie Restriction Mode](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) is enabled, Adobe Commerce does not collect behavioral data until the shopper consents to using cookies. If Cookie Restriction Mode is disabled, Adobe Commerce collects behavioral data by default.
