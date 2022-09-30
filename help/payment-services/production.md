---
title: Enable [!DNL Payment Services] for production
description: Complete the onboarding process by enabling [!DNL Payment Services] for production.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
---
# Enable [!DNL Payment Services] for production

You can put the service into production and complete the [onboarding process](onboard.md), per the steps in this topic, after you:

* [Install](install.md) the Payment Services extension
* [Configure and connect](connect.md) your instance
* [Set up](sandbox.md) and [test](test-validate.md) your sandbox

## Set [!DNL Payment Services] as payment method

After you [configure your Commerce Services](connect.md#configure-commerce-services) and enable either [sandbox testing](sandbox.md#enable-sandbox-testing) or [live payments](#enable-live-payments), you must set [!DNL Payment Services] as your payment method.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Click **[!UICONTROL Enable Payment Services]**.

   This option is visible if you have not yet configured [!DNL Payment Services] as the payment method for one or more of your websites.

   You are directed to the settings area in the Home view with the relevant options expanded (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), where you can enable the [!DNL Payment Services] options as your [payment method](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. In _[!UICONTROL General Configuration]_, set **[!UICONTROL Enable]** to `Yes`.
1. Set **[!UICONTROL Payment Action]**, for both _[!UICONTROL Credit Card Fields]_ and _[!UICONTROL PayPal Smart Buttons]_, to one of the following:

   |Setting|Description|
   |---|---|
   | `Authorize`  |  Approves the purchase and puts a hold on the funds. The amount is not withdrawn until it is "captured" by the merchant. |
   | `Authorize and Capture`  | Approves the purchase and the merchant "captures" the funds. |

1. Click **[!UICONTROL Save]**.
1. Click **[!UICONTROL Go to Payment Services]** to be directed back to the [!DNL Payment Services] Home.
1. [Clear your cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   Clearing should be done after every configuration change.

See [Configure Payment Services](settings.md) for more information about configuring Credit Card Fields and PayPal Smart Buttons.

## Complete merchant onboarding

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Click **[!UICONTROL Live onboarding]**.

   This option is visible if you have not yet completed live onboarding for [!DNL Payment Services].

   You are presented with a PayPal window.

1. Continue with the PayPal flow, using your PayPal account credentials (not your sandbox account credentials) or sign up for a new PayPal account.
1. On the Admin sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   The _[!UICONTROL Live onboarding]_ button is no longer visible and you see a "[!UICONTROL Live payments pending]" text box.

   In that text box, you may also be asked to confirm your email address with PayPal to complete onboarding.

1. If you are prompted to confirm your email address, check your email for the confirmation message sent from PayPal and click to confirm your email address.
1. On the Admin sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Refresh your browser window.

   When your PayPal merchant onboarding is approved, you should see a notification stating that your payment system is in sandbox mode and is not processing live payments.

   >[!IMPORTANT]
   >
   >If you revoke consent to [!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] for processing your payments (in your PayPal account settings), orders in your store cannot be processed by [!DNL Payment Services]. On your Payment Services Home, an alert about the revoked consent appears.

## Request payments entitlement from Adobe

To enable live onboarding, you must request payments entitlement from Adobe:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Click **[!UICONTROL Get Live Payments]** in your [!DNL Payment Services] Home.

   ![Request entitlements](assets/request-entitlements.png)

1. Complete the form.
1. A member of the sales team will contact you.

Alternatively, you can request payments entitlements from Adobe at [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Live onboarding** is not accessible until payments entitlement has been approved.

## Configure pricing tier

To get your [!DNL Payment Services] _Merchant ID_:


1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. In the Home view, click **[!UICONTROL Settings]**. See [Home](payments-home.md) for more information.
1. Select the required _Merchant ID_ and submit it to your Sales representative, who will configure the correct pricing tier.

## Enable live payments

A _production merchant ID_ is auto-generated and populated in the [configuration](configure-admin.md). Do not change or alter this ID.

To enable live payments:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. On the Home, click **[!UICONTROL Settings]** at the top right of the page. See [Home](payments-home.md) for more information.
1. In the _[!UICONTROL General Configuration]_ section set **[!UICONTROL Payment mode]** to `Production`.
1. Click **[!UICONTROL Save]**.
1. [Clear your cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >If you do not clear your cache, customers cannot see PayPal payment options during checkout.

If you navigate back to [!DNL Payment Services] Home, the Sandbox payment mode message no longer appears because you are now processing live payments.

See [Configure in the Admin](configure-admin.md) for legacy configuration options.

>[!IMPORTANT]
>
>If you revoke consent to [!DNL Payment Services] for processing your payments (in your PayPal account settings), orders in your store cannot be processed by [!DNL Payment Services]. If you want to re-enable payment processing, you must complete onboarding again. On your Payment Services Home, an alert about the revoked consent appears.

## Test in production

It is highly recommended that you test Payments in production, with real credit cards and banks, before exposing this functionality to shoppers.

See [Test and validate](test-validate.md) for more information.
