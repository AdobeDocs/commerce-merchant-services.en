---
title: Onboard Payment Services
description: Complete a few onboarding steps to connect your instance with Payment Services functionality.
role: User
content-type: Context
feature: Payments
level: Intermediate
---
# Onboard Payment Services

To get started using Payment Services for Adobe Commerce and Magento Open Source you must complete a few onboarding steps to connect your instance with our payments functionality.

## Onboarding flow

<!-- ![Onboarding flow](assets/onboard-diagram.svg) -->

This onboarding flow diagram shows the general process for onboarding Payment Services.

After you complete onboarding for sandbox or live payments, [financial reporting](financial-reporting.md) is accessible from Payment Services in the Admin.

If both sandbox and live payments are onboarded and enabled, you can easily switch between those modes from the Payment Services home.

## Prerequisites

In order to use Payment Services, you must have the following available for your instance:

* Services Connector module
* Services ID module
* API keys

The Services Connector and Services ID modules will be automatically installed during the [installation of Payment Services](install.md). When installation is complete, you will see a new section in the Admin---in **Stores** > _Settings_ > **Configuration** > **Services**---called Commerce Services Connector.

See [API credentials](#obtain-api-credentials) to learn how to create or access your API keys.

## Onboarding steps

1. [Install Payment Services](install.md#get-payment-services).
1. [Obtain API credentials](connect.md#obtain-api-credentials).
1. [Connect your instance](Connect.md#configure-commerce-services) to Commerce Services. This only needs to be completed once per Commerce instance.
1. [Set up the sandbox service](sandbox.md#enable-sandbox-testing) (or, alternatively, proceed to [enabling live payments](sandbox.md#enable-live-payments) if you've tested functionality in another environment) to set up a test PayPal payment processing account.
1. [Set Payment Services as your payment method](production.md#set-payment-services-as-payment-method), in sandbox mode, to start processing test payments.
1. [Complete merchant onboarding](production.md#complete-merchant-onboarding) to enable live payments for your Commerce website(s).
1. [Request payments entitlement](production.md#request-payments-entitlement-from-adobe) to enable live onboarding.
1. [Enable Payment Services in live mode](production.md#enable-live-payments) to begin processing live payments.
1. Test Payments, in both [sandbox](sandbox.md#test-in-sandbox-environment) and [production](production.md#test-in-production) environments.

>[!NOTE]
>
>If you do not configure your Commerce Services in the Admin (step 3) you cannot set up sandbox or live payments.

## Troubleshooting

// add articles from KB