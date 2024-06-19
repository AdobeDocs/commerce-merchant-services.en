---
title: "[!DNL Manage the Data Export extension]"
description: "Learn how to upgrade the [!DNL Data Export] extension and to remove or disable data export services that are not required."
role: Admin, Developer
recommendations: noCatalog
---

# Manage the SaaS data export Extension

The [!DNL data export] extension for SaaS services is a collection of modules that enable data collection and synchronization between Adobe Commerce and connected Commerce Services.

Specific modules are included in the metapackages for Adobe Commerce Services extensions such
as [Live Search](/help/live-search/overview.md), [Product Recommendations](/help/product-recommendations/overview.md), and [Catalog Service](/help/catalog-service/overview.md). If you are using these services, no separate installation is required to enable the Data Export extension.

## Remove or disable Commerce data export features

If you don't need one of the installed commerce data export modules, use the `magento:module:disable` CLI command to disable it.

For example, there is a [Categories API](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) that uses the categories permission feed data internally. If you are not using this API, you can disable the data export for the categories permission feed.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Update a module to a specific version

You can update any of the installed commerce data export modules by using Composer. For example, you can update a module to a specified version, and also update any required dependencies.

1. Log into the Commerce application server.

1. From the command line, update the module using Composer:

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

If the Commerce instance is deployed on Cloud infrastructure, update the extension from your cloud project directory. See [Upgrade an extension](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) in the _Adobe Commerce on Cloud Infrastructure Guide_.




