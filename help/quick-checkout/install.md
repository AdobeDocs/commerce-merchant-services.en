---
title: "Install [!DNL Quick Checkout] for Adobe Commerce extension"
description: "Follow these steps to install [!DNL Quick Checkout] in your Adobe Commerce project."
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
---
# Install [!DNL Quick Checkout]

The [!DNL Quick Checkout] extension for Adobe Commerce and [!DNL Magento Open Source] can be installed with [!DNL Composer keys], which are linked to the Commerce account [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} provided in the signup process. Composer uses these keys during the initial installation of Adobe Commerce, or in situations in which the [!DNL Composer keys] were not previously saved to the `auth.json` file.

See [get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} topic for more information about obtaining [!DNL Composer keys].

There are two ways to install this extension---for [Adobe Commerce on cloud infrastructure](#magento-commerce-cloud) or [on-premises](#on-premises) installations. These methods require you to use the command-line interface (CLI).

## Update minimum-stability setting

Before you install the extension, ensure that the `minimum-stability` field in your `composer.json` file is set to `"stable"`:

`"minimum-stability": "stable"`

## Install the extension

You can install the [!DNL Quick Checkout] extension for both Adobe Commerce on cloud infrastructure and on-premises instances.

### Adobe Commerce on cloud infrastructure

This method is used for installing the [!DNL Quick Checkout] extension for a Commerce Cloud instance.

1. On your local workstation, change to the Cloud project root directory.

1. Update your `composer.json` file:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/quick-checkout`.

1. Commit and push your changes.

### On-premises

This method is used for installing the [!DNL Quick Checkout] extension for an On-premises instance.

1. Add the Quick Checkout module to the `require` section of the `composer.json` file:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/quick-checkout`.

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Clear the cache:

   ```bash
   bin/magento cache:clean
   ```

1. Commit changes.
1. Update your on-premises instance to ensure the committed code is deployed.

## Upgrade the extension

When we release a new version of the [!DNL Quick Checkout], you can easily upgrade your extension.

1. To obtain the most recent version of the package:

   ```bash
   composer update
   ```
   
   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/quick-checkout`.

1. Commit and push your changes.

## Troubleshooting

You may see errors when attempting to install the [!DNL Quick Checkout] extension.

If you encounter any issues during the [!DNL Quick Checkout] installation process, see [Troubleshoot Quick Checkout issues](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) in the Adobe Commerce Help Center.

## Prerequisites

See the [prerequisites](../quick-checkout/prerequisites.md) topic for more information.
