---
title: Test and Validate
description: Testing and validation help ensure that [!DNL Payment Services] functions work as expected and provide the best payment options for your customers
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
---
# Test and Validate

Before you expose [!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] to your shoppers, it is a good idea to test in your sandbox environment _and_ in production. Testing and validation help ensure that [!DNL Payment Services] functions work as expected and provide the best payment options for your store and customers.

## Test in sandbox environment

Testing [!DNL Payment Services] in a sandbox environment is an important validation step, even though it is a simulated environment connected only to the PayPal sandbox, not to real banks and merchants.

1. Complete a successful checkout from your store, either with [Credit Card Fields](payments-options.md#credit-card-fields) or any of the [PayPal payment buttons](payments-options.md#paypal-smart-buttons). See [Testing credentials](#testing-credentials) for more information about using fake credit cards for testing.
1. Capture (when your payment action is [set to `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [refund](refunds.md), or [void](voids.md) the just-completed order. You can also simply [create an invoice](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} for an order, if your payment action is set to `Authorize` instead of `Authorize and Capture`.
1. Within 24-48 hours, view the transaction and other information in the [Payouts report](payouts.md).
1. See details of the order in the [Order payment status report](order-payment-status.md).

### Testing credentials

When testing and validating your sandbox you must use fake credit card numbers, so that you are not creating real charges to an existing credit card account.

Use PayPal's Credit Card Generator to [generate random credit card information](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) for testing.

To test Apple Pay in sandbox mode:

* Create an [Apple sandbox tester account](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), complete with fake credit card and billing information.
* [Register your sandbox domains](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal's sandbox payment processing is sometimes slow and the service can occasionally go down. This situation is not an indication of the speed and efficiency of live product payment processing.

## Test in production

It is highly recommended that you test [!DNL Payment Services] in production, with real credit cards and banks, before exposing this functionality to shoppers. Even though testing [!DNL Payment Services] in sandbox is important, testing in production is the most fool-proof method for ensuring [!DNL Payment Services] works as expected.

You can test [!DNL Payment Services] in production in one of two ways:

* Choose a time when you know that no orders will be placed by shoppers.
* Use a webstore which is temporarily inaccessible to shoppers, but is accessible to you for testing.

Complete your production testing with real credit cards and PayPal accounts, testing the entire lifecycle of a payment, including capture and refund. Completing the entire checkout and payment flow during testing gives you the clearest picture of how your [!DNL Payment Services] functionality will work when live shoppers are using it.

You should also verify the information that appears on the bank statements for the payment methods you use in production testing are correct and expected (including the description of your business).

To test Apple Pay in production mode, you must [register your production domains](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
