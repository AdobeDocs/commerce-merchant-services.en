---
title: "Troubleshooting issues for the [!DNL Quick Checkout]"
description: "Troubleshoot errors, known issues you may experience while using the [!DNL Quick Checkout] for Adobe Commerce extension."
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
---
# Troubleshoot [!DNL Quick Checkout] for Adobe Commerce

Use the following troubleshooting methods to resolve these specific issues.

## Incorrect [!DNL Composer keys]

If you see the following error denoting you have the incorrect [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Verify that your [!DNL Composer keys] are linked to the Magento ID used during the Quick Checkout registration.

To see which [!DNL Composer keys] are configured:

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

If you see the following error denoting you have the incorrect [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Set minimum-stability to `RC` in the `composer.json` file.

## Not enough memory for PHP

If you see the following error denoting you do not have enough memory for PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Increase the memory limit](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) for PHP on your environment in `php.ini`.

Alternatively, you can specify the memory limit using this command: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Invalid shipping address

There is a known issue for the [!DNL Quick Checkout].

When the default shipping address is not valid, customer is redirected to the shipping address step. Storefront only shows valid shipping addresses.

>[!WARNING]
>
> if there are no valid shipping addresses customer does not see any available shipping address.

Refer to the [shipping details](../quick-checkout/shipping-details.md) topic for more information.

## Add street address lines with a new shipping address

There is a known issue for the [!DNL Quick Checkout].

When you [log in with a [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) you can add a new shipping address with a limitation of 4 lines per street address.

Adobe Commerce usually can be configured to support up to 20 street address lines.

## Checkbox `enable terms and conditions` not displaying properly

There is a known issue for the [!DNL Quick Checkout].

When you enable the `Enable terms and conditions` checkbox in the Admin and log in with a [!DNL Bolt] account, the `Enable terms and conditions` checkbox is not displayed during the checkout. Refer to the [Log in](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] topic for more information.

See [terms and conditions](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) topic for more information on the Admin configuration.

## Unexpected behaviour when `Display Billing Address On` is set to `payment page`

There is a known issue for the [!DNL Quick Checkout].

If you set the `Display Billing Address On` parameter to `payment page` and [login with a [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) when you check the `My billing and shipping address are the same` checkbox the radio button displays `use existing card`.

![Same address](assets/checked-address.png)

See the [Checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) topic for more information about the `Display Billing Address On` parameter.

## Translating the [!DNL Quick Checkout] extension

Adobe Commerce enables you to localize your store for multiple regions and markets. You can even localize error messages in your Admin view.

Refer to the [translating and localizing](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) topic for more information.

## Flush your cache

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

## Get help

Contact [Adobe Commerce Support](mailto:quick-checkout-support@adobe.com) for assistance.
