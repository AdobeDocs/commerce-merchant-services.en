---
title: Troubleshooting issues for the [!DNL Express Checkout]
description: Troubleshoot errors, known issues you may experience while using the [!DNL Express Checkout] for Adobe Commerce extension.
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
---
# Troubleshoot [!DNL Express Checkout] for Adobe Commerce

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

Use the following troubleshooting methods to resolve these specific issues.

## Incorrect Composer keys

If you see the following error denoting you have the incorrect Composer keys:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
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

## Minimum stability in the `composer.json` is set to stable

If you see the following error denoting you have the incorrect Composer keys:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Set minimum-stability to `RC` in the `composer.json` file.

## Not enough memory for PHP

If you see the following error denoting you do not have enough memory for PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Increase the memory limit](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) for PHP on your environment in `php.ini`.

Alternatively, you can specify the memory limit using this command: `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## Invalid shipping address

There is a known issue for the [!DNL Express Checkout].

When the default shipping address is not valid, customer is redirected to the shipping address step. Storefront only shows valid shipping addresses.

>[!WARNING]
>
> if there are no valid shipping addresses customer does not see any available shipping address.

Refer to the [shipping details](../express-checkout/shipping-details.md) topic for more information.

## Add street address lines with a new shipping address

There is a known issue for the [!DNL Express Checkout].

When you [login with a Bolt account](https://help.bolt.com/shoppers/guides/checkout/log-in/) you can add a new shipping address with a limitation of 4 lines per street address.

Adobe Commerce usually can be configured to support up to 20 street address lines.

## Checkbox `enable terms and conditions` not displaying properly

There is a known issue for the [!DNL Express Checkout].

When you enable the `Enable terms and conditions` checkbox and [login with a Bolt account](https://help.bolt.com/shoppers/guides/checkout/log-in/), the checkbox is not displayed.

See [terms and conditions](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) topic for more information.

## Unexpected behaviour when `Display Billing Address On` is set to `payment page`

There is a known issue for the [!DNL Express Checkout].

If you set the `Display Billing Address On` parameter to `payment page` and [login with a Bolt account](https://help.bolt.com/shoppers/guides/checkout/log-in/) when you check the `My billing and shipping address are the same` checkbox:

![Same address](../assets/checked-address.png)

Radio button displays `use existing card`.

See [Checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) topic for more information on the `Display Billing Address On` parameter.

## Translating the [!DNL Express Checkout] extension

Adobe Commerce enables you to localize your store for multiple regions and markets. You can even localize error messages in your Admin view.

Refer to the [translating and localizing](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) topic for more information.

## Get help

Contact Adobe Commerce Support for more assistance or questions.
