---
title: Payment Options
description: Set the payment options to customize the methods available for your store customers.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
---
# Payment Options

With [!DNL Adobe Commerce] and [!DNL Magento Open Source] [!DNL Payment Services], you have multiple payment options available to you. You can configure these payment options through:

*  [Home settings](payments-home.md)
*  [Store configuration](configure-admin.md) (recommended for legacy payment options or a multistore setup)

There are different behaviors for each payment method depending on where you are in the checkout process:

*  Product page---The product page for an item
*  Mini cart---Available upon click of the cart icon when a product has been added to the cart
*  Shopping cart---Available upon click of _View and edit cart_ from the mini-cart
*  Checkout view---Available upon click of _Proceed to Checkout_ from mini-cart or shopping cart

>[!IMPORTANT]
>
>Payment Services onboarding must be completed before payments can be processed.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] provide a simple and secure checkout for credit card or debit card payment methods. When a shopper checks out using credit card fields, they enter their name, billing address, and credit or debit card information, to place their order. Their customer information is securely used during the purchase session to seamlessly guide them through the checkout flow.

Enable [credit card vaulting](#vaulting) for your stores to allow shoppers to vault (save) their credit card information for a fast checkout later.

You can configure [!UICONTROL Credit Card Fields] in the store configuration or the Payment Services Home. See [Settings](settings.md#credit-card-fields) for more information.

You can also change the layout, width, height, and outer styling of the credit card fields. See [PayPal documentation](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) for more information.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], which use PayPal to complete a purchase, stores your shopper's shipping address, billing addresses, and payment details for later use. Shoppers can use any payment method previously stored or offered by PayPal.

![[!DNL PayPal Smart Buttons] options](assets/buttons-md.png)

You can configure [!UICONTROL PayPal Smart Buttons] in the store configuration or the Payment Services Home.  See [Settings](settings.md#payment-buttons) for more information.

### [!DNL PayPal] button

Customers can check out with ease and confidence using the PayPal button.

The [!DNL PayPal] button is visible from the product page, mini-cart, shopping cart, and checkout views.

### [!DNL Venmo] button

Customers can check out using the [Venmo](https://venmo.com/) button.

The [!DNL Venmo] button is visible from the product page, mini-cart, shopping cart, and checkout views.

### [!DNL Apple Pay] button

Customers can use Touch ID on their devices to use [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), which utilizes credit and debit card payment credentials stored on their iOS or macOS device.

The [!DNL Apple Pay] button is visible from the product page, mini-cart, shopping cart, and checkout views.

   >[!NOTE]
   >
   > To use [!DNL Apple Pay] for your stores, complete [self-registration with [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Register your live domain_ section only) and [configure it for your stores in [!DNL Payment Services]](settings.md#payment-buttons).

### [!DNL Pay Later] button

Offer your customers short-term, interest-free payments, and other financing options so that they can buy now and pay later with the [!DNL Pay Later] button.

The [!DNL Pay Later] button is visible from the product page, mini-cart, shopping cart, and checkout views:

*  **When a customer selects a product between $30 and $600**, messaging under the PayPal and [!DNL Pay Later] buttons gives the customer more information about the [!DNL Pay in 4] payment option. Customers can click **Learn more** to learn about the "[!DNL Pay in 4]" option _or_ click the "Or see 6 months special financing" text in the popup to learn about and apply for the PayPal Credit option.
*  **When a customer selects a product or products exceeding $98.99**, messaging under the PayPal and [!DNL Pay Later] buttons gives customers more information about the PayPal Credit payment option. Customers can click **Learn more** to learn about and apply for the PayPal Credit option, _or_ click the "Or see Pay in 4" text in the popup to learn about the [!DNL Pay in 4] option.

   >[!NOTE]
   >
   >The amounts listed above are subject to change.

See [Settings](settings.md#payment-buttons) to learn how to disable/enable the [!DNL Pay Later] messaging.

There are two payment options with the [!DNL Pay Later] button:

*  **Pay in 4**---Customers can pay their order balance in four interest-free payments (every two weeks) after an initial down payment. See the [Pay in 4 documentation](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) for more information.
*  **PayPal Credit**---Customers can pay their order balance in full over six months, interest-free. See the [PayPal Credit documentation](https://www.paypal.com/us/webapps/mpp/paypal-credit) for more information.

### [!DNL Pay Now] button

The [!DNL Pay Now] button is visible in the PayPal popup window when a customer clicks a payment button on the payments screen.

If the final order amount is not yet known (such as when you do not yet have shipping address information) and the customer is in the process of checking out from the product page, mini-cart, or shopping cart, a _Continue_ button is available instead. When a customer clicks _Continue_, after they confirm their payment method, they are directed to an order review page to gather the needed details before completing checkout.

## Use only PayPal branded payment buttons

To quickly get your store into production mode you can configure _only_ PayPal branded payment buttons (VenMo, PayPal, etc.)---instead of also using the PayPal credit card payment option.

This allows you to:

*  Provide a variety of payment options for your customers without applying for credit card approval through PayPal.
*  Use your existing credit card provider for credit card payments, while also utilizing PayPal's other payment options.
*  Use PayPal's branded payment buttons in a region in which PayPal does not support credit cards as a payment option.

**To use _only_ branded payment buttons**, turn _Off_ the **[[!UICONTROL Show Credit and Debit card button]](settings.md#payment-buttons)** option in _Settings_.

**To use your existing credit card provider, and _not_ the PayPal credit card payment option**, turn _On_ the **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** option in _Settings_.

## Order recalculation

When a customer enters the checkout flow from the mini-cart, shopping cart, or product page, they are directed to an order review page where they can see the selected shipping address in a PayPal popup window. After the customer selects the shipping method, the order amount is recalculated appropriately and the customer can see shipping costs and taxes.

When a customer enters the checkout flow from the checkout page, the system is already aware of the shipping address and final calculated amount, and totals are appropriately represented.

Tax holidays, shipping costs, and sales tax can vary widely from location to location. After [!DNL Payment Services] receives the shipping address and rate, it quickly recalculates all applicable costs and display them appropriately during the last stages of checkout.

## Checkout from product page

When a customer checks out directly from the product page, using the PayPal or [!DNL Pay Later] buttons, only the item represented in the current product page is purchased. Items already residing in the customer's cart is not added to the checkout flow and is not purchased.

If the customer cancels the order, the item in the current product page is added to the customer's cart, joining any other items present in the cart. This function allows the customer to quickly purchase the item they are currently viewing, while also retaining any other items they added to their cart previously when browsing products.

When a customer enters the checkout flow from the product page, the checkout page is simplified---the view only shows order-related data and options.

## Credit card vaulting

Shoppers can vault---or "save"---their credit card information for future purchases on the website level (any store within the same merchant's account).

See [Credit card vaulting](vaulting.md) for more information.

## Security

See [PCI compliance](security.md#pci-compliance) for more information.
