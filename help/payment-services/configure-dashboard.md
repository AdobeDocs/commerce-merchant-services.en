---
title: Configure in the dashboard
description: After installation, you can configure [!DNL Payment Services] in the dashboard.
role: Admin, User
level: Intermediate
exl-id: 015c5c8c-8184-45c1-932a-f4365ddf5a30
---
# Configure in the Dashboard

You can customize [!DNL Payment Services] to your needs with helpful configuration options in the dashboard.

When you click [!UICONTROL Settings] in the dashboard, you can quickly configure [!DNL Payment Services] for Adobe Commerce and Magento Open Source. These configuration options apply only to the environment that is set in the [!UICONTROL Payment mode] field in the General settings.

See the [[!UICONTROL General] settings section](#general-settings) for more information.

>[!IMPORTANT]
>
> For multi-store or legacy configuration, refer to the [Configure in the Admin](configure-admin.md) topic.

## Configure Payment Services

You can enable [!DNL Payment Services] for your website, and enable either sandbox testing or live payments in the [!UICONTROL General] settings section.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Dashboard view](assets/payment-services-menu-small.png)

1. On the dashboard, click **[!UICONTROL Settings]** at the top right of the page.

   The _[!UICONTROL General]_ section includes the configuration options used to set [!DNL Payment Services] as a payment method.

1. For the toggle option at the top (**[!UICONTROL Enable Payment Services as payment method]**), set it to `Yes` to enable [!DNL Payment Services] for your website.

1. For **Payment mode**, set it to `Sandbox` if you are still testing [!DNL Payment Services] for your store or `Production` if you are ready to enable live payments.

   >[!WARNING]
   >
   >Your [!UICONTROL Sandbox Merchant ID] and [!UICONTROL Production Merchant ID] are auto-generated and present in their respectable fields when you have finished onboarding for the sandbox and/or production. Do not remove or change these IDs.

1. To change the default settings for payment functions and storefront display, set the additional options as needed:

   - [Credit card fields](#credit-card-fields)
   - [PayPal smart buttons](#paypal-smart-buttons)
   - [Button style](#button-style)

1. To save your changes, click **[!UICONTROL Save]** at the top right of the page.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### Credit card fields

The [!UICONTROL Credit Card Fields] payment options provide a simple and secure checkout for credit card or debit card payment methods.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

1. For **[!UICONTROL Checkout title]**, enter text (if needed) to change the name of the payment method that is displayed during checkout.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), set **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. For **[!UICONTROL Debug Mode]**, toggle the selector to enable debug mode.
1. To save your changes, click **[!UICONTROL Save]** at the top right of the page.
1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### PayPal smart buttons

The [!DNL PayPal Smart Buttons] payment options provide a simple, fast, and secure checkout process for your customer. See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

You can enable the PayPal smart buttons payment options within the dashboard:

1. To change the name of the payment method as shown during checkout, edit the value in the **[!UICONTROL Checkout Title]** field.
1. To [set the payment action](production.md#set-payment-services-as-payment-method), set **[!UICONTROL Payment action]** to `Authorize` or `Authorize and Capture`.
1. Use the toggle selectors to enable or disable [!DNL PayPal smart button] display features:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** to enable option to show button during checkout.

1. To change the [Pay Later messaging](payments-options.md#pay-later-button) (if desired), toggle the **[!UICONTROL Display Pay Later message]** option.
1. To enable debug mode, click **[!UICONTROL Debug Mode]**,  
1. To save your changes, click **[!UICONTROL Save]** at the top right of the page.
1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### Button style

You can also configure the _[!UICONTROL Button style]_ options of the PayPal smart buttons within the dashboard:

1. To change the **[!UICONTROL Layout]**, select `Vertical` or `Horizontal`.
1. To enable tagline in a horizontal layout, click **[!UICONTROL Show tagline]**.
1. To modify the **[!UICONTROL Color]**, select the desired color option.
1. To change the **[!UICONTROL Shape]**, select `Pill` or `Rect`.
1. To enable button height selector, click **[!UICONTROL Responsive button height]**.
1. To modify the **[!UICONTROL Label]**, select the desired label option.
1. To save your changes, click **[!UICONTROL Save]** at the top right of the page.
1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

You can configure [!DNL PayPal Smart Buttons] styling in the Admin or the Dashboard. See [PayPal's Buttons style guide](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) for more information.
