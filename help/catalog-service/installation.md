---
title: Onboarding and Installation
description: Learn how to install [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
---
# Onboarding and Installation

## Prerequisites

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server. If you are not familiar with working from the command line, ask a developer or system integrator to help.

### Software requirements

-  Adobe Commerce 2.4.x
-  PHP 8.1, 7.4, 7.3
-  Composer: 2.x, 1.x

### Supported platforms

-  Adobe Commerce on cloud infrastructure: 2.4.x
-  Adobe Commerce on premises: 2.4.x

## Install the extension

You can install the [!DNL Catalog Service] extension for both Adobe Commerce on cloud infrastructure and on-premises instances.

The [!DNL Catalog Service] is installed with Composer keys, which are linked to the Commerce account [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) provided in the signup process. Composer uses these keys during the initial installation of [!DNL Adobe Commerce], or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) for more information about obtaining Composer keys.

### Adobe Commerce on cloud infrastructure

Use this method for installing the [!DNL Catalog Service] extension for a Commerce Cloud instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the `require` section as follows:

   ```json
   "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1"
    }
   ```

1. Test the new configuration locally and update dependencies:

   ```bash
   composer update
   ```

   The command updates all dependencies.

1. Commit and push your changes for `composer.json` and `composer.lock`.

### On-premises

Use this method for installing the [!DNL Catalog Service] extension for an on-premises instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the `require` section as follows:

   ```json
   "require": {
    "magento/module-saas-catalog": "^101.4.0",
    "magento/module-saas-product-override": "^101.4.0",
    "magento/module-saas-product-variant": "^101.4.0",
    "magento/module-bundle-product-data-exporter": "^101.3.1",
    "magento/module-catalog-data-exporter": "^101.3.1",
    "magento/module-catalog-inventory-data-exporter": "^101.3.1",
    "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
    "magento/module-configurable-product-data-exporter": "^101.3.1",
    "magento/module-data-exporter": "^101.3.1",
    "magento/module-parent-product-data-exporter": "^101.3.1",
    "magento/module-product-override-data-exporter": "^101.3.1",
    "magento/data-services": "^7.0.11",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
   }
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The command updates all dependencies.

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Clear the cache:

   ```bash
   bin/magento cache:clean
   ```

## Configure catalog export

After you install [!DNL Catalog Service], you must configure the [Commerce Services Connector](../landing/saas.md) by specifying API Keys and selecting a SaaS Data Space.

To ensure that the catalog export is running correctly:

-  Confirm that [cron jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) are running. 
-  Verify the [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) are running.
-  Ensure that the `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`, and `Product Variant Feed` indexers are set to `Update by Schedule`.

## Catalog Service and API Mesh

The [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) enables developers to integrate private or third-party APIs and other interfaces with Adobe products using Adobe IO.

The first step for using the API Mesh with Catalog Service is to connect API Mesh to your instance. See detailed instructions in [Create a Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

To complete the setup, you will need the [Adobe IO CLI package](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installed.

Once Mesh is configured on Adobe IO, run the following command which adds a `CommerceCatalogServiceGraph` source to your mesh.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` is a separate file that stores commonly used values for Adobe IO.
For instance, the API key can be saved within the file:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

After running this command, the Catalog Service should be running through the API Mesh. You can run the `aio api-mesh:get` command to view the configuration of your updated mesh.

## [!DNL Catalog Service] demo

Watch this video to learn about [!DNL Catalog Service] installation and testing:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
