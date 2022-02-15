---
title: Install the [!DNL Express Checkout] for Adobe Commerce extension
description: Follow these steps to install the [!DNL Upgrade Compatibility Tool] for your Adobe Commerce project.
---

# Install the [!DNL Express Checkout]

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

The [!DNL Express Checkout] for Adobe Commerce powers a seamless checkout experience designed to convert one-time guest shoppers into loyal account holders.

The [!DNL Express Checkout] extension for Adobe Commerce and Magento Open Source can be installed with Composer keys, which are linked to the [Magento ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} provided in the signup process. Composer uses these keys during the initial installation of Adobe Commerce, or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} for more information about obtaining Composer keys.

There are two ways to install this extension---for [Adobe Commerce on cloud infrastructure](#magento-commerce-cloud) or [On-premises](#on-premises) installations. These methods require you to use the Command Line Interface (CLI).

## Update minimum-stability setting

Before installing the extension, you can change the `minimum-stability` requirement to `RC` (release candidate) in your `composer.json` file if you want to try the release candidate version. You can use an IDE or your favorite text editor (like Visual Studio Code or Sublime Text).

In your `composer.json` file, change `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## Install the extension

You can install the [!DNL Express Checkout] extension for both Adobe Commerce on cloud infrastructure and on-premises instances.

### Adobe Commerce on cloud infrastructure

This method is used for installing the [!DNL Express Checkout] extension for a Commerce Cloud instance.

1. On your local workstation, change to the Cloud project root directory.

1. Update your `composer.json` file:

   ```bash
   composer require magento/express-checkout
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/express-checkout`.

1. Commit and push your changes.

### On-premises

This method is used for installing the [!DNL Express Checkout] extension for an On-premises instance.

1. Add the Express Checkout module to the `require` section of the `composer.json` file:

   ```bash
   composer require magento/express-checkout
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/express-checkout`.

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

When we release a new version of the [!DNL Express Checkout], you can easily upgrade your extension.

1. To obtain the most recent version of the package:

   ```bash
   composer update
   ```
   
   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/express-checkout`.

1. Commit and push your changes.

## Troubleshooting

You may see errors when attempting to install the [!DNL Express Checkout] extension. Use the following troubleshooting methods to resolve the errors.

### Incorrect Composer keys

If you see the following error denoting you have the incorrect Composer keys:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Verify that your Composer keys are linked to the Magento ID used during the Express Checkout registration.

To see which Composer keys are configured:

1. Find the location of the `auth.json` file:

   ```bash
   composer config --global home
   ```

1. View the `auth.json` file:

   ```bash
   cat /path/to/auth.json
   ```

1. See [which keys are associated with your Magento ID](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## Prerequisites

See [prerequisites](../express-checkout/prerequisites.md) topic for more information.

>[!NOTE]
>
>You can run the [!DNL Express Checkout] in any operating system.
