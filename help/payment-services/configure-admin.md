---
title: Configure in the Admin
Description: After installation, you can configure Payment Services in the Admin.
feature: Payments
role: Administrator, User
level: Intermediate
---
# Configure in the Admin

You can customize Payment Services to your needs with helpful configuration options in the Admin.

When you configure Payment Services for Adobe Commerce and Magento Open Source in the Admin, those configurations apply only to the environment that is set in the Method field of General Configuration. Any changes you make in the configuration fields are independent of switching the Method selection---if you switch the method, your selections do not reset.

See the [General Configuration section](#general-configuration) for more information.

## General configuration

You can enable Payment Services for your store, and enable either sandbox testing or live payments in the General Configuration section.

![Methods view](assets/methods-view.png)

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.
1. In the left panel, expand **Sales** and choose **Payment Methods**.
1. Expand the _Recommended Solutions_ section.
1. In the _Payment Services_ section, expand the _General Configuration_ section.
1. For **Enable**, set it to `Yes` to enable Payment Services for your store.
1. For **Method**, set it to `Sandbox` if you are still testing Payment Services for your store or `Production` if you are ready to enable live payments.

   >[!WARNING]
   >
   >Your Sandbox Merchant ID and Production Merchant ID are auto-generated and present in their respectable fields when you have finished onboarding for the sandbox and/or production. Do not remove or change these IDs.

1. Click **Save Config** to save your changes.

### Configuration options

| Field | Scope | Description |
|---|---|---|
| Enable | website | Enable or disable Payment Services for your website. Options: Yes / No |
| Method | store view | Set the method, or environment, for your store. Options: Sandbox / Production |
| Sandbox Merchant ID | store view | Field for your sandbox merchant ID, auto-generated during sandbox onboarding. Do not change or alter this ID. |
| Production Merchant ID | store view | Field for your production merchant ID, auto-generated during sandbox onboarding. Do not change or alter this ID. |

## Credit Card Fields

The Credit Card Fields payment options provide a simple and secure checkout for credit card or debit card payment methods.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

### Configure Credit Card Fields

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.
1. In the left panel, expand **Sales** and choose **Payment Methods**.
1. Expand the _Recommended Solutions_ section.
1. In the _Payment Services_ section, expand the _Credit Card Fields_ section.
1. For **Title**, enter text (if needed) to change the name of the payment method as shown during checkout.
1. To [set the payment action](onboard-payments.md#set-payment-services-as-payment-method), select **Authorize** or **Authorize and Capture**.
1. For **Debug Mode**, choose `Yes` to enable debug mode (or `No` to disable it).
1. Click **Save Config** to save your changes.

#### Configuration options

| Field | Scope | Description |
|---|---|---|
| Title | store view | Add the text for display as the title for this payment option in the Payment Method view during checkout. Options: text field |
| Payment Action | website | The [payment action](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} for the specified payment method. Options: Authorize / Authorize and Capture |
| Debug Mode | website | Enable or disable Debug Mode. Options: Yes / No |

## PayPal Smart Buttons

The PayPal Smart Buttons payment options provide a simple, fast, and secure checkout process for your customer.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

### Configure PayPal Smart Buttons

You can enable and configure the PayPal Smart Buttons payment options within the Admin:

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.
1. In the left panel, expand **Sales** and choose **Payment Methods**.
1. Expand the _Recommended Solutions_ section.
1. In the _Payment Services_ section, expand the _PayPal Smart Buttons_ section.
1. To change the name of the payment method as shown during checkout, edit the _Title_ field.
1. To [set the payment action](onboard-payments.md#set-payment-services-as-payment-method), select **Authorize** or **Authorize and Capture**.
1. To disable the [Pay Later messaging](payments-options.md#pay-later-button) (if desired), select **No** for _Display Pay Later Message_.
1. To enable debug mode, select **Yes** for the _Debug Mode_ (**No** disables it).
1. To save your changes, click **Save Config** .

#### Configuration options

| Field | Scope | Description |
|---|---|---|
| Title | store view | Add the text to be displayed as the title for this payment option in the Payment Method view during checkout. Options: text field |
| Payment Action | website | The [payment action](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} for the specified payment method. Options: Authorize / Authorize and Capture |
| Display Pay Later Message | website | Enable or disable the Pay Later messaging in the shopping cart, product page, mini-cart, and during the checkout flow. Options: Yes / No |
| Debug Mode | website | Enable or disable Debug Mode. options: Yes / No |
