---
title: SaaS Price Indexing
description: Using the SaaS Price Indexing to improve performance
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
---
# SaaS Price Indexing

SaaS price indexing speeds up the time it takes for price changes to get reflected on a customer's website after they have been submitted. This optional modulue allows merchants with large, complex catalogs, or with multiple websites or customer groups, to process price changes more rapidly and continuously.

The biggest bottleneck of the pipeline: computational heavy processes such as indexation and price calculation, have been moved from the PHP core to the Adobe's Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes to websites at much faster speeds.

All merchants who meet the requirements can benefit from these improvements, but those who will see the largest uptick are those customers with: 

* Constant price changes: Merchants that require repeated changes to their prices to meet strategic goals such as frequent promotions, seasonal discounts, or inventory markdowns.
* Multiple websites and/or customer groups: Merchants with shared product catalogs across multiple websites (domains/brands) and/or customer groups. 
* Large number of unique prices across websites or customer groups: Merchants with extensive shared product catalogs that contain unique prices across websites or customer groups, such as B2B merchants with pre-negotiated prices, brands with different pricing strategies.

If you have third party applications that rely on the PHP core price indexer, read the documentation and consult with the extension provider before making any changes. 

SaaS price indexing is available for free for customers using Adobe Commerce services.

This mini-guide describes how SaaS price indexing works and how to enable it.

## System requirements

To use SaaS price indexing, you need:

* Adobe Commerce 2.4.4+
* At least one of the following SaaS services installed:

    * [Catalog Service](../catalog-service/overview.md)
    * [Live Search](../live-search/guide-overview.md)
    * [Product Recommendations](../product-recommendations/guide-overview.md)

## Modules

SaaS price indexing uses a set of modules to provide functionality. The list of required modules could be slightly different, depending on the store setup.

These two modules add the new feeds to the Admin. These feeds transfer data required for price calculations to the SaaS indexer and ignores the PHP core price indexer.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Customers using Luma and Adobe Commerce Core GraphQL can install a module that provides Luma compatability and disables the PHP core price indexer:

```
adobe-commerce/catalog-adapter
```

Note that the `catalog-adapter` is only compatible with 2.4.5. Support for 2.4.4 and 2.4.6 will be released in the near future.
The PHP core price indexer can be re-enabled if needed by a third party extension or any other reason.

## Caveats

Depending on factors such as product types, price complexity and catalog size, SaaS price indexing may be the right solution for your store. Read over the following limitations and determine if this is a good solution for your site.

Currently, SaaS price indexing supports Simple, Grouped, Virtual, Configurable, and Bundle Dynamic product types.
Support for Downloadable, Gift Cards, and Bundle Fixed product types is coming soon.

SaaS price indexing supports base prices:

* Min/Max regular price
* Min/Max final price
* Special prices
* Customer group prices 
* Catalog rule prices

Once you opt in to using the new pricing feed, you can contact [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) to help you undo it.

New feeds should be manually synced with the `resync` [CLI command](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Otherwise, the data gets refreshed in the standard sync process. Get more infomation about the [Catalog Sync](../landing/catalog-sync.md) process.

## Usage scenarios

### Luma with no extention dependencies

* A Luma or Abode Commerce Core GraphQL merchant who has a required service installed (Live Search, Product Recommendations, Catalog Service)
* No third party extensions relying on the PHP core price indexer
* Selling simple, configurable, grouped, virtual, and bundle dynamic products

1. Enable new feeds.
1. Install the catalog adapter.

### Luma and Abode Commerce Core GraphQl with PHP core price indexer dependencies

* A Luma or Abode Commerce Core GraphQL merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* With a third party extension relying on the PHP core price indexer
* Selling simple, configurable, grouped, virtual, and bundle dynamic products

1. Enable the new feeds
1. Install the catalog adapter.
1. Re-enable the PHP core price indexer. 
1. Use new feeds and the Luma compatibility code in the `catalog-adapter` module.

### Headless merchant

* A headless merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* No reliance on PHP core price indexer
* Selling simple, configurable, grouped, virtual, and bundle dynamic products

1. Enable new feeds
1. Install the catalog adapter, which disables the PHP core price indexer.

### Luma/Core GraphQL/Headless with unsupported product types

* Luma/Headless merchant
* Selling gift cards, downloadable, or bundle fixed products

With currently unsupported product types, wait for full product type support.
