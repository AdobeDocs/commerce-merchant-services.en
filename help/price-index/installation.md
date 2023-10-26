---
title: SaaS Price Indexing Manual Installation
description: Installing SaaS Price Indexing for older version
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: 4577111a-64a4-4e20-b970-3abfa6758247
role: Admin, Developer
---
# SaaS Price Indexing Manual Installation

SaaS Price Indexing is available out of the box for supported [latest version](index.md#Requirements) of Commerce Services.
If you don't have the latest version and want to enable SaaS Price Indexing for your Adobe Commerce instance, please use this mini-guide.

## Prerequisites

* Adobe Commerce 2.4.4+
* At least one of the following SaaS services is installed:

    * [Catalog Service](../catalog-service/overview.md)
    * [Live Search](../live-search/guide-overview.md)
    * [Product Recommendations](../product-recommendations/guide-overview.md)

## Install required modules

Depending on your setup, the installation process might be slightly different.
There are extensions that add the new feeds and the supporting code.

1. Add the following modules to your `composer.json` file:

    ```json
    "magento/module-saas-price": "^102.2.0",
    "magento/module-saas-scopes": ^"102.2.0",
    "magento/module-product-override-price-remover": "^102.2.0",
    "magento/module-bundle-product-override-data-exporter": "^102.2.0",
    ```

1. Run the upgrade command:

    ```bash
    bin/magento setup:upgrade
    ```

After upgrading, three new feeds are available:

* `prices` - responsible for delivering prices data to the service
* `scopesCustomerGroup` - responsible for delivering Customer Groups to the service 
* `scopesWebsite` - responsible for delivering Websites, Store Groups and Store Views to the service


1. Configure the new feeds to be set to "Update on Schedule" mode:

    ```bash
    bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
    ```

1. Reindex the new feeds:

    ```bash
    bin/magento saas:resync --feed=scopesCustomerGroup
    bin/magento saas:resync --feed=scopesWebsite
    bin/magento saas:resync --feed=prices
    ```

Run the above indexers manually, as needed. Otherwise, the data gets refreshed in the standard sync process. Read more about the [Catalog Sync](../landing/catalog-sync.md) service.


To configure Live Search and Catalog Adapter, follow the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) instructions.

## Caveats

Before `103.0.0` version, SaaS price indexing supported Simple, Grouped, Virtual, Configurable, and Bundle Dynamic product types.
Support for Downloadable, Gift Cards, and Bundle Fixed product types is available starting from `magento/module-saas-price:103.0.0` version and available out of the box for supported Commerce Services.

New feeds should be manually synced with the `resync` [CLI command](../landing/catalog-sync.md#resynccmdline). Otherwise, the data gets refreshed in the standard sync process. Get more information about the [Catalog Sync](../landing/catalog-sync.md) process.
