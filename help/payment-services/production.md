---
title: Enable Payment Services for production
description: 
---
# Enable Payment Services for production

After the Payments Services extension is [installed](install.md), your Commerce instance is [configured and connected](connect.md), and you have [set up the sandbox](sandbox.md) and tested there, you can proceed to put the service into production and complete the [onboarding process](onboard.md).

## Set Payment Services as payment method

After you [configure your Commerce Services](connect.md#configure-commerce-services) and enable either [sandbox testing](sandbox.md#enable-sandbox-testing) or [live payments](#enable-live-payments) you must set Payment Services as your payment method.

1. On the _Admin_ sidebar go to **Sales** > **Payment Services**.
1. Click **Enable Payment Services**.

   This option will be visible if you have not yet configured Payment Services as the payment method for one or more of your Magento websites.

   You will be directed to the configuration area in the Admin---**Stores** > _Settings_ > **Configuration** > **Sales** > **Payment Methods** > _Recommended Solutions_ > _Payment Services_---to enable the Payment Services options as your [payment method](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. In _General Configuration_, set **Enable** to `Yes`.
1. Set **Payment Action**, for both _Credit Card Fields_ and _PayPal Smart Buttons_, to one of the following:

   |---|---|
   | `Authorize`  |  Approves the purchase and puts a hold on the funds. The amount is not withdrawn until it is “captured” by the merchant. |
   | `Authorize and Capture`  | Approves the purchase and the merchant "captures" the funds. |

1. Click **Save Config**.
1. Click **Go to Payment Services** to be directed back to the Payment Services home.
1. [Clear your cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   This should be done after every configuration change.

See [Configure Payment Services](configure-admin.md) for more information about configuring Credit Card Fields and PayPal Smart Buttons.

## Request payments entitlement from Adobe

To enable live onboarding you will need to request payments entitlement from Adobe [here](https://magento.com/resources/payment-services).

>[!IMPORTANT]
>
>**Live onboarding** will not be accessible until payments entitlement has been approved.

## Complete merchant onboarding

1. On the _Admin_ sidebar go to **Sales** > **Payment Services**.
1. Click **Live onboarding**.

   This option will be visible if you have not yet completed live onboarding for Payment Services.

   You are presented with a PayPal window.

1. Continue with the PayPal flow, using your PayPal account credentials (not your sandbox account credentials) or sign up for a new PayPal account.
1. On the _Admin_ sidebar go to **Sales** > **Payment Services**

   The **Live onboarding** button will no longer be visible and you see a "Live payments pending" text box.

   In that text box, you may also be asked to confirm your email address with PayPal to complete onboarding.

1. If you are prompted to confirm your email address, check your email for the confirmation message sent from PayPal and click to confirm your email address.
1. On the _Admin_ sidebar go to **Sales** > **Payment Services**.
1. Refresh your browser window.

   Once your PayPal merchant onboarding is approved, you will see a notification stating that your payment system is currently in sandbox mode and is not processing live payments.

   >[!IMPORTANT]
   >
   >If you revoke consent to Payment Services for Adobe Commerce and Magento Open Source for processing your payments (in your PayPal account settings), orders in your store cannot be processed by Payment Services.

## Enable live payments

A production merchant ID will be auto-generated and populated into the [configuration](configure-admin.md). Do not change or alter this ID.

To enable live payments:

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.
1. In the left panel, expand **Sales** and choose **Payment Methods**.
1. Expand the _Recommended Solutions_ section.
1. In the _Payment Services_ section, expand the _General Configuration_ section.
1. Set **Method** to `Production`.
1. Click **Save Config**.
1. [Clear your cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >If you do not clear your cache, you will be unable to see PayPal payment options during checkout.

If you navigate back to Payment Services home, the Sandbox payment mode message will no longer appear because you are now processing live payments.

See [Configure in the Admin](configure-admin.md) for more configuration options.

>[!IMPORTANT]
>
>If you revoke consent to Payment Services for processing your payments (in your PayPal account settings), orders in your store cannot be processed by Payment Services. If you want to re-enable payment processing, you must complete onboarding again.

## Test in production

It is highly recommended that you test Payments in production, with real credit cards and banks, before exposing this functionality to shoppers.

See [Test and validate](test-validate.md) for more information.
