---
title: "Onboarding Overview"
description: "[!DNL Live Search] onboarding flow, system requirements, boundaries, and limitations"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
---
# Onboarding Overview

To get started using [!DNL Live Search] for Adobe Commerce, complete the onboarding process to install the extension, configure your API keys, and synchronize your catalog.

## Onboarding flow

![[!DNL Live Search] onboarding diagram](assets/onboarding-flow.svg)

## Requirements {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Supported platforms

* Adobe Commerce on-prem (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpoint

[!DNL Live Search] communicates through the endpoint at `https://catalog-service.adobe.io/graphql`.

## Boundaries and thresholds

Currently, the [!DNL Live Search] search/category API has the following supported limits and static boundaries:

### Indexing

* Indexes up to 300 product attributes per store view.
* Indexes only products from the Adobe Commerce database.
* Products must be in the Default Shared Catalog.
* CMS pages are not indexed.

### Query

* [!DNL Live Search] does not have access to the full taxonomy of the category tree, which makes some layered navigation search scenarios beyond its reach.
* [!DNL Live Search] uses a unique GraphQL endpoint for queries to support features such as dynamic faceting and search-as-you-type. Although similar to the [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/), there are a few differences and some fields may not be fully compatible.

To restrict customer groups using Catalog permissions:

* Products must be assigned to the Root category.
* The "Not Logged in" customer group must be given "Allow" browsing permissions.
* To restrict products to the Not Logged In customer group, go to each category and set permission for each customer group.

### Rules

* Maximum number of rules per store view is 50.
* Maximum number of conditions per rule is 10.
* Maximum number of events per rule is 25.

### Synonyms

* [!DNL Live Search] can manage up to 200 synonyms per store view.

## Price indexer

Live Search customers can use the new [SaaS price indexer](../price-index/index.md), which provides faster price change updates and synchronization time.

### PWA support

[!DNL Live Search] works with PWA Studio but users may see slight differences compared to other Commerce implementations. Basic functionality such as search and product listing page work in Venia but some permutations of Graphql may not work correctly. There may also be performance differences.

* The current PWA implementation of [!DNL Live Search] requires more processing time to return search results than [!DNL Live Search] with the native Commerce storefront.
* [!DNL Live Search] in PWA  does not support [event handling](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Intelligent merchandising will not work because of this.
* Filtering directly on `description`, `name`, `short_description` is not supported by GraphQL when used with [PWA](https://developer.adobe.com/commerce/pwa-studio/), but they are returned with a more general filter.

To use [!DNL Live Search] with PWA Studio, integrators must also:

1. Install [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Set the `environmentId` in the `storeDetails` object.

    ```javascript
    const storeDetails: StoreDetailsProps = {
        environmentId: <Storefront_ID>,
        websiteCode: "base",
        storeCode: "main_website_store",
        storeViewCode: "default",
        searchUnitId: searchUnitId,
        config: {
            minQueryLength: 5,
            pageSize: 8,
            currencySymbol: "$",
            },
        };
    ```

### Not currently supported

* The [Advanced Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
* Multiple inventory locations as used by [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) or other OMS extensions
* Product prices do not include [value added tax](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT).
* [Tier Price](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) is not supported in the Live Search Popover and Product Listing Page Widget.

## Cookies

[!DNL Live Search] collects user interaction data as part of its base functionality and cookies are used to store this data. When collecting any user information, the user must agree to store cookies. [!DNL Live Search] and [!DNL Product Recommendations] share the data stream and therefore the same cookie mechanism. Read more about it in [Handle Cookie Restrictions](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
