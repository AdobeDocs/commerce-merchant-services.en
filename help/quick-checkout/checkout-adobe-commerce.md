---
title: "Checkout flow for an Adobe Commerce user"
description: "Overview of the [!DNL Quick Checkout] flow for an Adobe Commerce user."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
---
# An existing Adobe Commerce user: How it works

An existing Adobe Commerce user can select saved shipping and payment details when placing an order with the [!DNL Quick Checkout] for a faster checkout experience.

When a shopper enters their email address at checkout, the [!DNL Quick Checkout] validates it and finds an existing [!DNL Bolt] account.

## Registered user in both Adobe Commerce and [!DNL Bolt]

When a shopper is a registered user in both Adobe Commerce and [!DNL Bolt] networks, both networks are provided stored shipping and payment details.

If a [!DNL Bolt] account is found during checkout, shoppers can continue with their [!DNL Quick Checkout] seamless checkout experience:

1. Input the One-Time Password (OTP) sent to that [!DNL Bolt] account's email address or mobile, depending on [user's preferences in the [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

  ![OTP Pop-up](assets/new-logo-otp-email.png)

1. Once logged in with your [!DNL Bolt] account, the details are automatically added:

   - Shipping information
   - Payment method

1. Place your order.

>[!NOTE]
>
> The Bolt OTP pop-up only appears when the shopper is on the checkout page. The shopper can opt out from logging in to Bolt by closing that pop-up window.

If the shopper is logged in to Adobe Commerce prior to checkout, the [!DNL Bolt] OTP pop-up will not appear during checkout, but a message appears suggesting the shopper to log in to access their Bolt Wallet.

If you encounter issues when you place an order as an existing Adobe Commerce user, see the [Troubleshoot Quick Checkout issues](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) article in the Adobe Commerce Help Center.

## Automatic login

The Automatic Login component detects when a shopper has an active Bolt session and automatically logs the shopper in. This skips the account detection and one-time passcode (OTP) steps because the shopper completed them in a previous session.

It is possible to configure an automatic login for [!DNL Quick Checkout] users. You can enable a configuration to automatically login a user during checkout.

1. On the _Admin_ sidebar, navigate to **Stores** > **Configuration** > **Checkout** to access the general Checkout Admin config page.
1. In the _Service Settings_ section for [!DNL Quick Checkout], provide all details required to setup automatic login.

See [[!DNL Quick Checkout] configure service settings](../quick-checkout/onboarding.md#configure-service-settings) topic for more information.

>[!NOTE]
>
> First time login when **automatic login** is enabled requires consent from the user to authorize it by accepting a pop-up window.

## New [!DNL Bolt] account

If no [!DNL Bolt] account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and the shopper selects all necessary details from their saved information to place the order:

- Shipping and billing information
- Shipping method
- Review payment method
- The option to register in [!DNL Bolt] for faster checkouts before placing the order appears. The shopper can agree to the terms and conditions to create their [!DNL Bolt] account.

  ![Remember [!DNL Bolt]](assets/checkbox-remember-bolt.png)
