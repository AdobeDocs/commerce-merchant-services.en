---
title: Install Payment Services
description: Install the Payments Services extension.
---
# Install Payment Services

Installing the Payment Services extension for Adobe Commerce and Magento Open Source is a prerequisite step for using Payment Services.

![Payment Services extension Admin view](assets/admin-view.png)

The Payment Services extension for Adobe Commerce and Magento Open Source can be installed with Composer keys, which are linked to the Magento ID ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) provided in the signup process. Composer uses these keys during the initial installation of Adobe Commerce, or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) for more information about obtaining Composer keys.

There are two ways to install this extension---for [Adobe Commerce on cloud infrastructure](https://devdocs.magento.com/payment-services/install-payments.html#magento-commerce-cloud) or [On-premises](https://devdocs.magento.com/payment-services/install-payments.html#on-premises) installations. These methods require you to use the Command Line Interface (CLI).

## Update minimum-stability setting

Before installing the extension, you must change the `minimum-stability` requirement to `RC` (release candidate) in your `composer.json` file. You can use an IDE or your favorite text editor (like Visual Studio Code or Sublime Text).

In your `composer.json` file, change `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## Install the extension

You can install the Payment Services extension for both Adobe Commerce on cloud infrastructure and on-premises instances.

### Adobe Commerce on cloud infrastructure

This method is used for installing the Payment Services extension for a Commerce Cloud instance.

1. Update your `composer.json` file:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer require magento/payment-services`.

1. Commit and push your changes.

### On-premises

This method is used for installing the Payment Services extension for an On-premises instance.

1. To obtain the extension, run these commands:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer require magento/payment-services`.

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Clear the cache:

   ```bash
   bin/magento cache:clean
   ```

1. Commit changes.
1. To ensure that the committed code is deployed, update your on-premises instance .

## Upgrade the extension

When a new version of Payment Services is released, you can easily upgrade your extension.

1. To obtain the most recent version of the package:

   ```bash
   composer update
   ```

   The `composer update` command updates all dependencies. If you do not want to update all dependencies at the same time, use this command instead: `composer update magento/payment-services`.

1. Commit and push your changes.

## Troubleshooting

You may see errors when attempting to install the Payment Services extension. Use the following troubleshooting methods to resolve the errors.

### Incorrect Composer keys

If you see the following error denoting that you have the incorrect Composer keys:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Verify that your Composer keys are linked to the Magento ID used during Payment Services registration.

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

### Not enough memory for PHP

If you see the following error denoting you do not have enough memory for PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Increase the memory limit](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) for PHP on your environment in `php.ini`.

Alternatively, you can specify the memory limit using this command: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
