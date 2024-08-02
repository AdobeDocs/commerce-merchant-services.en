---
title: Set Up the Testing Sandbox
description: Use a PayPal sandbox account to use [!DNL Payment Services] in test mode.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install
---
# Set Up the Testing Sandbox

Before starting sandbox onboarding, you must sign up for a free PayPal Developer's account, and create both merchant (to use for onboarding) and shopper accounts (to use for testing your checkout). You can create multiple Developer accounts, if desired.

A PayPal sandbox account allows you to use [!DNL Payment Services] in test mode. PayPal requires that you use a PayPal Developer Portal-generated Business sandbox test account, email, and password for sandbox onboarding. *Do not create another account during the sandbox onboarding process.*

## Sandbox onboarding

To complete sandbox onboarding:

1. Navigate to the [PayPal Developer Account page](https://developer.paypal.com/developer/accounts/).
1. Click **[!UICONTROL Log in to Dashboard]** and log in with your existing PayPal Developer Portal-generated Business sandbox test account or click **Sign Up** to create an account.
1. Create a PayPal sandbox account:
   1. Go to _[!UICONTROL Testing Tools]_ > **[!UICONTROL Sandbox Accounts]**.
   1. Click **[!UICONTROL Create account]**.

      If you created an a PayPal sandbox account during the sandbox PayPal onboarding process, you must [reset your onboarding sandbox](#reset-your-sandbox-account) because or you cannot verify your email.

   1. Select **[!UICONTROL Business]** as the Account Type and click **[!UICONTROL Create]**.
   1. In the _[!UICONTROL Sandbox Accounts]_ section, click the three dots in the _[!UICONTROL Manage accounts]_ column for the sandbox account you created.
   1. Click **[!UICONTROL View/edit account]**.

      ![PayPal - View/edit sandbox account](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Copy and save the Email ID and System-Generated Password for future use.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Click **[!UICONTROL Sandbox onboarding]**.

   This option is visible if you have not yet completed sandbox onboarding for [!DNL Payment Services].

   A sandbox merchant ID is auto-generated and populated into [settings](settings.md). Do not change or alter this ID.

   You are presented with a PayPal window for connecting a PayPal account to start accepting payments.

1. Enter the email and password of the PayPal sandbox account you generated in step 3 (not your PayPal business account information) and your country or region.
1. Click **[!UICONTROL Next]**.

   ![PayPal - Connect PayPal account for payments](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Continue to follow the PayPal flow, using your previously saved sandbox account credentials.
1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   The **[!UICONTROL Sandbox onboarding]** button is no longer visible and you see a "Sandbox payments pending" text.

  When your PayPal sandbox onboarding is approved, you should see a notification stating that your payment system is currently in sandbox mode and is not processing live payments.

   >[!IMPORTANT]
   >
   >If you revoke consent to [!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] for processing your payments (in your PayPal account settings), orders in your store cannot be processed by [!DNL Payment Services]. On your Payment Services home, an alert about the revoked consent appears. To dismiss the alert, click **[!UICONTROL Do not show again]**.

### Reset your sandbox account

If you created an a PayPal sandbox account during the sandbox PayPal onboarding process, you must reset your onboarding sandbox because or you cannot verify your email.

To reset your sandbox account:

1. Click **[!UICONTROL Reset sandbox]**. [Create a PayPal business sandbox account](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Click **[!UICONTROL Sandbox onboarding]** and complete the next set of steps.

## Enable contact telephone number

Contact telephone number allows you to obtain the contact telephone numbers that PayPal collects from your customers. PayPal always collects contact telephone numbers from PayPal account holders to help confirm their identities and to contact them to resolve problems on their accounts, or to complete their fulfillment processes. However, PayPal discourages the use of contact phone numbers directly from the merchant because it can negatively impact sales. See the [PayPal get contact telephone numbers](https://www.sandbox.paypal.com/businessmanage/preferences/website) documentation for more information.

This feature is `off` by default. When you enable it, store administrators can see phone numbers when a customer completes a Branded Checkout flow outside of the checkout page.

>[!IMPORTANT]
>
>This setting does not apply to other checkout flows.

## Test in sandbox environment

It is highly recommended that you use testing dataspaces for integration and staging environments, and to test Payments in production, with real credit cards and banks, before exposing this functionality to shoppers.

See [Test and validate](test-validate.md) for more information.
