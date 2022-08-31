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

For feature changes and fixes released outside of the regular versioned feature release, see the Hosted service updates section(s).

See [Upcoming Releases](https://devdocs.magento.com/release/) to learn about release schedules and support.

See [Availability](https://devdocs.magento.com/release/availability.html) in the developer documentation to learn about product compatibility.

## Hosted service updates

These release notes describe feature changes and fixes that occurred and were released outside of the regular versioned feature releases for the hosted service.

_August 31, 2022_
![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3629 --> When a new merchant accesses the Payment Services Home for the first time, it now immediately loads instead of requiring a page reload to show content.

_August 9, 2021_
![New](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay is now available as a PayPal Smart Button. This [payment option](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) enables customers to use Touch ID on their devices to use Apple Pay, which uses credit and debit card payment credentials stored on their iOS or macOS devices.

_June 28, 2021_
![New](../assets/new.svg)<!-- Issue PAY-1720 --> Disputes for store orders are now available in [the Order payment status report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). You can navigate directly to the PayPal Resolution Center from [!DNL Payment Services] to take action on disputes.

![New](../assets/new.svg)<!-- Issue PAY-2854 --> User experience improvements from [!DNL Payment Services] Home include the ability to modify a configuration at the current inheritance level and improvements to display of the header and navigation.

![New](../assets/new.svg)<!-- Issue PAY-2854 --> You can now see warnings when you switch from sandbox mode to production mode and when you attempt to navigate away from a view with updates that have not been saved.

![New](../assets/new.svg)<!-- Issue PAY-2761 --> You can now customize the data that displays in the [Order payment status report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) and the [Payouts report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) by showing or hiding columns using the Column settings control.

## v1.3.0

_August 9, 2022_

![New](../assets/new.svg)<!-- Issue PAY-XX --> General availability release---[!DNL Payment Services] is now [compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay is now compatible with the Safari browser v15.5 on mobile and desktop.

## v1.2.0

_June 29, 2022_

![Known issue](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay is incompatible with the Safari browser v15.5 on mobile and desktop. When using Safari version 15.5, you are not able to complete checkout with Apple Pay.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3264 --> Previously, when a logged-in user selected a different billing/shipping address other than the default address for their account, checkout failed. We fixed this issue, and now the selected billing/shipping address is sent (instead of the default saved address) and checkout is completed successfully.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3314 --> If you disable PayPal smart buttons for checkout, no errors are shown.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3330 --> Payments no longer fail during checkout when a guest user enters a phone number that includes dashes.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> When Commerce Services credentials are invalid, the [!DNL Payment Services] Home will now appear in the Admin. A credentials error appears to alert you that your credentials are invalid.

![Known issue](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] is currently incompatible with `commerce-data-export` v101.20 and higher, which renders it incompatible with the [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

### Hosted service updates

These release notes describe feature changes and fixes that occurred and were released outside of the regular versioned feature releases, between the v1.2.0 release and the previous 1.1.0 release for the hosted service. _These changes may also be applicable to earlier release versions._



## v1.1.0

_March 31, 2022_

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release---[!DNL Payment Services] is now [compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![New](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] extension for [!DNL Adobe Commerce] and [!DNL Magento Open Source] is now available for Canadian merchants. Merchants can view payments configuration in either [French](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) or [English](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![New](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Canadian dollars (CAD)](overview.md#accepted-credit-cards-and-currencies) for credit cards and PayPal transactions.

![New](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants can [onboard [!DNL Payment Services]](onboard.md) extension in English or French languages.

![New](../assets/new.svg)<!-- Issue PAY-2678 --> Merchants can now view financial reports, both the [Order payment status](order-payment-status.md) and [Payouts reports](payouts.md), in Canadian dollars (CAD).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] is now compatible with [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3017 --> Improved Sandbox mode alert to display proper alerts with multiple stores.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2742 --> You can now enable and disable available payment methods, such as Venmo, at the store view level. Previously, you could configure payment methods per website only.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2277 --> You can now selectively [enable or disable individual PayPal smart buttons](settings.md#payment-buttons).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-2561 --> Previously removed products do not appear in the cart on the _Review Order_ page.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2842 --> Test credit card transactions [may fail with PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) when processing payments in a sandbox environment.

## v1.0.0

_November 29, 2021_

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release---[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) is now compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.3-p1.

![New](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] extension for [!DNL Adobe Commerce] and [!DNL Magento Open Source] can be installed either for [[!DNL Adobe Commerce] on cloud infrastructure](install.md#adobe-commerce-on-cloud-infrastructure) or [On-premises](install.md#on-premises) instances. These methods require the use of a Command Line Interface.

![New](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] supports a [sandbox account](sandbox.md) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue PAY-666 --> Merchants can [configure the Payment Services](settings.md) extension with basic payment behaviors, such as utilizing [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) switching between sandbox or production environments.

![New](../assets/new.svg)<!-- Issue PAY-780 --> Your shoppers can check out with [!DNL Payment Services] or via [manual order creation](create-order.md).

![New](../assets/new.svg)<!-- Issue PAY-1856 --> Comprehensive reporting, via [Order payment status](order-payment-status.md) and [Payouts reports](payouts.md), are available for [!DNL Payment Services] to give you a clear view of your store's orders and related payments.

![New](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] supports flexible tiered pricing, based on total processing volume, adapted to any merchant.

![New](../assets/new.svg)<!-- Issue PAY-1443 --> You can easily [customize the look and feel](payments-options.md) of PayPal smart buttons and credit card fields for the [!DNL Payment Services] extension.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 --> Using [incorrect Composer keys](https://support.magento.com/hc/en-us/articles/4406603542541) during installation of the extension prevents the user from [authenticating](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with the correct `MAGEID`.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] reports [may not synchronize immediately](https://support.magento.com/hc/en-us/articles/4406114741517).

![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 --> Your [PayPal sandbox account](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] cannot be verified  if you create that account during onboarding.
