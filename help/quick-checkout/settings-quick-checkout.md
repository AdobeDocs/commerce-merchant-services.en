---
title: Configure the [!DNL Quick Checkout] for Adobe Commerce extension
description: Learn the configuration options for the [!DNL Quick Checkout] and how to successfully onboard and setup the extension.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
---
# [!DNL Quick Checkout] Settings

[!DNL Quick Checkout] for Adobe Commerce and Magento Open Source provides a configuration view with all the necessary information to set up the extension.

To access these configuration settings:

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.
1. In the left panel, expand **Sales** and select **Checkout**.

   ![Quick Checkout](assets/configuration-view.png)

Refer to the [Onboarding](../quick-checkout/onboarding.md) topic for more information on how to configure the [!DNL Quick Checkout] for Adobe Commerce.

## Enable extension

![Quick Checkout](assets/enable-method.png)

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL Enable] | website | Enable or disable [!DNL Quick Checkout] for your website. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | website | Set the method, or environment, for your [!DNL Quick Checkout]. Options: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## Account credentials

![Quick Checkout](assets/account-creds.png)

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL API key] | website | A private key used by your back end to interact with [!DNL Bolt] APIs. |
| [!UICONTROL Publishable key] | website | A key used by your front end to interact with [!DNL Bolt] APIs. |
| [!UICONTROL Signing secret] | website | Used for signature verification on requests received from [!DNL Bolt]. |

{style="table-layout:auto"}

## Service settings

![Quick Checkout](assets/service-settings.png)

| Field | Scope | Description |
|---|---|---|
| [!UICONTROL Title] | store view | Add the text for display as the title for this payment option in the Payment Method view during checkout. Options: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | The [payment action](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} for the specified payment method. Options: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Enable or disable Debug Mode. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | website | Define if Adobe Commerce allows checkout tracking information to be shared with Bolt. Enabled by default. If disabled, reporting will be affected. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | website | Change navigation flow after customer is logged in. Options: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | website | Define if [!DNL Quick Checkout] allows for the automatic login during checkout. Enabled by default. Options: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | website | Select the network where the customer logs in automatically. Enabled Bolt by default. Options: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
