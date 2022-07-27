---
title: Connect your instance
description: Connect your Commerce instance using an API key and a private key, and specify the data space in the configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
---
# Connect your instance

[!DNL Payment Services] is powered by Commerce Services and deployed as SaaS (software as a service). You connect your Commerce instance using an API key and a private key, and specify the data space in the configuration. You set up this connection only once.

See [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target="_blank"} in the core user guide for detailed information about this service. 

## Obtain API credentials

To consume a Commerce SaaS service, you must use your instance's API keys, which are created and managed in your [My Account Dashboard](https://account.magento.com/customer/account/login){target="_blank"}. Two different API keys can be created for a Commerce account---one for sandbox and one for production---though only one pair can be actively used at a time.

>[!NOTE]
>
>Need help with accessing your [!UICONTROL My Account] dashboard? See [Create a Commerce account](https://docs.magento.com/user-guide/magento/magento-account-create.html){target="_blank"}.

A given API key pair is valid for all Commerce Services in an environment, so if you already have Commerce Services configured for your Commerce instance your API key pair is already present in the Admin. If your API key is lost, a new API key pair must be generated and applied to the Commerce Services configuration in the Admin.

To learn how to generate an API key for either sandbox or production environments, see [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target="_blank"}.

>[!IMPORTANT]
>
>If you regenerate an API key pair and change the SaaS Identifier, all Commerce Services used by this instance will connect to a different data store and your access (including previously stored data) is lost. It is recommended that you do not regenerate an API key pair and change the SaaS Identifier on an active production instance.

The same API key can be used across instances, but each instance must have its own [SaaS Data Space](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

## Configure SaaS project

Now that you have obtained your credentials, you can configure your SaaS project. See [SaaS configuration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv) to learn how to select or create a SaaS project.

## Configure Commerce Services

The first step in onboarding [!DNL Payment Services] is to configure your Commerce Services in the Admin.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Click **[!UICONTROL Configure Commerce Services]**.

   This option is visible if you have not yet configured Commerce Services for your account.

   You are directed to the configuration area in the Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]** > **[!UICONTROL Commerce Services Connector]**, to configure your Commerce Services Connector.

1. To configure your Commerce Services, follow the steps described in [Commerce Services](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target="_blank"}.
