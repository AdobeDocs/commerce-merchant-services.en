---
title: Connect Your Instance
description: Connect your Commerce instance using an API key and a private key, and specify the data space in the configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
---
# Connect Your Instance

[!DNL Payment Services] is powered by Commerce Services and deployed as SaaS (software as a service). You connect your Commerce instance using an API key and a private key, and specify the data space in the configuration using the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **You set up this connection only once.**

>[!INFO]
>
> See our [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) video for additional information.

* If you have *already connected your instance*, by obtaining and using your API credentials and configuring Commerce Services, you can proceed to [setting up your testing sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* If you still *need to connect your instance*, see the information in this topic about [obtaining API credentials](#obtain-api-credentials) and [configuring Commerce Services](#configure-commerce-services).
* If you are *unsure whether your instance is connected*, navigate to **System** > Services > **Commerce Services Connector** and view the public and private API key values in the [!UICONTROL Sandbox Keys] and [!UICONTROL Production Keys] sections, and the *Project* and *Data Space* fields in the [!UICONTROL SaaS Identifier] section. If those values are present, then your instance is connected.

>[!NOTE]
>
>All merchants entitled for Payment Services can use one production data space and two testing data spaces.

## Obtain API credentials

To consume a Commerce SaaS service, you must use your instance's API keys (Commerce public API key and a private key) for both sandbox and production, which are created and managed in your [My Account Dashboard](https://account.magento.com/customer/account/login). [The key pair](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) can be created for a Commerce account---one for sandbox and one for production---though only one pair can be actively used at a time.

>[!NOTE]
>
>Need help with accessing your [!UICONTROL My Account] dashboard? See [Create a Commerce account](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create).

A public API key, once created, is always available in your My Account Dashboard. It can be copied or deleted as needed. The private API key becomes visible when you create a public API key for either sandbox or production; it is only available for copying or saving from the ensuing dialog box and cannot be accessed later.

A given API key pair is valid for all Commerce Services in an environment, so if you already have Commerce Services configured for your instance, your API key pair is already present in the Commerce Services Connector.

If your API key is lost, a new API key pair must be [generated](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) and [applied](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) to the Commerce Services Connector configuration in the Admin. If the wrong keys are configured or none exist in the config, an account verification error dialog appears in Payment Services notifying you that the account was not verified.

See a [list of available Commerce Services that use the API](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#availableservices).

To learn how to generate an API key for either sandbox or production environments, see [Credentials](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>It is recommended that you do not regenerate an API key pair *and* change the SaaS identifier and/or data space on an active production instance. You will lose data for your instance if they are modified.

## Configure Commerce Services

The same API key can be used across instances, but each instance must have its own [SaaS Data Space](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Merchants must use the same keys generated for the MageID for their Payment entitlements.

Now that you have obtained your credentials, you can configure your SaaS project and Saas Data Space.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Click **[!UICONTROL Configure Commerce Services]**.

   This option is visible if you have not yet configured Commerce Services for your account.

   You are directed to the configuration area in the Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]** > **[!UICONTROL Commerce Services Connector]**, to configure your Commerce Services Connector.

1. To configure your Commerce Services, follow the steps described in [SaaS configuration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).

   >[!INFO]
   >
   > See our [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) video for additional information.

## Endpoint

[!DNL Payment Services] uses the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) to connect to Commerce Services and deploy as SaaS. This [!DNL Commerce Services Connector] communicates through the endpoint at:

* `commerce-beta.adobe.io` for sandbox environments.
* `commerce.adobe.io for` for live environments.
