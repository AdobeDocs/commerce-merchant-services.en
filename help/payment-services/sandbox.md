---
title: Set up the testing sandbox
description: Use a PayPal sandbox account to use Payment Services in test mode.
---
# Set up the testing sandbox

## Set up sandbox for testing

Before starting sandbox onboarding, you must sign up for a free PayPal Developer's account, and create both merchant (to use for onboarding) and shopper accounts (to use for testing your checkout). You can create multiple Developer accounts, if desired.

A PayPal sandbox account allows you to use Payment Services in test mode. PayPal requires that you use a PayPal Developer Portal-generated Business sandbox test account, email, and password for sandbox onboarding. Do not create another account during the sandbox onboarding process.

If you created an account during the sandbox PayPal onboarding process, you must reset your onboarding sandbox because or you cannot verify your email.

To reset your sandbox account:

1. Click **Reset sandbox**. See the [PayPal create a business sandbox account](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) documentation for more information.
1. Click **Sandbox onboarding** and complete the next set of steps.

To complete sandbox onboarding:

1. Navigate to the [PayPal Developer Account page](https://developer.paypal.com/developer/accounts/).
1. Click **Log in to Dashboard** and log in with your existing credentials to the PayPal Developers account or click **Sign Up** to create an account.
1. Create a PayPal sandbox account:
   1. Go to _SANDBOX_ > **Accounts**.
   1. Click **Create account**.
   1. Select **Business** as the Account Type and click **Create**.
   1. In the _Sandbox Accounts_ section, click the three dots in the _Manage accounts_ column for the sandbox account you created.
   1. Click **View/edit account**.

      ![PayPal - View/edit sandbox account](assets/onboarding-viewedit-sandbox.png)

   1. Copy and save the Email ID and System-Generated Password for future use.

1. On the Admin sidebar, go to **Sales** > **Payment Services**.
1. Click **Sandbox onboarding**.

   This option is visible if you have not yet completed sandbox onboarding for Payment Services.

   A sandbox merchant ID is auto-generated and populated into the [configuration](configure-admin.md). Do not change or alter this ID.

   You are presented with a PayPal window for connecting a PayPal account to start accepting payments.

1. Enter the email of your business account and your country or region and click **Next**.

   ![PayPal - Connect PayPal account for payments](assets/paypal-connectacct.png)

1. Continue to follow the PayPal flow, using your previously saved sandbox account credentials.
1. On the Admin sidebar, go to **Sales** > **Payment Services**.

   The **Sandbox onboarding** button is no longer visible and you see a "Sandbox payments pending" text.

  When your PayPal sandbox onboarding is approved, you should see a notification stating that your payment system is currently in sandbox mode and is not processing live payments.

   >[!IMPORTANT]
   >
   >If you revoke consent to Payment Services for Adobe Commerce and Magento Open Source for processing your payments (in your PayPal account settings), orders in your store cannot be processed by Payment Services.

### Enable contact telephone number

Contact telephone number allows you to obtain the contact telephone numbers that PayPal collects from your customers. PayPal always collects contact telephone numbers from PayPal account holders to help confirm their identities and to contact them to resolve problems on their accounts, or to complete their fulfillment processes. However, PayPal discourages the use of contact phone numbers directly from the merchant because it can negatively impact sales. See the [PayPal get contact telephone numbers](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) documentation for more information.

This feature is `off` by default. When you enable it, store administrators can see phone numbers when a customer completes a Branded Checkout flow outside of the checkout page.

>[!IMPORTANT]
>
>This setting does not apply to other checkout flows.

## Test in sandbox environment

See [Test and validate](test-validate.md) for more information.
