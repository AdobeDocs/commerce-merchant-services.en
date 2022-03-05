---
title: Checkout flow
description: Overview of the [!DNL Express Checkout] flow in Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
---
# [!DNL Express Checkout] flow

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

This section provides an overview of the typical checkout experience using the [!DNL Express Checkout] for Adobe Commerce extension.

A successful [!DNL Express Checkout] flow consists of the following steps:

1. Open your storefront and add items in your cart.
1. Proceed to checkout.

  ![Checkout](../assets/proceed-checkout.png)

1. When prompted, enter an email address associated with a Bolt account.
1. Input the One-Time Password (OTP) sent to that Bolt account’s email address or phone number.
1. Once logged in with your Bolt account, checkout details are automatically filled in:

   - Shipping information
   - Payment method
   
   >[!NOTE]
   >
   > You can use your existing wallet information (address or credit card information) even if your checkout details are automatically filled in.

1. Place Order.

The [!DNL Express Checkout] is compatible with standard additional Adobe Commerce checkout options, such as [gift cards](https://docs.magento.com/user-guide/catalog/product-gift-card.html) or [discount codes](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] use cases

The [!DNL Express Checkout] allows for multiple use cases during a checkout flow:

- Guest user with a registered Bolt account.
- Guest user with a new Bolt account.
- An existing Adobe Commerce user with/without a registered Bolt account.

## Guest user checkout: How it works

Guest checkout experience is different from the logged-in experience. When a shopper enters an email address into checkout, the [!DNL Express Checkout] validates it to find an existing Bolt account.

### Registered Bolt account

If a Bolt account is found, shoppers continue with their [!DNL Express Checkout] seamless checkout experience: 

1. Input the One-Time Password (OTP) sent to that Bolt account’s email address or mobile, depending on user's preferences in the Bolt account.
1. Once logged in with your Bolt account, it fills the checkout details automatically:

   - Shipping information
   - Payment method

1. Place Order.

>[!TIP]
>
> Guest user places the order and can register in Adobe Commerce.

### New Bolt account

If no Bolt account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and shopper provides all necessary details to place order:

- Shipping and billing information
- Shipping method
- Review payment method
- A checkbox appears to register in Bolt for faster checkouts before placing the order. They can agree to the terms & conditions to create their Bolt account.

  ![Remember Bolt](../assets/checked-bolt.png)

- The guest user places the order and can register in Adobe Commerce.

## An existing Adobe Commerce user: How it works

An existing user can select existing details when user places an order with the [!DNL Express Checkout] for a faster checkout experience.

When a shopper enters an email address into checkout, the [!DNL Express Checkout] validates it to find an existing Bolt account.

### Registered Bolt account with an Adobe Commerce user

If a Bolt account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and shopper provides all necessary details and then places order:

- Shipping and billing information
- Shipping method
- Review payment method

Refer to the [troubleshooting](../express-checkout/shipping-details.md) topic for more information if you encounter problems when you place an order as an existing Adobe Commerce user.

>[!NOTE]
>
> If user has a Bolt account and email does not appear as registered in Adobe Commerce, it triggers the One-Time Password (OTP) login. See the [registered Bolt account](#registered-bolt-account) flow.

### New Bolt account

If no Bolt account is found, shoppers continue with their default Adobe Commerce checkout and shopper selects all necessary details from their saved information to place the order:

- Shipping and billing information
- Shipping method
- Review payment method
- A checkbox appears to register in Bolt for faster checkouts before placing the order. They can agree to the terms & conditions to create their Bolt account.

  ![Remember Bolt](../assets/checked-bolt.png)

## Get help

Contact Adobe Commerce Support for assistance and questions.
