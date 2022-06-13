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

See [Upcoming Releases](https://devdocs.magento.com/release/) to learn about release schedules and support.

See [Availabilty](https://devdocs.magento.com/release/availability.html) in the developer documentation to learn about product compatibility.

## v1.1.0

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release---[!DNL Payment Services] is now [compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![New](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] extension for [!DNL Adobe Commerce] and [!DNL Magento Open Source] is now available for Canadian merchant. Merchants can view payments configuration in either [French](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) or [English](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![New](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Canadian dollars (CAD)](overview.md#accepted-credit-cards-and-currencies) for credit cards and PayPal transactions.

![New](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants can [onboard [!DNL Payment Services]](onboard.md) extension in English or French languages.

![New](../assets/new.svg)<!-- Issue PAY-2678 --> Merchants can now view financial reports, both the [Order payment status](order-payment-status.md) and [Payouts reports](payouts.md), in Canadian dollars (CAD).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] is now compatible with [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3017 --> Improved Sandbox mode alert to display proper alerts with multiple stores. -->

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2742 --> You can now enable and disable available payment methods, such as Venmo, at the store view level. Previously, you could configure payment methods per website only.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2277 --> You can now selectively [enable or disable individual PayPal smart buttons](settings.md#paypal-smart-buttons).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2561 --> Previously removed products do not appear in the cart on the _Review Order_ page.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2842 --> Test credit card transactions [may fail with PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) when processing payments in a sandbox environment.

## v1.0.0

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release---[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) is now compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.3-p1.

![New](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] extension for [!DNL Adobe Commerce] and [!DNL Magento Open Source] can be installed either for [[!DNL Adobe Commerce] on cloud infrastructure](install.md#magento-commerce-cloud) or [On-premises](install.md#on-premises) instances. These methods require the use of a Command Line Interface.

![New](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] supports a [sandbox account](onboard.md#enable-sandbox-testing) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue PAY-666 --> Merchants can [configure the Payment Services](settings.md) extension with basic payment behaviors, such as utilizing [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) switching between sandbox or production environments.

![New](../assets/new.svg)<!-- Issue PAY-780 --> Your shoppers can check out with [!DNL Payment Services] or via [manual order creation](create-order.md).

![New](../assets/new.svg)<!-- Issue PAY-1856 --> Comprehensive reporting, via [Order payment status](order-payment-status.md) and [Payouts reports](payouts.md), are available for [!DNL Payment Services] to give you a clear view of your store's orders and related payments.

![New](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] supports flexible tiered pricing, based on total processing volume, adapted to any merchant.

![New](../assets/new.svg)<!-- Issue PAY-1443 --> You can easily [customize the look and feel](payments-options.md) of PayPal smart buttons and credit card fields for the Payment Services extension.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 --> Using [incorrect Composer keys](https://support.magento.com/hc/en-us/articles/4406603542541) during installation of the extension prevents the user from [authenticating](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with the correct `MAGEID`.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] reports [may not synchronize immediately](https://support.magento.com/hc/en-us/articles/4406114741517).

![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 --> Your [PayPal sandbox account](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] cannot be verified  if you create that account during onboarding.
