---
title: Onboard [!DNL Payment Services]
description: Connect your instance with [!DNL Payment Services] functionality by completing a few onboarding steps.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
---
# Onboard [!DNL Payment Services]

To get started using [!DNL Payment Services] for Adobe Commerce and Magento Open Source, you must complete a few onboarding steps for connecting your instance with the payments functionality.

## Onboarding flow

![Onboarding flow](assets/onboarding-diagram.svg)

This onboarding flow diagram shows the general process for onboarding [!DNL Payment Services].

After you complete onboarding for sandbox or live payments, financial reporting is accessible from [!DNL Payment Services] in the Admin.

If both sandbox and live payments are onboarded and enabled, you can easily switch between those modes from the [!DNL Payment Services] home.

## Prerequisites

In order to use [!DNL Payment Services], you must have the following available for your instance:

* Services Connector module
* Services ID module
* API keys

The Services Connector and Services ID modules are automatically installed during the [installation of [!DNL Payment Services]](install.md). When installation is complete, you can see a new section in the configuration settings (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]**) when you expand **[!UICONTROL Services]**---**[!UICONTROL Commerce Services Connector]**.

To learn how to create or access your API keys, see [API credentials](#obtain-api-credentials).

## Onboarding steps

1. [Install the [!DNL Payment Services] extension](install.md#get-payment-services).
1. [Obtain API credentials](connect.md#obtain-api-credentials).
1. [Connect your instance](connect.md#configure-commerce-services) to Commerce Services. This connect must be completed only once per Commerce instance.
1. [Set up the sandbox service](sandbox.md#enable-sandbox-testing) (or, alternatively, proceed to [enabling live payments](sandbox.md#enable-live-payments) if you've tested functionality in another environment) with a test PayPal payment processing account.
1. [Set [!DNL Payment Services] as your payment method](production.md#set-payment-services-as-payment-method), in sandbox mode, to start processing test payments.
1. [Request payments entitlement](production.md#request-payments-entitlement-from-adobe) to enable live onboarding.
1. [Complete merchant onboarding](production.md#complete-merchant-onboarding) to enable live payments for your Commerce websites.
1. [Get your [!DNL Payment Services] Merchant ID](production.md#configure-pricing-tier) and hand it to Sales to configure the correct pricing tier.
1. [Enable [!DNL Payment Services] in live mode](production.md#enable-live-payments) to begin processing live payments.
1. Test Payments, in both [sandbox](sandbox.md#test-in-sandbox-environment) and [production](production.md#test-in-production) environments.

>[!NOTE]
>
>If you do not configure your Commerce Services in the Admin (step 3), you cannot set up sandbox or live payments.

## Troubleshooting

* [Troubleshoot [!DNL Payment Services] installation](https://support.magento.com/hc/en-us/articles/4406603542541)
* [PayPal sandbox account not verified](https://support.magento.com/hc/en-us/articles/4406954952461)
* [Delayed [!DNL Payment Services] report data](https://support.magento.com/hc/en-us/articles/4406114741517)
* [Test credit card fails with PayPal when processing payments in a Sandbox environment](https://support.magento.com/hc/en-us/articles/5201041963917)
