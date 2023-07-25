---
title: Signifyd Fraud Protection
description: Enable automated fraud protection for [!DNL Payment Services] with Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
---

# Signifyd fraud protection

You can enable automated fraud protection for [!DNL Payment Services] with the [Signifyd extension](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce supports Signifyd versions 5.4.0 and newer. [!DNL Payment Services] supports pre-auth and post-auth Signifyd flows.

## Limitations

Currently, the following limitations apply to Signifyd with [!DNL Payment Services]:

* Signifyd supports only [credit card fields](../payment-services/payments-options.md#credit-card-fields) (not PayPal payment buttons or Apple Pay). You may configure Signifyd to consume orders placed with PayPal payment buttons or Apple Pay, but we cannot guarantee that Signifyd is able to identify fraud in those payment options.
* Signifyd does not support orders placed in the Admin by a merchant for a shopper.
* Signifyd does not support orders placed with [vaulted credit cards](../payment-services/vaulting.md).

## Onboarding

You must communicate directly with Signifyd to onboard the extension for use with [!DNL Payment Services]---there is no [!DNL Payment Services] configuration needed. You can configure the Signifyd extension in the Admin once installed. Any support related to this extension will be managed by Signifyd.

When onboarding with Signifyd you must:

* Contact Signifyd to set up a new account.
* [Allowlist credit card fields](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) to ensure Signifyd does not trigger for other payment options it does not currently support.
* Confirm with Signifyd that PayPal will not reject orders, via the merchant's fraud protection setting in Paypal, that could be approved by Signifyd.
* Enable the Signifyd extension to be compatible with [!DNL Payment Services]:
  * When using [!DNL Payment Services] in _Live_ mode, Signifyd must be in Test mode.
  * When using [!DNL Payment Services] in _Sandbox_ mode, Signifyd must be in Production mode.

### Configuration

Because Signifyd takes some action on your orders, it is necessary to configure the extension to behave appropriately based on the payment action you set for [!DNL Payment Services].

To configure order behavior in Signifyd (once installed) in the Admin:

1. On the _Admin_ sidebar, go to **[!UICONTROL Stores]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Click **[!UICONTROL Order Workflow]**.
1. For _Approved Guarantees_:
   * If your [!DNL Payment Services] [payment action](../payment-services/production.md#set-payment-services-as-payment-method) is set to `Authorize and Capture`, select either **[!UICONTROL Do nothing]** or **[!UICONTROL Unhold order]**.
1. For _Declined Guarantees_:
   * If your [!DNL Payment Services] [payment action](../payment-services/production.md#set-payment-services-as-payment-method) is set to `Authorize and Capture`, select either **[!UICONTROL Do nothing]** or **[!UICONTROL Create credit memo]**.
   * If your [!DNL Payment Services] [payment action](../payment-services/production.md#set-payment-services-as-payment-method) is set to `Authorize`, select either **[!UICONTROL Do nothing]** or **[!UICONTROL Cancel order]**.

   See [Signifyd documentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works) for more information.
