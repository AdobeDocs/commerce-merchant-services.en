---
title: Catalog Adapter Extension
description: Using Catalog Adapter to render prices from Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: TBD
---

# Catalog Adapter

The `Catalog Adapter` extension disables the default Adobe Commerce Product Price indexer and instead uses prices provided from the [Catalog Service](../catalog-service/overview.md).
The Adobe Commerce Product Price indexer is disabled and cannot be turned on with these extension modules installed. Only by removing or disabling this extension can the default product price indexer be reenabled.

## Requirements

* Adobe Commerce 2.4.4+
* One of the following Commerce Services installed:

    * [Catalog Service](../catalog-service/overview.md)
    * [Live Search](../live-search/guide-overview.md)

## Installation

To use the `catalog-adapter` module, [!DNL Live Search] and [!DNL Catalog Service] must first be installed and configured. Follow the [Install [!DNL Live Search]](../live-search/install.md) and [Catalog Service Installation](../catalog-service/installation.md) instructions before continuing.

Once those services are installed, run the following command:

```bash
composer require adobe-commerce/catalog-adapter
```

## Renable the Adobe Commerce Product Price indexer

If you have third-party applications that rely on the default Adobe Commerce Product Price indexer, it can be re-enabled with the following commands:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Disable Product Price indexer for Headless Storefront scenario

If you have a headless Commerce instance, you may need to disable the Adobe Commerce Product Price indexer to reduce load on your Adobe Commerce instance.
This is done by installing the `magento/module-price-indexer-disabler` module:

```bash
composer require magento/module-price-indexer-disabler
```

## Usage scenarios

The following are some common `Catalog Adapter` scenarios.

### No dependencies on Adobe Commerce Product Price indexer

* You are a Luma or Adobe Commerce Core GraphQL merchant who has a required service installed (Live Search, Product Recommendations, Catalog Service)
* No third-party extensions relying on the Adobe Commerce Product Price indexer

1. Install the catalog adapter.

### With dependencies on Adobe Commerce Product Price indexer

* You are a Luma or Adobe Commerce Core GraphQL merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
* You use a third-party extension relying on the Adobe Commerce Product Price indexer

1. Install the catalog adapter.
1. Re-enable the default Adobe Commerce Product Price indexer.

### Headless Commerce instances

* A merchant with a headless Commerce instance with the required services installed (Live Search, Product Recommendations, Catalog Service)
* No reliance on the default Adobe Commerce Product Price indexer

1. Install "price disabler" from the catalog adapter package
