---
title: Install and Configure
description: Learn how to install, update, and uninstall [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
---
# Install and Configure

Deploying [!DNL Product Recommendations] to your storefront and Admin requires that you install the module and configure the [Commerce Services Connector](../landing/saas.md). As updates are released, you can easily update your installation with the latest version.

- [Install](#install)
- [Configure](#configure)
- [Update](#update)
- [Uninstall](#uninstall)

## Install [!DNL Product Recommendations] {#install}

Because the [!DNL Product Recommendations] module is a stand-alone metapackage, updates are released more frequently than Adobe Commerce. To make sure you are up to date with the latest bug fixes and features, refer to the [release notes](release-notes.md).

Install the `magento/product-recommendations` module with Composer:

```bash
composer require magento/product-recommendations
```

### Add Page Builder support {#pbsupport}

[!DNL Product Recommendations] for Page Builder is an optional module and is installed separately. To use [!DNL Product Recommendations] with Page Builder, install the module by running the following command:

```bash
composer require magento/module-page-builder-product-recommendations
```

By enabling [!DNL Product Recommendations] in Page Builder, you can add an existing, active [recommendation unit](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) to any content created in Page Builder, such as pages, blocks, and dynamic blocks.

See [Using [!DNL Product Recommendations] with Page Builder Content](page-builder.md) for further instructions.

### Add Visual similarity recommendation type {#vissimsupport}

The _Visual similarity_ recommendation type allows you to deploy a recommendation unit to your product detail page that displays products that are [visually similar](type.md#visualsim) to the product being viewed. This recommendation type is most useful where images and visual aspects of the products are important parts of the shopping experience. Install the _Visual similarity_ recommendation type by running the following command:

```bash
composer require magento/module-visual-product-recommendations
```

## Configure [!DNL Product Recommendations] {#configure}

After you install the `magento/product-recommendations` module, you must configure the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) by specifying API Keys and selecting a SaaS Data Space.

To ensure that catalog export is running correctly, confirm that the [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) jobs and the [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) are running and the `Product Feed` indexer is set to `Update by Schedule`.

When you successfully link to Commerce Services through API keys and specify the SaaS Data Space, the catalog sync begins. You can then [verify](verify.md) that behavioral data is being sent to your storefront.

## Update your [!DNL Product Recommendations] installation {#update}

Like all of Adobe Commerce, [!DNL Product Recommendations] uses Composer for installation and updates. To update the `magento/product-recommendations` module, run the following:

```bash
composer update magento/product-recommendations --with-dependencies
```

To update to a major version, such as from 3.0 to 4.0, you must edit the root `composer.json` file for your project. (See the [release notes](release-notes.md) for information about the latest version.) For example, let's open the main `composer.json` file and search for the `magento/product-recommendations` module:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Let's bump the major version from `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Save the `composer.json` file and run:

```bash
composer update magento/product-recommendations --with-dependencies
```

Or if you have installed the `magento/module-visual-product-recommendations` and `magento/module-page-builder-product-recommendations` modules:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> In versions 3.x.x of Product Recommendations, you only needed a single API key. In versions 4.x.x and higher, you must provide Production public and private API keys as well as Sandbox public and private API keys. If you do not provide both pairs of API keys, you cannot access the Product Recommendations feature in the Admin. Data collection, however, will continue on your storefront and existing recommendations will continue to be shown to your shoppers.

## Firewalls

If you need to let Product Recommendations through a firewall, add `commerce.adobe.io` to the allow list.

## Uninstall [!DNL Product Recommendations] {#uninstall}

If necessary, you can [uninstall](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) the product-recommendations module.
