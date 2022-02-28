---
title: Testing the [!DNL Express Checkout] for Adobe Commerce extension
description: Testing and validating ensures that the [!DNL Express Checkout] extension works as expected.
---

# Testing the [!DNL Express Checkout] for Adobe Commerce extension

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

Before you expose the [!DNL Express Checkout] for Adobe Commerce extension to your shoppers, it is recommended to test in a sandbox environment and in your production environment. Testing and validation helps ensure that the [!DNL Express Checkout] works as expected and provides a seamless checkout experience for your store and customers.

Before you configure the [!DNL Express Checkout] in your Adobe Commerce Admin it is required to create a [production](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} merchant account in Bolt.

## Testing in sandbox

Testing the [!DNL Express Checkout] in a sandbox environment is a very important validation step, even though it is a simulated environment connected only to the Bolt sandbox account, not to real banks or merchants.

### Using sandbox account

When you test and validate your sandbox you must use a fake credit card number and a [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} merchant account in Bolt, so that you are not creating real charges to an existing credit card account.

## Testing in production

>[!NOTE]
>
> It is highly recommended that you test the [!DNL Express Checkout] in a production environment, with real credit cards and banks, before exposing the extension to shoppers. Even though testing in sandbox is important, testing in production is the most fool-proof method for ensuring it works as expected.

Recommended to test in production in one of two ways:

- Choose a time when you know that no orders will be placed by shoppers.
- Use a webstore which is temporarily inaccessible to shoppers, but is accessible to you for testing.

Complete your production testing with real credit cards and Bolt production accounts, testing the entire lifecycle of a checkout. When you complete the entire checkout flow during testing gives you a clear picture of how your functionality works when live shoppers are use it.

You should also verify the information that appears on the bank statements for the payment methods you use in production testing are correct and expected (including the description of your business).

## How to test the [!DNL Express Checkout] extension

Complete a successful checkout from your store following these steps:

1. Go to your storefront and place desired items in your cart.
1. Proceed to checkout.
1. Enter an email address that is associated with a Bolt Account when prompted.
1. Input the One-Time Password (OTP) sent to the account’s email address.
1. Select the environment dashboard:

   - Sandbox
   - Production

1. Place Order.

Once an order is placed, you can view details of your orders in your _Orders grid_ view:

1. Navigate to _Sales_ > _Orders_.
1. See list of all placed orders.

See the [orders](https://docs.magento.com/user-guide/sales/orders.html) topic for more information about your _Orders grid_ view.
