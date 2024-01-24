---
title: "Technical Overview"
description: "[!DNL Live Search] onboarding flow, system requirements, boundaries, and limitations"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
---
# Technical Overview

This topic reviews technical requirements and tips for installing and optimizing [!DNL Live Search] for Adobe Commerce.

## Requirements {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Supported platforms

* Adobe Commerce on-prem (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpoint

[!DNL Live Search] communicates through the endpoint at `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] does not have access to the complete product database, [!DNL Live Search] GraphQL and Commerce core GraphQL will not have complete parity.

It is recommended to call the SaaS API's directly - specifically the Catalog Service endpoint.

* Gain performance and reduce processor load by bypassing the Commerce database/Graphql process
* Take advantage of the [!DNL Catalog Service] federation to call [!DNL Live Search], [!DNL Catalog Service], and [!DNL Product Recommendations] from a single endpoint.

For some use cases, it maybe better to call [!DNL Catalog Service] for product details and similar cases. See [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) for more information.

If you have a custom headless implementation, check out the [!DNL Live Search] reference implementations:

* [PLP widget](https://github.com/adobe/storefront-product-listing-page)
* [Live Search field](https://github.com/adobe/storefront-search-as-you-type)

If you do not use the default components, such as Search Adapter or widgets on Luma, or AEM CIF Widgets, be aware that eventing (clickstream data that feeds Adobe Sensei for Intelligent Merchandising and performance metrics) will not work out of the box and requires custom development to implement headless eventing.
The latest version of [!DNL Live Search] already uses [!DNL Catalog Service] and the installs [!DNL Catalog Service] modules.

## Boundaries and thresholds

Currently, the [!DNL Live Search] search/category API has the following supported limits and static boundaries:

### Indexing

* [Indexes](indexing.md) up to 300 product attributes per store view.
* Indexes only products from the Adobe Commerce database.
* CMS pages are not indexed.

### Query

* [!DNL Live Search] does not have access to the full taxonomy of the category tree, which makes some layered navigation search scenarios beyond its reach.
* [!DNL Live Search] uses a unique GraphQL endpoint for queries to support features such as dynamic faceting and search-as-you-type. Although similar to the [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/), there are a few differences and some fields may not be fully compatible.

To restrict customer groups using Catalog permissions:

* Products must be assigned to the Root category.
* The "Not Logged in" customer group must be given "Allow" browsing permissions.
* To restrict products to the Not Logged In customer group, go to each category and set permission for each customer group.

### Rules

* Maximum number of search merchandising [rules](rules.md) per store view is 50.
* Category merchandising can have one rule per category.
* Maximum number of conditions per rule is 10.
* Maximum number of events per rule is 25.

### Synonyms

* [!DNL Live Search] can manage up to 200 [synonyms](synonyms.md) per store view.

## Language support

[!DNL Live Search] widgets support the following languages:

|||||
|--- |--- |--- |--- |
|Language|Region| Language Code |Magento Locale|
|Bulgarian|Bulgaria|bg_BG|bg_BG|
|Catalan|Spain|ca_ES|ca_ES|
|Czech|Czech Republic|cs_CZ|cs_CZ|
|Danish|Denmark|da_DK|da_DK|
|German|Germany|de_DE|de_DE|
|Greek|Greece|el_GR|el_GR|
|English|United Kingdom|en_GB|en_GB|
|English|United States|en_US|en_US|
|Spanish|Spain|es_ES|es_ES|
|Estonian|Estonia|et_EE|et_EE|
|Basque|Spain|eu_ES|eu_ES|
|Persian|Iran|fa_IR|fa_IR|
|Finnish|Finland|fi_FI|fi_FI|
|French|France|fr_FR|fr_FR|
|Galician|Spain|gl_ES|gl_ES|
|Hindi|India|hi_IN|hi_IN|
|Hungarian|Hungary|hu_HU|hu_HU|
|Indonesian|Indonesia|id_ID|id_ID|
|Italian|Italy|it_IT|it_IT|
|Korean|South Korea|ko_KR|ko_KR|
|Lithuanian|Lithuania|lt_LT|lt_LT|
|Latvian|Latvia|lv_LV|lv_LV|
|Norwegian|Norway Bokmal|nb_NO|nb_NO|
|Dutch|Netherlands|nl_NL|nl_NL|
|Portuguese|Brazil|pt_BR|pt_BR|
|Portuguese|Portugal|pt_PT|pt_PT|
|Romanian|Romania|ro_RO|ro_RO|
|Russian|Russia|ru_RU|ru_RU|
|Swedish|Sweden|sv_SE|sv_SE|
|Thai|Thailand|th_TH|th_TH|
|Turkish|Turkey|tr_TR|tr_TR|
|Chinese|China|zh_CN|zh_Hans_CN|
|Chinese|Taiwan|zh_TW|zh_Hant_TW|

If the widget detects that the Commerce Admin language setting (_Stores_ > Settings > _Configuration_ > _General_ > Country Options) matches a supported language, it defaults to that language. Otherwise, the widgets default to English.

Admins can also set the language of the [search index](settings.md#language), to help ensure better search results.

## Category Merchandising

[Category Merchandising](category-merch.md) allows you to configure [!DNL Live Search] to work on the product category level.

This video is an introduction to Category Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Widget code repository

The Product Listing Page widget and the Live Search field widget are both available for download from their github repository.

This allows developers to fully customize the functionality and styling. These users host the code themselves while still taking advantage of the [!DNL Live Search] service.

* [PLP widget](https://github.com/adobe/storefront-product-listing-page)
* [Search bar](https://github.com/adobe/storefront-search-as-you-type)

## Inventory Management

[!DNL Live Search] supports [Inventory Management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) capabilities in Commerce (formerly knows as Multi-Source Inventory, or MSI). To enable full support, you must [update](install.md#update) the dependency module `commerce-data-export` to version 102.2.0+.

[!DNL Live Search] returns a boolean noting whether a product is available within Inventory Management, but does not contain information about which source has the stock.

## Price indexer

Live Search customers can use the new [SaaS price indexer](../price-index/index.md), which provides faster price change updates and synchronization time.

## Price support

Live Search widgets support most but not all of the price types supported by Adobe Commerce.

Currently, basic prices are supported. Advanced prices that are not supported are:

* Cost
* Minimum Advertised Price

Look at [API Mesh](../catalog-service/mesh.md) for more complex price calculations.

The price format supports the locale configuration setting within the Commerce instance: *Stores* > Settings > *Configuration* > General > *General* > Local Options > Locale.

## PWA support

[!DNL Live Search] works with PWA Studio but users may see slight differences compared to other Commerce implementations. Basic functionality such as search and product listing page work in Venia but some permutations of Graphql may not work correctly. There may also be performance differences.

* The current PWA implementation of [!DNL Live Search] requires more processing time to return search results than [!DNL Live Search] with the native Commerce storefront.
* [!DNL Live Search] in PWA does not support [event handling](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). As a result, search reporting nor intelligent merchandising will work.
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

## Not currently supported

* The [Advanced Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
* [Tier Pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) and [Special Pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) are not supported in the [!DNL Live Search] field and Product Listing Page Widget.

## Cookies

[!DNL Live Search] collects user interaction data as part of its base functionality and cookies are used to store this data. When collecting any user information, the user must agree to store cookies. [!DNL Live Search] and [!DNL Product Recommendations] share the data stream and therefore the same cookie mechanism. Read more about it in [Handle Cookie Restrictions](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
