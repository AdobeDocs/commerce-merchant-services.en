---
title: "Testing the [!DNL Quick Checkout] for Adobe Commerce extension"
description: "Testing and validating ensures that the [!DNL Quick Checkout] extension works as expected."
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
feature: Checkout, Services
---

# Test the [!DNL Quick Checkout] extension

Before you expose the [!DNL Quick Checkout] for Adobe Commerce extension to your shoppers, it is recommended to test in a sandbox environment and in your production environment. Testing and validation helps ensure that the [!DNL Quick Checkout] works as expected and provides a seamless checkout experience for your store and customers.

Before you configure the [!DNL Quick Checkout] in your Adobe Commerce Admin it is required to create  [production](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} merchant accounts in [!DNL Bolt].

## Testing in sandbox

Testing the [!DNL Quick Checkout] in a sandbox environment is a very important validation step, even though it is a simulated environment connected only to the [!DNL Bolt] sandbox account, not to real banks or merchants.

### Using sandbox account

When you test and validate your sandbox you must use a fake credit card number and a [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} merchant account in [!DNL Bolt], so that you are not creating real charges to an existing credit card account.

## Testing in production

>[!NOTE]
>
> It is highly recommended that you test the [!DNL Quick Checkout] in a production environment, with real credit cards and banks, before exposing the extension to shoppers. Even though testing in sandbox is important, testing in production is the most fool-proof method for ensuring it works as expected.

Test your production environment in one of these two recommended ways:

- Choose a time when you know that no orders will be placed by shoppers.
- Use a webstore which is temporarily inaccessible to shoppers, but is accessible to you for testing.

Complete your production testing with real credit cards and [!DNL Bolt] production accounts, testing the entire lifecycle of a checkout. When you complete the entire checkout flow during testing, it gives you a clear picture of how your functionality works when live shoppers use it.

You should also verify the information that appears on the bank statements for the payment methods you use in production testing are correct and expected (including the description of your business).

## How to test the [!DNL Quick Checkout] extension

Complete a successful checkout from your store:

1. Go to your storefront and place desired items in your cart.
1. Proceed to checkout.
1. Enter an email address that is associated with a [!DNL Bolt] account when prompted.
1. Input the one-time Password (OTP) sent to the account's email address.
1. Select the environment dashboard:

   - Sandbox
   - Production

1. Place the order.

Once an order is placed, you can view details of your orders in your _Orders grid_ view:

1. Navigate to _Sales_ > _Orders_.
1. See list of all placed orders.

See the [Orders](https://docs.magento.com/user-guide/sales/orders.html) topic for more information about your _Orders grid_ view.
