---
title: "[!DNL Payment Services] Release Notes"
description: Review the release notes for information about all [!DNL Payment Services] releases.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
---
# Release Notes

These release notes describe the initial release of [!DNL Payment Services] and include:

![New](../assets/new.svg) New features
![Fixed issue](../assets/fix.svg) Fixes and improvements
![Known issue](../assets/bug.svg) Known issues

## v1.1.0

![New](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) is now compatible with Adobe Commerce and Magento Open Source versions 2.4.0 to 2.4.4.

![New](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] extension for Adobe Commerce and Magento Open Source is available for Canadian merchants. Merchants can view payments configuration in either [French](overview.md?lang=fr) or [English](overview.md?lang=en).

![New](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Canadian dollars (CAD)](overview.md#accepted-credit-cards-and-currencies) with Credit card and Paypal. Shoppers can have a shopping experience in their preferred language, depending on the locale of the store in which they are shopping.

![New](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants can [onboard [!DNL Payment Services]](onboard.md) extension in their preferred language.

![New](../assets/new.svg)<!-- Issue PAY-2678 --> Merchants can now view [financial reports](order-payment-status.md) in Canadian dollars (CAD).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] is now compatible with [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3035 --> Improved Admin Checkout for the [!DNL Payment Services] extension.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3017 --> Improved Sandbox mode alert to display proper alerts with multiple stores.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] allows to enable/disable available payment methods like Venmo at the storeview level.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2277 --> Improved the merchant's capability in the Admin to selectively disable/enable PayPal smart buttons.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2561 --> Previously removed products do not appear in the cart on the _Review Order_ page.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] improves payment method labels in the Admin.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2907 --> Improved transaction data collection to  best utilize fraud rules and chargeback protection.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 --> Using [incorrect composer keys](https://support.magento.com/hc/en-us/articles/4406603542541) during installation of the extension prevents user to [authenticate](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with correct `MAGEID`.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [reports](https://support.magento.com/hc/en-us/articles/4406114741517) for Payout and Order payment status may not synchronize immediately.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal sandbox account](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] cannot be verified  if account is created during onboarding.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2842 --> [Test credit card fails](https://support.magento.com/hc/en-us/articles/4406954952461) with PayPal when processing payments in a Sandbox environment.

## v1.0.0

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release. [Payment Services](https://marketplace.magento.com/magento-payment-services.html) is now compatible with Adobe Commerce and Magento Open Source versions 2.4.0 to 2.4.3-p1.

![New](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] extension for Adobe Commerce and Magento Open Source can be installed either for [Adobe Commerce on cloud infrastructure](install.md#magento-commerce-cloud) or [On-premises](install.md#on-premises) instances. These methods require the use of a Command Line Interface.

![New](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] supports a [sandbox account](onboard.md#enable-sandbox-testing) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue PAY-666 --> Merchants can [configure Payment Services](configure-admin.md) extension with basic payment behaviors (such as Auth-capture together and switching between sandbox or production environments).

![New](../assets/new.svg)<!-- Issue PAY-780 --> Shoppers can check out with [!DNL Payment Services] or you can take the order over the phone and [create an entire order](create-order.md) in the Admin for them.

![New](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] offer merchants comprehensive reporting so that you can get a clear view of your store orders and payments.

![New](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] supports tiered pricing (based on TPV) adapted to any merchant.

![New](../assets/new.svg)<!-- Issue PAY-1443 --> It is possible to customize the look and feel of PayPal buttons and the CC fields for the [Payment Services](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) extension.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 --> Using [incorrect composer keys](https://support.magento.com/hc/en-us/articles/4406603542541) during installation of the extension prevents user to [authenticate](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with correct `MAGEID`.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [reports](https://support.magento.com/hc/en-us/articles/4406114741517) for Payout and Order payment status may not synchronize immediately.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal sandbox account](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] cannot be verified.
