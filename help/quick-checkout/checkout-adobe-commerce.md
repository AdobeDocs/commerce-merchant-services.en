---
title: Checkout flow
description: Overview of the [!DNL Quick Checkout] flow for an Adobe Commerce user.
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
---
# An existing Adobe Commerce user: How it works

An existing Adobe Commerce user can select saved shipping and payment details when placing an order with the [!DNL Quick Checkout] for a faster checkout experience.

When a shopper enters their email address at checkout, the [!DNL Quick Checkout] validates it and finds an existing [!DNL Bolt] account.

## Registered [!DNL Bolt] account with an Adobe Commerce user

If a [!DNL Bolt] account is found, shoppers continue with their [!DNL Quick Checkout] seamless checkout experience:

1. Input the One-Time Password (OTP) sent to that [!DNL Bolt] account’s email address or mobile, depending on [user's preferences in the [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Once logged in with your [!DNL Bolt] account, the details are automatically added:

   - Shipping information
   - Payment method

1. Place your order.

If you encounter issues when you place an order as an existing Adobe Commerce user, see the [Troubleshoot Quick Checkout issues](https://support.magento.com/hc/en-us/articles/6909450342541) article in the Adobe Commerce Help Center.

## New [!DNL Bolt] account

If no [!DNL Bolt] account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and the shopper selects all necessary details from their saved information to place the order:

- Shipping and billing information
- Shipping method
- Review payment method
- The option to register in [!DNL Bolt] for faster checkouts before placing the order appears. The shopper can agree to the terms and conditions to create their [!DNL Bolt] account.

  ![Remember [!DNL Bolt]](assets/checked-bolt.png)
