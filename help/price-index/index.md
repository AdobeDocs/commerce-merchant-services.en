---
title: Commerce Price Indexer
description: Using the Commerce Price Indexer to improve performance
seo-title: Adobe Commerce Price Indexer
seo-description: Price indexing give performance improvements using SaaS infrastructure
---
# Commerce Price Indexer

The Price Indexer moves price calculations from the monolith to Adobe's cloud environment. This vastly decreases indexing time for large catalogs and frees up server resources for other tasks. 

The indexer is available for free for Commerce customers. It is built into existing SaaS products. 

This mini-guide describes how the indexer works and how to enable it.

## System requirements

To get the SaaS price indexer, you need:

* Adobe Commerce 2.4.4+ (Catalog Adaptor 2.4.5 only for now)
* At least one of the following SaaS services:

    * Catalog Service
    * Live Search
    * Product Recommendations

## Modules

The Commerce price indexer uses a set of modules to provide functionality. The list of required modules could be slightly different, depending on the store setup.

These two modules add the new feeds to the Admin. These feeds use the SaaS indexer and ignore the monolith price indexer.

```
magento/module-saas-price
magento/module-saas-scopes
```

Those with on-premise (EE) installations require the following modules to 

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Customers using LUMA must install a module that provides LUMA compatability and disables the monolith price index:

```bash
composer require adobe-commerce/catalog-adapter
```

Note that the `catalog-adaptor` is only supported by 2.4.5. Support for 2.4.4 and 2.4.6 will be released in the near future.
The monolith price indexer can be re-enabled if needed by a third party extension or any other reason.

## Usage scenarios

### LUMA with no extentions dependencies

* A LUMA merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* Only sells simple, configurable and grouped products
* No third party extensions relying on price indexer

Enable new feeds and the catalog adapter, disabling the price indexer.

### LUMA with extension dependencies

* A LUMA merchant with any of LS/PREX/CS installed
* Selling simple, configurable and grouped products
* With a third party extension relying on price indexer

Enable the new feeds and install the catalog adapter.
Re-enable the default price indexer. 
Use new feeds and LUMA compatibility part from the Catalog Adapter metapackage;

### Headless merchant

* A headless merchants who uses LS/PREX/CS
* Selling simple, configurable and grouped products
* No reliance on monolith price indexer

Enable new feeds and the catalog adapter, which will disable the price indexer.

### LUMA/headless with unsupported product types

* LUMA/Headless merchant
* Selling simple, configurable, grouped, and gift cards

With currently unsupported product types, wait for full product type support.

## Caveats

Depending on factors such as product types, price complexity and catalog size, the Commerce price indexer may be the right solution for your store. Read over the following limitations and determine if this is a good solution for your site.

Currently, for Live Search and Product Recommendations, the new price indexer supports Simple, Virtual, Configurable, and Bundle Dynamic products types.
Support for Downaloable, Gift Cards, and Bundle Fixed product types is expected in 2023.

The price indexer supports base prices:

* Min/Max regular price
* Min/Max final price
* Special prices
* Customer group prices 
* Catalog rule prices

The following items are available in Luma currently not supported by SaaS products.

* Tier prices
* MSRP
* Customizable product options
* Currency rate
* Category rules
* Taxes

Using the Commerce price index is optional.

* Once you opt in to using the new pricing feed, you can contact Support to undo it.
* The Resync button on the Product Recommendations catalog sync dashboard will not run the new price feeds. It should be run with the `resync` [CLI command](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline):

    ```bash
    bin/magento saas:resync --feed=scopesCustomerGroup
    bin/magento saas:resync --feed=scopesWebsite
    bin/magento saas:resync --feed=prices
    ```

## FAQ

What are these improvements and how are they achieved?

The price indexation feed sought to speed up the time it takes for price changes to get reflected on a customer's website after they have been submitted. It allows merchants with large and complex catalogs, or that have many websites or customer groups, to process price changes more rapidly and continuously. The monolith price indexer generally took up 80% of the total indexing time.

Where are the speed improvements coming from? How is the process changing compared to the old one?

The biggest bottleneck of the pipeline: moving computational heavy processes (indexation, calculation, computation), have been moved from the monolith, to the Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes to websites at much faster speeds.

### What are the requirements?

* Adobe Commerce 2.4.4+
* Any of the supported SaaS applications must be installed: Live Search, Product Recommendations, and Catalog Service for Adobe Commerce

### Who is this for?

Merchants that can expect the largest improvements are those with:

* Frequent price changes
* Multiple websites and/or customer groups
* Large number of unique prices across websites or customer groups.

### What are the main benefits?

Considerable reduction in time to process price changes and see them reflected on website.
It uses Adobe's cloud infrastructure. The customer's Adobe Commerce instance is no longer used to process these calculations, freeing up resources for other processes.

### What speed improvements can I expect from the new indexer?

Price changes are updated across websites and customer groups up to 90% faster, depending on catalog composition and the frequency of prices updates.

### Is Magento OS supported?

SaaS services are only available to Adobe Commerce customers.

### Do I have to pay for the price index service?

No, it is free to all Adobe Commerce merchants.

### Will extensions or apps that rely on the current price indexer be affected? If so, how?

If you have third party applications that rely on the current price indexer, read the documentation and consult with the extension provider before making any changes. 
