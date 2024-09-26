---
title: Collect Data
description: Learn how events collect data for product recommendations.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
---
# Collect Data

When you install and configure SaaS-based Adobe Commerce features such as [Product Recommendations](install-configure.md) or [Live Search](../live-search/install.md), the modules deploy behavioral data collection to your storefront. This mechanism collects anonymized behavioral data from your shoppers and powers product recommendations. For example, the `view` event is used to compute the `Viewed this, viewed that` recommendation type, and the `place-order` event is used to compute the `Bought this, bought that` recommendation type.

>[!NOTE]
>
>Data collection for the purposes of Product recommendations does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. Learn [more](https://www.adobe.com/privacy/experience-cloud.html).

## Data types and events

There are two types of data used in Product Recommendations:

- **Behavioral** - Data from a shopper's engagement on your site, such as product views, items added to a cart, and purchases.
- **Catalog** - Product metadata, such as name, price, availability, and so on.

When you install the `magento/product-recommendations` module, Adobe Sensei aggregates the behavioral and catalog data, creating Product Recommendations for each recommendation type. The Product Recommendations service then deploys those recommendations to your storefront.

Some recommendation types use behavioral data from your shoppers to train machine learning models to build personalized recommendations. Other recommendation types use catalog data only and do not use any behavioral data. If you want to quickly start using Product Recommendations on your site, you can use the following, catalog-only recommendation types:

- `More like this`
- `Visual similarity`

### Cold start

So when can you start using recommendation types that use behavioral data? It depends. This is referred to as the _Cold Start_ problem.

The _Cold Start_ problem is a measure of how much time that a model needs to train before it can be considered high quality. In product recommendations, it translates to waiting for Adobe Sensei to train its machine learning models before deploying recommendation units on your site. The more data that these models have, the more accurate and useful the recommendations are. Collecting this data takes time and varies based on traffic volume. Because this data can be collected only on a production site, it is in your best interest to deploy data collection there as early as possible. You can do this by [installing and configuring](install-configure.md) the `magento/production-recommendations` module.

>[!INFO]
>
>A recommendation unit is a widget that contains the recommended product _items_.

The following table provides some general guidance for the amount of time that it takes to collect enough data for each recommendation type:

| Recommendation type | Training Time | Notes |
|---|---|---|
|Popularity-based (`Most viewed`, `Most purchased`, `Most added to cart`) | Varies | Depends on volume of events - views are most common, and therefore learns faster; then adds to cart, then purchases|
|`Viewed this, viewed that` | Requires more training |Product views are decently high in volume|
|`Viewed this, bought that`, `Bought this, bought that`| Requires the most training |Purchase events are the most rare events on commerce site, especially compared to product views|
|`Trending` | Requires three days of data to establish a popularity baseline| Trending is a measure of recent momentum in a product's popularity compared with its own popularity baseline. A product's trending score is computed using a foreground set (recent popularity over 24 hours) and a background set (popularity baseline over 72 hours). If an item has become much more popular within the last 24 hours as compared with its baseline popularity, then it receives a high trending score. Every product has this score, and the highest ones at any time comprise the set of top trending products. |

Other variables that can impact the time needed to train:

- Higher traffic volume contributes to faster learning
- Some recommendation types train faster than others
- Adobe Commerce recomputes behavioral data every four hours. Recommendations become more accurate the longer they are used on your site.

To help you visualize the training progress of each recommendation type, the [create recommendation](create.md#readiness-indicators) page displays readiness indicators.

While data is collected on production and machine learning models are trained, you can implement the [remaining tasks](implementation-workflow.md) necessary to deploy recommendations to your storefront. By the time you have finished testing and configuring recommendations, the machine learning models have collected and computed enough data to build relevant recommendations thus allowing you to deploy the recommendations to your storefront.

If there is insufficient traffic (views, products bought, trending) for the majority of SKUs, there may not be enough data to complete the learning process. This may cause the readiness indicator in the Admin to look as if it were stuck. The readiness indicators are meant to provide merchants with another data point in choosing what recommendations type is better for their store. The numbers are a guide and may never reach 100%. [Learn more](create.md#readiness-indicators) about readiness indicators.

### Backup recommendations {#backuprecs}

If there is not sufficient input data to provide all requested recommendation items in a unit, Adobe Commerce provides backup recommendations to populate recommendation units. For example, if you deploy the `Recommended for you` recommendation type to your homepage, a first-time shopper on your site has not generated enough behavioral data to accurately recommended personalized products. In this case, Adobe Commerce surfaces items based on the `Most viewed` recommendation type to this shopper.

The following recommendation types fallback to `Most viewed` recommendation type if there is not sufficient input data collected:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### Required events

The [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lists all the events deployed to your storefront. From that list, however, there is a subset of events specific to Product Recommendations. These events collect data when shoppers interact with recommendation units on the storefront and power the metrics used to help you analyze how well your recommendations are performing.

>[!NOTE]
>
>Product Recommendation metrics are optiimized for Luma storefronts. If your storefront is non-Luma based, how the metrics track data depends on how you implement the event collection.

| Event | Description |Used for metrics? |
| --- | --- | --- |
|`impression-render` | Sent when the recommendation unit is rendered on the page. If a page has two recommendation units (bought-bought, view-view) then two `impression-render` events are sent. This event is used to track the metric for impressions. | Yes|
|`rec-add-to-cart-click` | The shopper clicks the **Add to cart** button for an item in the recommendation unit. | Yes, when an **Add to cart** button is present in the recommendations template.|
|`rec-click` | The shopper clicks a product in the recommendation unit. | Yes|
|`view` | Sent when the recommendation unit becomes at least 50 percent viewable, such as by scrolling down the page. For example, if a recommendation unit has two lines, a `view` event is sent when one line plus one pixel of the second line becomes visible to the shopper. If the shopper scrolls the page up and down several times, the `view` event is sent as many times as the shopper sees the whole recommendation unit again on the page.| Yes|

The following events are required to properly populate the dashboard.

| Dashboard column | Events    | Join field  |
| ---------------- | --------- | ----------- |
| Impressions      |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId  |
| Views            |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId  |
| Clicks           |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | unitId  |
| Revenue          |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku, parentSku |
| LT Revenue       |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku, parentSku |
| CTR              |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | unitId, sku, parentSku |
| vCTR             |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku, parentSku |

The following events are not specific to Product Recommendations, but are the minimum required set of events that enables Adobe Sensei to interpret shopper data correctly:

- `view`
- `add-to-cart`
- `place-order`

If your storefront is implemented with PWA Studio, refer to the [PWA documentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). If you use a custom frontend technology such as React or Vue JS, refer to the user guide to learn how to integrate [Product Recommendations in a headless](headless.md) environment.

### Caveats

- Ad blockers and privacy settings can prevent the `magento/product-recommendations` module from capturing events and might cause the engagement and revenue [metrics](workspace.md) to be underreported.
- Eventing does not capture every transaction happening on the merchant's site. Eventing is meant to give the merchant a general idea of events that are happening on the site. ???(this needs to be clarified, why is eventing not capturing all transactions??? what do we mean with this?)???
- [Headless implementations](headless.md) must implement eventing to power the Product Recommendations dashboard.
- For configurable products, Product Recommendations use the image of the parent product in the recommendation unit. If the configurable product does not have an image specified, the recommendation unit will be empty for that specific product.

>[!NOTE]
>
>If [Cookie Restriction Mode](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) is enabled, Adobe Commerce does not collect behavioral data until the shopper consents to using cookies. If Cookie Restriction Mode is disabled, Adobe Commerce collects behavioral data by default.
