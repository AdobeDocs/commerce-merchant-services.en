---
title: Troubleshooting issues for the [!DNL Express Checkout]
description: Troubleshoot errors, known issues you may experience while using the [!DNL Express Checkout] for Adobe Commerce extension.
---

# Troubleshoot [!DNL Express Checkout] for Adobe Commerce

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

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

Contact Adobe Commerce Support for assistance and questions.
