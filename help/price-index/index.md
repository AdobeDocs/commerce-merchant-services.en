---
title: SaaS Price Indexer
description: Using the SaaS Price Indexer to improve performance
seo-title: Adobe SaaS Price Indexer
seo-description: Price indexing give performance improvements using SaaS infrastructure
---
# SaaS Price Indexer

The price indexation feed sought to speed up the time it takes for price changes to get reflected on a customer's website after they have been submitted. It allows merchants with large and complex catalogs, or that have many websites or customer groups, to process price changes more rapidly and continuously. The PHP core price indexer generally took up 80% of the total indexing time.

The biggest bottleneck of the pipeline: computational heavy processes such as indexation and price calculation, have been moved from the PHP core to the Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes to websites at much faster speeds. Price changes are updated across websites and customer groups up to 90% faster, depending on catalog composition and the frequency of prices updates.

Merchants that can expect the largest improvements are those with:

* Frequent price changes
* Multiple websites and/or customer groups
* Large number of unique prices across websites or customer groups

If you have third party applications that rely on the current price indexer, read the documentation and consult with the extension provider before making any changes. 

The indexer is available for free for customers using Adobe Commerce services.

This mini-guide describes how the indexer works and how to enable it.

## System requirements

To get the SaaS price indexer, you need:

* Adobe Commerce 2.4.4+
* At least one of the following SaaS services installed:

    * [Catalog Service](../catalog-service/overview.md)
    * [Live Search](../live-search/guide-overview.md)
    * [Product Recommendations](../product-recommendations/guide-overview.md)

## Modules

The SaaS price indexer uses a set of modules to provide functionality. The list of required modules could be slightly different, depending on the store setup.

These two modules add the new feeds to the Admin. These feeds transfer data required for price calculations to the SaaS indexer and ignores the PHP core price indexer.

```
magento/module-saas-price
magento/module-saas-scopes
```

Those with on-premise (EE) installations require the following modules:

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Customers using LUMA can install a module that provides LUMA compatability and disables the PHP core price indexer:

```
adobe-commerce/catalog-adapter
```

Note that the `catalog-adapter` is only compatible with 2.4.5. Support for 2.4.4 and 2.4.6 will be released in the near future.
The PHP core price indexer can be re-enabled if needed by a third party extension or any other reason.

## Caveats

Depending on factors such as product types, price complexity and catalog size, the SaaS price indexer may be the right solution for your store. Read over the following limitations and determine if this is a good solution for your site.

Currently, for Live Search and Product Recommendations, the new price indexer supports Simple, Virtual, Configurable, and Bundle Dynamic products types.
Support for Downloadable, Gift Cards, and Bundle Fixed product types is expected in 2023.

The price indexer supports base prices:

* Min/Max regular price
* Min/Max final price
* Special prices
* Customer group prices 
* Catalog rule prices

The following items available in Luma are currently not supported by SaaS products:

* Tier prices
* MSRP
* Customizable product options
* Currency rate
* Category rules
* Taxes

Using the SaaS price index is optional.

Once you opt in to using the new pricing feed, you can contact Support to undo it.
* The Resync button on the Product Recommendations catalog sync dashboard will not run the new price feeds. It should be run with the `resync` [CLI command](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline).

## Usage scenarios

### LUMA with no extention dependencies

* A LUMA merchant who has a required service installed (Live Search, Product Recommendations, Catalog Service)
* Only sells simple, configurable and grouped products
* No third party extensions relying on the PHP core price indexer

1. Enable new feeds.
1. Install the catalog adapter.
1. Disable the price indexer.

### LUMA with price index extension dependencies

* A LUMA merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* Selling simple, configurable and grouped products
* With a third party extension relying on the PHP core price indexer

1. Enable the new feeds
1. Install the catalog adapter.
1. Re-enable the default price indexer. 
1. Use new feeds and the LUMA compatibility code.

### Headless merchant

* A headless merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* Selling simple, configurable and grouped products
* No reliance on PHP core price indexer

1. Enable new feeds
1. Install he catalog adapter, which disables the price indexer.

### LUMA/headless with unsupported product types

* LUMA/Headless merchant
* Selling simple, configurable, grouped, and gift cards

With currently unsupported product types, wait for full product type support.
