---
title: Price Indexing Service Installation
description: Installing the Price Indexing service
seo-title: Adobe Commerce Services Price Indexing installation
seo-description: Installing the Price indexing service
---
# Price Indexing Service Installation

Setting up the Price Indexing Service requires installing new modules and running CLI commands. Admins will need command line access to complete this installation.

## Prerequisites

To use the price indexing service, you must have installed, or install, one of the supported Commerce services:

* Catalog Service
* Live Search
* Product Recommendations

## Install required modules

Depending on your setup, the installation process might be slightly different.
There are extensions that add the new feeds and supporting code and there is an extension that removes the default prices feed.

1. Add the following modules to your `composer.json` file:

    For Cloud Environments:

    ```json
    "magento/module-saas-price": "102.1.0",
    "magento/module-saas-scopes": "102.1.0",
    "adobe-commerce/catalog-adapter"
    ```

    For Enterprise Environments:

    ```json
    "magento/module-saas-price": "102.1.0",
    "magento/module-saas-scopes": "102.1.0",
    "magento/module-product-override-price-remover": "102.1.0",
    "magento/module-bundle-product-override-data-exporter": "102.1.0",
    "adobe-commerce/catalog-adapter"
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

For LUMA or Adobe Commerce GraphQL customers that do not have 3rd party modules that rely on price indexer, install all modules; 
if you are headless merchants, you will need to install new pricing module and price indexer disabler. 


1. Reindex the new feeds:

    ```bash
    bin/magento saas:resync --feed=scopesCustomerGroup
    bin/magento saas:resync --feed=scopesWebsite
    bin/magento saas:resync --feed=prices
    ```


