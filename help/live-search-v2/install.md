---
title: "Get Started with [!DNL Live Search]"
description: "Learn the system requirements and installation steps for [!DNL Live Search] from Adobe Commerce."
role: Admin, Developer
---
# Set up for success with [!DNL Live Search] and [!DNL Catalog Service]

This comprehensive article provides step-by-step instructions for integrating Adobe Commerce Live Search into your e-commerce platform effortlessly. Whether you are a seasoned developer or a newcomer to Adobe Commerce, this guide equips you with the necessary technical knowledge to seamlessly implement Live Search and enhance your customers' shopping experience.

When you install and configure the [!DNL Live Search] and [!DNL Catalog Service] extensions, data begins to flow between your storefront and backend to SaaS Services.

![Live Search Data Flow](assets/ls-cs-data-flow.png)



## Audience

This article is intended for the developer or systems integrator on your team who is responsible for installing and configuring your Adobe Commerce instance.

## 



FROM ROHAN

Guide should start with common steps spanning all storefront architectures (e.g., "Configure and Sync Your Data", "Set Up Eventing" then break into branches with links for each storefront architecture, with the "recommended approach" for each.
This can happen using a block:
"Select your storefront architecture"
[Reference: See Algolia docs on this page under "Choose your bootstrap tutorial"] -> links jump down to sections of the guide.
After all the recommended implementation options, we can have a section at the bottom of the guide called "Alternative Implementation Options" -> this includes Search Adapter, etc.









## Choose your storefront architecture

This section provides instructions for how to install [!DNL Live Search] and [!DNL Catalog Service] on your Adobe Commerce instance. Choose your storefront architecture.

|Storefront|Install scenario|Link|
|---|---|---|
|Luma|New install||
|Luma|Updating from 3.x to 4.x+||
|AEM + CIF adapter|New install||
|AEM + CIF adapter|Updating from 3.x to 4.x+||
|EDS + CIF adapter|New install||
|EDS + CIF adapter|Updating from 3.x to 4.x+||




### New install on Luma


#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.

### Update Luma install from 3.x to 4.x+

#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.


### New install on AEM + CIF adapter

#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.

### Update AEM + CIF adapter install from 3.x to 4.x+

#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.


### New install on EDS + CIF adapter

#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.

### Update EDS + CIF adapter install from 3.x to 4.x+

#### Technical Requirements

Learn about the prerequisites and technical specifications required for successful installation based on your architecture. This should be included if there are any specific requirements for the architecture used, like for AEM, must use CIF and the Adapter.

#### Integration Options

Explore different integration methods and choose the one that best suits your project requirements.

#### Install

Clear and concise instructions to install Live Search seamlessly. 

#### Customization Guidelines

Discover how to customize Live Search to align with your brand identity and optimize user experience.

#### Troubleshooting Tips

Resolve common installation issues quickly with troubleshooting tips and solutions.

#### Use Cases

Gain insights into real-world scenarios where Live Search can add value to your e-commerce website.

#### Best Practices

Learn industry best practices to maximize the effectiveness of Live Search and drive conversions.













## Before you begin {#before-you-begin}

Do the following:

1. Confirm that [cron jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) and [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are running.



>[!IMPORTANT]
>
>Due to the Elasticsearch 7 end-of-support announcement for August 2023, it is recommended that all Adobe Commerce customers migrate to the OpenSearch 2.x search engine. For information about migrating your search engine during product upgrade, see [Migrating to OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) in the _Upgrade Guide_.
 
Then, it is a step by step flow of implementing catalog service together with Live Search
^That ends up providing the "sizzle" we need + ends up covering the implementation flow
If a customer needs to get onboarded to Live Search, that is the page we send them to

[!DNL Live Search] is installed as an extension from Adobe Marketplace. After the [!DNL Live Search] module (with catalog modules as dependencies) is installed and configured, [!DNL Commerce] begins sharing search and catalog data with SaaS services. At this point, *Admin* users can set up, customize, and manage search facets, synonyms, and merchandising rules.

This topic provides instructions to do the following:

* Install [!DNL Live Search] (Methods 1 and 2)
* [Update [!DNL Live Search]](#update)
* [Uninstall [!DNL Live Search]](#uninstall)



## Method 1: Install without OpenSearch {#method-1}

This onboarding method is recommended when installing [!DNL Live Search] to a:

* New [!DNL Commerce] installation
* Staging environment

In this scenario, storefront operations are interrupted while the [!DNL Live Search] service indexes all products in the catalog. During the installation, [!DNL Live Search] modules are enabled and [!DNL OpenSearch] modules are disabled.

1. Install Adobe Commerce 2.4.4+ without [!DNL Live Search].

1. To download the `live-search` package, run the following from the command line:

   ```bash
   composer require magento/live-search
   ```

1. Run the following commands to disable [!DNL OpenSearch] and related modules, and install [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > While the data is indexed and synchronized, the search and category browse operations are not available in the storefront. Depending on the size of your catalog, the process can take at least an hour from the time `cron` runs to synchronize your data to [!DNL Live Search] services.

1. Verify that the following [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are set to "Update by Schedule":

   * Product Feed
   * Product Variant Feed
   * Catalog Attributes Feed
   * Product Prices Feed
   * Scopes Website Data feed
   * Scopes Customer Groups Data feed
   * Categories Feed
   * Category Permissions Feed

1. Configure your [API keys](#configure-api-keys) and verify that your catalog data is [synchronized](#synchronize-catalog-data) with [!DNL Live Search] services.

1. To make facets available as filters in the storefront, add the [facets](facets-add.md) you need, according to the [faceting requirements](facets.md).

   You should be able to add facets after `cron` runs the attribute feeds and exports attribute metadata.

1. Run the following command in this order:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [Verify](#verify-export) that the data was exported.

1. [Test](#test-the-connection) the connection from the storefront.

## Method 2: Install with OpenSearch {#method-2}

This onboarding method is recommended when installing [!DNL Live Search] to:

* An existing production [!DNL Commerce] installation

In this scenario, [!DNL OpenSearch] temporarily manages search requests from the storefront while the [!DNL Live Search] service indexes all products in the background, without any interruption to normal storefront operations. [!DNL OpenSearch] is disabled and [!DNL Live Search] enabled after all catalog data is indexed and synchronized.

1. To download the `live-search` package, run the following from the command line:

   ```bash
   composer require magento/live-search
   ```

1. Run the following command to temporarily disable the [!DNL Live Search] modules that serve storefront search results.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] continues to manage search requests from the storefront while the [!DNL Live Search] service synchronizes catalog data and indexes products in the background.

1. Verify that the following [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are set to "Update by Schedule":

   * Product Feed
   * Product Variant Feed
   * Catalog Attributes Feed
   * Product Prices Feed
   * Scopes website data feed
   * Scopes customer groups data feed

1. Configure your [API keys](#configure-api-keys) and verify that your catalog data is [synchronized](#synchronize-catalog-data) with [!DNL Live Search] services.

1. To make facets available as filters in the storefront, add the [facets](facets-add.md) you need, according to the [faceting requirements](facets.md).

   You should be able to add facets after `cron` runs the product and attribute feeds and exports attribute metadata to [!DNL Live Search] services.

1. Run the following command in this order:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. After the sync is complete, use the [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) with the default query to verify the following:

   * The returned product count is close to what you expect for the store view.
   * Facet(s) are returned.

1. Run the following commands to enable [!DNL Live Search] modules, disable [!DNL OpenSearch], and run `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Test](#test-the-connection) the connection from the storefront.

## Configure API keys {#configure-api-keys}

The Adobe Commerce API key and its associated private key are required to connect [!DNL Live Search] to an installation of Adobe Commerce. The API key is generated and maintained in the account of the [!DNL Commerce] license holder, who can share it with the developer or SI. The developer can then create and manage the SaaS Data Spaces on behalf of the license holder.  If you already have a set of API keys, you do not need to regenerate them.

### Adobe Commerce license holder

To generate an API key and private key, refer to [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce developer or SI

The developer or SI configures the SaaS data space as described in the *Commerce Services* section of the configuration. In the *Admin*, Commerce Services becomes available in the *Configuration* sidebar when a SaaS module is installed.

## Synchronize catalog data {#synchronize-catalog-data}

[!DNL Live Search] requires synchronized product data for search operations, and synchronized attribute data to configure facets. The initial synchronization between the product catalog and the catalog service begins when [!DNL Live Search] is first connected. Depending on the installation method and size of the catalog, it can take up to 30 minutes for the data to be exported and indexed by [!DNL Live Search]. The list of data that is synchronized and shared with the catalog service can be found in the schema, which is defined in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verify export {#verify-export}

To verify that the catalog data has been exported from your Adobe Commerce instance and is synchronized for [!DNL Live Search], look for entries in the following tables:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

For additional help, refer to [[!DNL Live Search] catalog not synchronized](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in the Support Knowledge Base.

### Future product updates

After the initial synchronization, it can take up to 15 minutes for incremental product updates to become available to storefront search. To learn more, go to [Indexing - Streaming Product Updates](indexing.md).

## Test the connection {#test-connection}

In the storefront, verify the following:

* The [!UICONTROL Search] box returns results correctly
* Category browse returns results correctly
* Facet(s) are available as filters on search results pages

If everything works correctly, congratulations! [!DNL Live Search] is installed, connected, and ready to use.

If you encounter problems in the storefront, check the `var/log/system.log` file for API communication failures or errors on the services side.

To allow Live Search through a firewall, add `commerce.adobe.io` to the allow list.

## Checking the installed version

Before updating Live Search, run the following from the command line to check the version of Live Search that is installed:

```bash
composer show magento/module-live-search | grep version
```

## Updating [!DNL Live Search] {#update}

To update [!DNL Live Search], run the following from the command line:

```bash
composer update magento/live-search --with-dependencies
```

To update to a major version such as from 3.1.1 to 4.0.0, edit the project's root [!DNL Composer] `.json` file as follows:

1. If your currently installed `magento/live-search` version is `3.1.1` or below, and you are upgrading to version `4.0.0` or higher, run the following command before the upgrade:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   For information about the currently installed `magento/live-search` version, run the following command:

   ```bash
   composer show magento/live-search
   ```

1. Open the root `composer.json` file and search for `magento/live-search`.

1. In the `require` section, update the version number as follows:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Save** `composer.json`. Then, run the following from the command line:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Uninstalling [!DNL Live Search] {#uninstall}

To uninstall [!DNL Live Search], refer to [Uninstall modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

| Package | Description |
|--- |--- |
| `module-live-search` | Allows merchants to configure their search settings for faceting, synonyms, query rules, and so on, and provides access to a read-only GraphQL playground to test queries from the *Admin*. |
| `module-live-search-adapter` | Routes search requests from the storefront to the [!DNL Live Search] service and renders the results in the storefront. <br />- Category browse - Routes requests from the storefront [top navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) to the search service.<br />- Global search - Routes requests from the [quick search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) box in the upper-right of the storefront to the [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | A "search as you type" popover replaces the standard quick search and returns data and thumbnails of top search results. |

## [!DNL Live Search] dependencies {#dependencies}

The following [!DNL Live Search] dependencies are captured by [!DNL Composer].
  
* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`









TECHNICAL OVERVIEW ARTICLE CONTENT BEGINS HERE

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

It is recommended to call the SaaS APIs directly - specifically the Catalog Service endpoint.

* Gain performance and reduce processor load by bypassing the Commerce database/Graphql process
* Take advantage of the [!DNL Catalog Service] federation to call [!DNL Live Search], [!DNL Catalog Service], and [!DNL Product Recommendations] from a single endpoint.

For some use cases, it maybe better to call [!DNL Catalog Service] for product details and similar cases. See [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) for more information.

If you have a custom headless implementation, check out the [!DNL Live Search] reference implementations:

* [PLP widget](https://github.com/adobe/storefront-product-listing-page)
* [Live Search field](https://github.com/adobe/storefront-search-as-you-type)

If you do not use the default components, such as Search Adapter or widgets on Luma, or AEM CIF Widgets, eventing (clickstream data that feeds Adobe Sensei for Intelligent Merchandising and performance metrics) will not work out of the box and requires custom development to implement headless eventing.
The latest version of [!DNL Live Search] already uses [!DNL Catalog Service].

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
|Polish|Poland|pl_PL|pl_PL|
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

[!DNL Live Search] supports [Inventory Management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) capabilities in Commerce (formerly knows as Multi-Source Inventory, or MSI). To enable full support, you must [update](install.md#update) the dependency module `commerce-data-export` to version 102.2.0+.

[!DNL Live Search] returns a boolean noting whether a product is available within Inventory Management, but does not contain information about which source has the stock.

## Price indexer

Live Search customers can use the new [SaaS price indexer](../price-index/price-indexing.md), which provides faster price change updates and synchronization time.

## Price support

Live Search widgets support most but not all price types supported by Adobe Commerce.

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

* The [Advanced Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
* [Tier Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) and [Special Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) are not supported in the [!DNL Live Search] field and Product Listing Page Widget.

## Cookies

[!DNL Live Search] collects user interaction data as part of its base functionality and cookies are used to store this data. When collecting any user information, the user must agree to store cookies. [!DNL Live Search] and [!DNL Product Recommendations] share the data stream and therefore the same cookie mechanism. Read more about it in [Handle Cookie Restrictions](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
