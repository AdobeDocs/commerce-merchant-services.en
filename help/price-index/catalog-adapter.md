---
title: Catalog Adapter Extension
description: Using Catalog Adapter to render prices from Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
---
# Catalog Adapter

The `[!DNL Catalog Adapter]` extension disables the default product price indexer included in the Commerce application and uses prices provided by the [Catalog Service](../catalog-service/overview.md) instead.

The adapter is designed to work with the [SaaS data export](../data-export/overview.md) and the Adobe Commerce Service. SaaS data export is responsible for submitting the prices, and the [!DNL Catalog Adapter] retrieves all the prices from the Adobe Commerce Service.

When you enable the [!DNL Catalog Adapter], price indexing and operations are affected in the following ways:

- The price indexer included in the Adobe Commerce application is disabled.
- Prices are managed using the SaaS data export and the [SaaS price indexer](price-indexing.md).
- When a customer opens a product, category or other page that shows product prices, the prices are retrieved from the Adobe Commerce Service.
- Prices are sent to the Adobe Commerce Service by syncing data from the [SaaS data export](../data-export/overview.md).
- Checkout recalculates prices dynamically.

 You can reenable price indexing in the Commerce application by removing or disabling the Catalog Adapter extension.

## Requirements

- Adobe Commerce 2.4.4+
- Have one of the following Commerce Services installed:

  - [Live Search](../live-search/install.md)
  - [Product Recommendations](../product-recommendations/install-configure.md)
  - [Catalog Service](../catalog-service/installation.md)

## Installation

The Catalog Adapter extension is a Composer metapackage that installs the following modules:

- **Price Indexer Disabler**–This module disables the price index in the Commerce application so that prices are delivered via SaaS price indexing. The product price indexer in the Commerce application cannot be turned on when the SaaS price indexing extension is installed.
- **Prices Provider**–This module provides prices for products from the Adobe Commerce Service. It forms the search query and obtains the prices for the products on the frontend.
- **Catalog Service Search Adapter**–This module transfers prices from the Adobe Commerce application to an Adobe Commerce Service in response to a product search request.

## Installation steps

>[!BEGINTABS]

>[!TAB Cloud infrastructure]

Use this method to install the [!DNL Catalog Adapter] for a Commerce Cloud instance.

1. On your local workstation, change to the project directory for your Adobe Commerce on cloud infrastructure project.

   >[!NOTE]
   >
   >For information about managing Commerce project environments locally, see [Managing branches with the CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) in the _Adobe Commerce on Cloud Infrastructure User Guide_.

1. Check out the environment branch to update using the Adobe Commerce Cloud CLI.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Add the Catalog Adapter module.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Update package dependencies.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Commit and push code changes for the `composer.json` and `composer.lock` files.

1. Add, commit, and push the code changes for the `composer.json` and `composer.lock` files to the cloud environment.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   Pushing the updates to the cloud environment initiates the [Commerce cloud deployment process](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) to apply the changes. Check the deployment status from the [deploy log](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-premises]

Use this method to install the [!DNL Catalog Adapter] for an on-premises instance.

1. Add the Catalog Adapter to your project using Composer:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Clear the cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In some cases, particularly when deploying to production, you might wish to avoid clearing compiled code because it can take some time. Ensure that you back up your system before making any changes.

>[!ENDTABS]


## Re-enable the Adobe Commerce product price indexer

If you have third-party applications that rely on the default Adobe Commerce product price indexer, you can re-enable it with the following commands:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Disable Product Price indexer for Headless Storefront scenario

If you have a headless Commerce instance, you might need to disable the Adobe Commerce product price indexer to reduce load on your Adobe Commerce instance. You can complete this task by installing the `magento/module-price-indexer-disabler` module:

```bash
composer require magento/module-price-indexer-disabler
```

## Usage scenarios

The following are some common `[!DNL Catalog Adapter]` scenarios.

### No dependencies on Adobe Commerce product price indexer

- You are a Luma or Adobe Commerce Core GraphQL merchant who has a required service installed (Live Search, Product Recommendations, Catalog Service)
- No integrations with third-party extensions that rely on the Adobe Commerce product price indexer

1. Install the [!DNL Catalog Adapter].

### With dependencies on Adobe Commerce product price indexer

- You are a Luma or Adobe Commerce Core GraphQL merchant who has a supported service installed (Live Search, Product Recommendations, Catalog Service)
- You use a third-party extension relying on the Adobe Commerce product price indexer

1. Install the [!DNL Catalog Adapter].
1. Re-enable the default Adobe Commerce product price indexer.

### Headless Commerce instances

- A merchant with a headless Commerce instance with the required services installed (Live Search, Product Recommendations, Catalog Service)
- No reliance on the default Adobe Commerce product price indexer

1. Install the `magento/module-price-indexer-disabler` module from the [!DNL Catalog Adapter] package.

