---
title: Signifyd Fraud Protection
description: Enable automated fraud protection for [!DNL Payment Services] with Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
---
# Signifyd fraud protection

You can enable automated fraud protection for [!DNL Payment Services] with the [Signifyd extension](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce supports Signifyd versions 5.4.0 and newer. [!DNL Payment Services] supports pre-auth and post-auth Signifyd flows.

The Signifyd/[!DNL Payment Services] integration provides coverage for credit cards, debit cards, vaulted cards, checkout through the Admin, and PayPal and Apple Pay payment methods. While some details of the transactions are not shared between Payment Services and Signifyd, Signifyd provides comprehensive risk coverage for all payment methods, ensuring the utmost in protection.

See [Signifyd documentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) to learn about installing and configuring the extension.

## Onboarding

You must communicate directly with Signifyd to onboard the extension for use with [!DNL Payment Services]---there is no [!DNL Payment Services] configuration needed. You can configure the Signifyd extension in the Admin once installed. Any support related to this extension will be managed by Signifyd.

When onboarding with Signifyd you must:

1. Contact Signifyd to set up a new account.
1. By default, Signifyd is [allowlisted](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) to ensure Signifyd does not trigger for other payment options it does not currently support. If you want to ban a particular payment method, you must make changes.
1. Confirm with Signifyd that PayPal will not reject orders, via the merchant's fraud protection setting in Paypal, that could be approved by Signifyd.
1. Enable the Signifyd extension to be compatible with [!DNL Payment Services]:
     * When using [!DNL Payment Services] in _Live_ mode, Signifyd must be in Production mode.
     * When using [!DNL Payment Services] in _Sandbox_ mode, Signifyd must be in Test mode.

## Configuration

Because Signifyd takes some action on your orders, it is necessary to configure the extension to behave appropriately based on the payment action you set for [!DNL Payment Services].

These configuration options are not compatible with Payment Services and the Signifyd integration:

* When [!DNL Payment Services] is configured with the `Authorize` payment action _and_ Signifyd is in `PostAuth` mode with the _[!UICONTROL Decline Guarantees]_ option set to **Create credit memo**.

   Reason: [!DNL Payment Services] creates an authorization transaction that Signify then attempts to refund.


* [!DNL Payment Services] is configured with the `Authorize and Capture` payment action _and_ Signifyd is in `PostAuth` mode with the _[!UICONTROL Decline Guarantees]_ option set to **Cancel order**.

   Reason: [!DNL Payment Services] creates a capture transaction that Signifyd then attempts to void.


See Signifyd documentation for information about [configuring the extension](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

See Signifyd documentation to [learn more about the order workflows](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
