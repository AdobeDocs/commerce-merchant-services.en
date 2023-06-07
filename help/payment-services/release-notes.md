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

+++Hosted service updates

_January 25, 2023_

![Known issue](../assets/bug.svg)<!-- Issue PAY-4102 --> New installations of Payment Services are unable to configure Commerce Services, rendering Payment Services inoperable. To fix this issue, update your Payment Services extension to version 1.5.3.

_September 12, 2022_

![New](../assets/new.svg)<!-- Issue PAY-3705 --> The `increment_id` is now available for use in reconciling payouts in external ERP systems. It is propagated to the [`custom_id` _and_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visible in both the PayPal webhook and the merchant activity detail for a payout.

_August 31, 2022_

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3629 --> When a new merchant accesses the Payment Services Home for the first time, the page now loads immediately to display the content instead of requiring a page refresh.

_August 9, 2021_

![New](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay is now available as a PayPal Smart Button. This [payment option](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) enables customers to use the Touch ID feature on their iOS or macOS device to select Apple Pay. Apple Pay processes the payment using the credit and debit card payment credentials stored on the device.

_June 28, 2021_

![New](../assets/new.svg)<!-- Issue PAY-1720 --> Disputes for store orders are now available in [the Order payment status report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). You can take action on disputes by navigating directly to the PayPal Resolution Center from [!DNL Payment Services].

![New](../assets/new.svg)<!-- Issue PAY-2854 --> User experience improvements from [!DNL Payment Services] Home include the ability to modify a configuration at the current inheritance level and improvements to the display of the header and navigation.

![New](../assets/new.svg)<!-- Issue PAY-2854 --> You can now see warnings when you switch from sandbox mode to production mode and when you attempt to navigate away from a view with updates that have not been saved.

![New](../assets/new.svg)<!-- Issue PAY-2761 --> You can now customize the data that displays in the [Order payment status report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) and the [Payouts report](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) by showing or hiding columns using the Column settings control.

+++

## v2.1.0

_June 9, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg)<!-- Issue xxx --> Added support for Adobe Commerce 2.4.7-beta1.

![New](../assets/new.svg)<!-- Issue PAY-4296 --> Added [expanded resources for Admin roles](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) to ensure Admin users can create and manage orders for customers and can see Payment Services in the Sales menu.

![New](../assets/new.svg)<!-- Issue PAY-4236 --> Added [auto-voiding for orders that incur errors during checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![New](../assets/new.svg)<!-- Issue PAY-4183 --> Created functionality to [show the credit/debit card payment option button](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) on the checkout page.

![New](../assets/new.svg)<!-- Issue PAY-4288 --> Now, merchants can [configure _only_ PayPal payment buttons](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)---and _not_ use the PayPal credit card payment option---to provide a variety of payment options without applying for PayPal credit card approval.

![New](../assets/new.svg)<!-- Issue PAY-4050 --> Added a [data visualization view](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), which appears on the Payment Service Home, for the Order payment status report.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-4486--> Previously, the PayPal PayLater button did not appear in checkout for UK merchants. That issue is resolved.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-4485--> Report data visualization views are now appearing on Payment Services Home when Payment Services is disabled.

## v2.0.0

_March 10, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg)<!-- Issue PAY-4152 --> Added support for PHP 8.2 and Adobe Commerce 2.4.6. Not compatible with PHP 7.x.

## v1.6.1

_March 10, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0-2.4.5-p2

![Fix](../assets/fix.svg)<!-- Issue PAY-4226 --> Fixed an issue that prevented new Payment Services merchants from using checkout in the Admin. Payment Services was previously using the Commerce customer ID, which does not exist for new customers.

![Fix](../assets/fix.svg)<!-- Issue PAY-4205 --> Fixed an issue that caused the specified shipping address state to be replaced by the state in the default tax settings during checkout using the [PayPal option](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Now, customers can have their orders shipped to a state other than the one configured as the default in the merchant's tax settings.

![Fix](../assets/fix.svg)<!-- Issue PAY-4202 --> Fixed an issue preventing customers from using card vaulting to complete a purchase or delete a vaulted payment method for a store [using the `Authorize and Capture` payment action](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Previously, a "Provider Vault ID not found" error appeared when the customer attempted to use or modify their vaulted credit cards.

## v1.6.0

_February 17, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-3540 --> Added [PCI 3DS compliance feature for merchants transacting in the European Union (EU) and Britain](security.md#3ds). This additional layer of security, which requires buyers to authenticate with their credit card issuer, helps prevent online fraud and is required as part of European Union (EU) compliance regulations.

![New](../assets/new.svg)<!-- Issue PAY-3609 --> Added the ability to [enable card vaulting in the Admin](vaulting.md#use-vaulting-in-the-admin). This allows merchants to create an order for customers in the Admin using their vaulted payment methods.

## v1.5.4

_January 29, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-4110 --> Fixed an issue that prevented buyers from placing an order using smart buttons on the product page, mini cart, and cart. Buyers can now complete orders successfully.

## v1.5.3

_January 25, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-4102 --> Released a fix to a backward incompatible known issue. This release locks the service ID extension version to the latest stable version, which reenables new Payment Services installations to configure Commerce Services.

## v1.5.2

_December 22, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3992 --> Improved invoicing in Payment Services when a payment method is declined.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3999 --> Payment Services now correctly displays PayPal smart buttons for merchants using [Fire Checkout's](https://marketplace.magento.com/swissup-firecheckout.html){target=_blank} custom template for the checkout page. Previously, the minicart intermittently displayed the buttons.

## v1.5.1

_November 23, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-3923 --> Payment Services now includes the version number in the user agent header for requests to be able to track, filter or deprecate unused endpoints.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3968 --> Payment Services now correctly displays order data when an order is placed from the product page using smart buttons.

## v1.5.0

_November 18, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-3880 --> A shopper can now [vault (save) their credit card information during checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) to use in a later purchase for the same or another store within the same merchant account.

![New](../assets/new.svg)<!-- Issue PAY-3950 --> Merchants can now enable the [Instant Purchase Commerce feature](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) for their stores so that shoppers can (use [vaulted credit card information](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) to expedite checkout.

## v1.4.1

_October 14, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Fix](../assets/fix.svg)<!-- Issue PAY-3766 --> When a customer's payment method is declined, the visible error message is more descriptive. It advises the customer to re-enter payment information and try again, try another payment method, or to contact their bank about the declined the transaction.

## v1.4.0

_September 30, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-784 --> Payment Services now includes the ability to set up a merchant account to [use multiple PayPal business accounts](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). This enables the merchant to operate your stores in multiple countries using different currencies, or to use Adobe Commerce for a portion of your business.

![New](../assets/new.svg)<!-- Issue PAY-3231 --> Merchants can [add a [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) to websites or individual store views configuration that show on customer transaction bank statements to delineate brands, stores, or product lines.

![New](../assets/new.svg)<!-- Issue PAY-3707 --> [Enable or disable credit card fields and PayPal smart buttons](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) for checkout in Payment Services settings.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3546 --> When a customer clicks **[!UICONTROL Edit cart]**, the page redirects to the cart page and shows the updated items instead of showing an empty cart.

## v1.3.1

_September 6, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3663 --> Now, when a merchant's store is capturing an order authorized with a non-global currency, the capture process completes and no error is shown.

## v1.3.0

_August 9, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-XX --> General availability release---[!DNL Payment Services] is now [compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay is now compatible with the Safari browser v15.5 on mobile and desktop.

## v1.2.0

_June 29, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![Known issue](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay is incompatible with the Safari browser v15.5 on mobile and desktop. When using Safari version 15.5, you are not able to complete checkout with Apple Pay.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3264 --> Previously, when a logged-in user selected a different billing/shipping address other than the default address for their account, checkout failed. We fixed this issue, and now the selected billing/shipping address is sent (instead of the default saved address) and checkout is completed successfully.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3314 --> If you disable PayPal smart buttons for checkout, no errors are shown.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3330 --> Payments no longer fail during checkout when a guest user enters a phone number that includes dashes.

![Fixed issue](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> When Commerce Services credentials are invalid, the [!DNL Payment Services] Home will now appear in the Admin. A credentials error appears to alert you that your credentials are invalid.

![Known issue](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] is currently incompatible with `commerce-data-export` v101.20 and higher, which renders it incompatible with the [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_March 31, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

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

![Known issue](../assets/bug.svg)<!-- Issue PAY-2842 --> Test credit card transactions [may fail with PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) when processing payments in a sandbox environment.

## v1.0.0

_November 29, 2021_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.0 and newer

![New](../assets/new.svg)<!-- Issue PAY-2127 --> General availability release---[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) is now compatible with [!DNL Adobe Commerce] and [!DNL Magento Open Source] versions 2.4.0 to 2.4.3-p1.

![New](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] extension for [!DNL Adobe Commerce] and [!DNL Magento Open Source] can be installed either for [[!DNL Adobe Commerce] on cloud infrastructure](install.md#adobe-commerce-on-cloud-infrastructure) or [On-premises](install.md#on-premises) instances. These methods require the use of a Command Line Interface.

![New](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] supports a [sandbox account](sandbox.md) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue PAY-666 --> Merchants can [configure the Payment Services](settings.md) extension with basic payment behaviors, such as utilizing [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) switching between sandbox or production environments.

![New](../assets/new.svg)<!-- Issue PAY-780 --> Your shoppers can check out with [!DNL Payment Services] or via [manual order creation](create-order.md).

![New](../assets/new.svg)<!-- Issue PAY-1856 --> Comprehensive reporting, via [Order payment status](order-payment-status.md) and [Payouts reports](payouts.md), are available for [!DNL Payment Services] to give you a clear view of your store's orders and related payments.

![New](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] supports flexible tiered pricing, based on total processing volume, adapted to any merchant.

![New](../assets/new.svg)<!-- Issue PAY-1443 --> You can easily [customize the look and feel](payments-options.md) of PayPal smart buttons and credit card fields for the [!DNL Payment Services] extension.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 --> Using [incorrect Composer keys](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) during installation of the extension prevents the user from [authenticating](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with the correct `MAGEID`.

![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] reports [may not synchronize immediately](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 --> Your [PayPal sandbox account](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) for [!DNL Payment Services] cannot be verified  if you create that account during onboarding.
