---
title: Payment Services Settings
description: After installation, you can configure [!DNL Payment Services] in the Home.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
---
# Settings

You can customize [!DNL Payment Services] to your needs with helpful settings in the [!DNL Payment Services] Home.

To configure [!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] click **[!UICONTROL Settings]**. These configuration options apply only to the environment that is set in the _[!UICONTROL Payment mode]_ field in General settings.

See the [[!UICONTROL General] settings section](#general-settings) for more information.

>[!IMPORTANT]
>
> For multi-store or legacy configuration, refer to the [Configure in the Admin](configure-admin.md) topic.

## Enable Payment Services

You can enable [!DNL Payment Services] for your website, and enable either sandbox testing or live payments, in the [!UICONTROL General] section.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Home view](assets/payment-services-menu-small.png)

1. Click **[!UICONTROL Settings]**. See [Introduction to [!DNL Payment Services] Home](payments-home.md) for more information.

   The _[!UICONTROL General]_ section includes settings used to enable [!DNL Payment Services] as the payment method.

1. To enable [!DNL Payment Services] as the payment method for your store, toggle (**[!UICONTROL Enable Payment Services as payment method]**) to `Yes`.

1. If you are still testing [!DNL Payment Services] for your store, set **Payment mode** to `Sandbox`. If you are ready to enable live payments, set it to `Production`.

   >[!WARNING]
   >
   >Your _[!UICONTROL Sandbox Merchant ID]_ and _[!UICONTROL Production Merchant ID]_ are auto-generated and present in their respectable fields when you finish onboarding for the sandbox and/or production. Do not remove or change these IDs.

1. To change the default settings for payment functions and storefront display, set the additional options as needed:

   - [Credit card fields](#credit-card-fields)
   - [PayPal smart buttons](#paypal-smart-buttons)
   - [Button style](#button-style)

1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### Credit card fields

The _[!UICONTROL Credit Card Fields]_ settings provide a simple and secure checkout option for credit card or debit card payment methods.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

1. To change the name of the payment method displayed during checkout, edit the value in the **[!UICONTROL Checkout title]** field.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), toggle **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. To enable debug mode, toggle the **[!UICONTROL Debug Mode]** selector.
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### PayPal smart buttons

The [!DNL PayPal Smart Buttons] payment options provide a simple, fast, and secure checkout process for your customer. See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

You can enable and configure the PayPal smart buttons payment options:

1. To change the name of the payment method as shown during checkout, edit the value in the **[!UICONTROL Checkout Title]** field.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), toggle **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. Use the toggle selectors to enable or disable [!DNL PayPal smart button] display features:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. To change the [Pay Later messaging](payments-options.md#pay-later-button), toggle the **[!UICONTROL Display Pay Later message]** option.
1. To enable debug mode, toggle the **[!UICONTROL Debug Mode]** selector.  
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

#### Button style

You can also configure the _[!UICONTROL Button style]_ options of the PayPal smart buttons:

1. To change the **[!UICONTROL Layout]**, select `Vertical` or `Horizontal`.

   >[!NOTE]
   >
   > If your store is configured to show all three PayPal smart buttons and the button style is configured as `Horizontal`, only two buttons are visible on the product page, mini cart, and checkout page, and one button is visible in the cart.

1. To enable the tagline in a horizontal layout, toggle the **[!UICONTROL Show tagline]** selector.
1. To modify the **[!UICONTROL Color]**, select the desired color option.
1. To modify the **[!UICONTROL Shape]**, select `Pill` or `Rect`.
1. To enable button height selector, toggle the **[!UICONTROL Responsive button height]** selector.
1. To modify the **[!UICONTROL Label]**, select the desired label option.
1. Click **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

You can configure [!DNL PayPal Smart Buttons] styling in the Admin or [!DNL Payment Services Home]. See [PayPal's Buttons style guide](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) for more information.
