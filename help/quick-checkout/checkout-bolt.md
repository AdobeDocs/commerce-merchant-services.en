---
title: "Checkout flow of a Bolt user in Adobe Commerce"
description: Overview of the [!DNL Quick Checkout] flow for a Bolt user in Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
---
# Guest users

The guest checkout experience is different from the Adobe user experience. When a shopper enters an email address into checkout, the [!DNL Quick Checkout] validates it and finds an existing [!DNL Bolt] account.

## Registered [!DNL Bolt] account

If a [!DNL Bolt] account is found, shoppers continue with their [!DNL Quick Checkout] seamless checkout experience: 

1. Input the One-Time Password (OTP) sent to that [!DNL Bolt] account's email address or mobile, depending on [user's preferences in the [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

  ![OTP Pop-up](assets/pop-up.png)

1. Once logged in with your [!DNL Bolt] account, the details are automatically added:

   - Shipping information
   - Payment method

1. Place your order.

>[!TIP]
>
> The guest user places the order, and they can optionally register in Adobe Commerce.

## New [!DNL Bolt] account

If no [!DNL Bolt] account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and the shopper provides all necessary details to place order:

- Shipping and billing information
- Shipping method
- Review payment method
- A checkbox appears to register in [!DNL Bolt] for faster checkouts before placing the order. The shopper can agree to the terms and conditions to create their [!DNL Bolt] account.

   ![Remember [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- The guest user places the order, and they can optionally register in Adobe Commerce.
