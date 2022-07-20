---
title: Payment Services Settings
description: After installation, you can configure [!DNL Payment Services] in the Home.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
---
# Settings

You can customize [!DNL Payment Services] to your needs with helpful settings in the [!DNL Payment Services] Home.

To configure [!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] click **[!UICONTROL Settings]**. These configuration options apply only to the environment that is set in the _[!UICONTROL Payment mode]_ field in _[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> For multi-store or legacy configuration, refer to the [Configure in the Admin](configure-admin.md) topic.

## Enable Payment Services

You can enable [!DNL Payment Services] for your website, and enable either sandbox testing or live payments, in the [!UICONTROL General] section.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Home view](assets/payment-services-menu-small.png)

1. Click **[!UICONTROL Settings]**. See [Introduction to [!DNL Payment Services] Home](payments-home.md) for more information.

   The _[!UICONTROL General]_ section includes settings used to enable [!DNL Payment Services] as the payment method.

1. To enable [!DNL Payment Services] as the payment method for your store, in the _[!UICONTROL General]_ section, toggle (**[!UICONTROL Enable Payment Services as payment method]**) to `Yes`.

1. If you are still testing [!DNL Payment Services] for your store, set **Payment mode** to `Sandbox`. If you are ready to enable live payments, set it to `Production`.

   >[!NOTE]
   >
   >Your _[!UICONTROL Sandbox Merchant ID]_ and _[!UICONTROL Production Merchant ID]_ are auto-generated and present in their respectable fields when you finish onboarding for the sandbox and/or production.

1. Select the store view, in the **[!UICONTROL Scope]** dropdown menu, for which you want to enable a payment method.
1. To change the default settings for payment functions and storefront display, set the additional options as needed:

   - [Credit card fields](#credit-card-fields)
   - [Payment buttons](#payment-buttons)
   - [Button style](#button-style)

1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### Configuration options

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL Enable] | website | Enable or disable [!DNL Payment Services] for your website. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | store view | Set the method, or environment, for your store. Options: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | store view | Your sandbox merchant ID, which is auto-generated during sandbox onboarding. |
| [!UICONTROL Production Merchant ID] | store view | Your production merchant ID, which is auto-generated during sandbox onboarding. |

### Credit card fields

The _[!UICONTROL Credit Card Fields]_ settings provide a simple and secure checkout option for credit card or debit card payment methods.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

1. To change the name of the payment method displayed during checkout, edit the value in the **[!UICONTROL Checkout title]** field.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), toggle **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. To enable debug mode, toggle the **[!UICONTROL Debug Mode]** selector.
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

#### Configuration options

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL Title] | store view | Add the text for display as the title for this payment option in the Payment Method view during checkout. Options: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | The [payment action](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} for the specified payment method. Options: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Enable or disable Debug Mode. Options: [!UICONTROL Yes] / [!UICONTROL No] |

### Payment buttons

The [!DNL PayPal Smart Buttons] payment options provide a simple, fast, and secure checkout process for your customer. See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

You can enable and configure the PayPal smart buttons payment options:

1. To change the name of the payment method as shown during checkout, edit the value in the **[!UICONTROL Checkout Title]** field.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), toggle **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. Use the toggle selectors to enable or disable [!DNL PayPal smart button] display features:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple Pay is enabled by default for sandbox mode, but you also [must have an Apple Developer Account](test-validate.md#test-in-sandbox-environment) (complete with fake credit card and billing information) to test it. When you are ready to use Apple Pay in production mode, after completing any [testing and validation](test-validate.md), contact sales to enable it for your live store(s).

1. To enable debug mode, toggle the **[!UICONTROL Debug Mode]** selector.  
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

#### Configuration options

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL Title] | store view | Add the text to be displayed as the title for this payment option in the Payment Method view during checkout. Options: text field |
| [!UICONTROL Payment Action] | website | The [payment action](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} for the specified payment method. Options: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | store view | Enable or disable [!DNL PayPal Smart Buttons] on the product detail page. Options: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | store view | Enable or disable [!DNL PayPal Smart Buttons] in the mini cart preview. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | store view | Enable or disable [!DNL PayPal Smart Buttons] on the cart page. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | store view | Enable or disable pay later payment option appearance where payment buttons are displayed. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | website | Enable or disable the Pay Later messaging in the shopping cart, product page, mini-cart, and during the checkout flow. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | store view | Enable or disable the Venmo payment option where payment buttons are displayed. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | store view | Enable or disable the Apple Pay payment option where payment buttons are displayed. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | website | Enable or disable Debug Mode. Options: [!UICONTROL Yes] / [!UICONTROL No] |

#### Button style

You can also configure the _[!UICONTROL Button style]_ options of the PayPal smart buttons:

1. To change the **[!UICONTROL Layout]**, select `Vertical` or `Horizontal`.

   >[!NOTE]
   >
   > If the button style is configured as `Horizontal` and your store is configured to show multiple PayPal smart buttons, you may only see two buttons displayed on the product page, checkout page, and mini cart, and one button displayed in the cart.

1. To enable the tagline in a horizontal layout, toggle the **[!UICONTROL Show tagline]** selector.
1. To modify the **[!UICONTROL Color]**, select the desired color option.
1. To modify the **[!UICONTROL Shape]**, select `Pill` or `Rect`.
1. To enable button height selector, toggle the **[!UICONTROL Responsive button height]** selector.
1. To modify the **[!UICONTROL Label]**, select the desired label option.
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

You can configure [!DNL PayPal Smart Buttons] styling [in the Admin](configure-admin.md#configure-paypal-smart-buttons) or [!DNL Payment Services Home]. See [PayPal's Buttons style guide](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) for more information about the options.

|Field|Scope|Description|
|--- |--- |--- |
|[!UICONTROL Layout]|Store View|Define style of layout for payment buttons. Options: [!UICONTROL Vertical] / [!UICONTROL Horizontal]|
|[!UICONTROL Tagline]|Store View|Enable/disable tagline. Options: [!UICONTROL Yes] / [!UICONTROL No]|
|[!UICONTROL Color]|Store View|Define color of the payment buttons. Options: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black]|
|[!UICONTROL Shape]|Store View|Define shape of the payment buttons. Options: [!UICONTROL Rectangular] / [!UICONTROL Pill]|
|[!UICONTROL Responsive Button Height]|Store View|Defines if payment buttons use a default height. Options: [!UICONTROL Yes] / [!UICONTROL No]|
|[!UICONTROL Height]|Store View|Define height of the payment buttons. Default value: none|
|[!UICONTROL Label]|Store View|Define label that appears in the payment buttons. Options: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment]|
