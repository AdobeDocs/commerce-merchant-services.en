---
title: '[!DNL Express Checkout] for Adobe Commerce Developer Information'
description: '[!DNL Express Checkout] developer information.'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
---
# [!DNL Express Checkout] developer information

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

This topic contains information for developers who work closely with the Adobe Commerce and Magento Open Source code and want to learn detailed information about the [!DNL Express Checkout] extension.

## Extension points

Use extension points to customize the [!DNL Express Checkout].

By using extension points, you can make customizations without actually altering the core components in the application code.

### Shipping details step

An extension point can be used to customize the automated step navigation after logging in with [!DNL Bolt].

Once a shopper logs in with [!DNL Bolt], all valid information is prefilled and redirected to the payment details step to place the order. See the [checkout flow](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) topic for more information.

This extension point allows to prevent navigation to a payment step and can be useful in case there are extensions that require a shopper to perform additional actions on the shipping step. See an example below on how you can use the extension point with a mixin:

1. Register a new mixin in the `require-config.js` file located in `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Extend the model in the `can-navigate-to-payment.js` file located in `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> This is an example for a shopper in Germany (DE) that wants to stay on the Shipping details step.

Check [[!DNL Bolt] developer help](https://help.bolt.com/developers/) for more information on [!DNL Bolt] for developers.
