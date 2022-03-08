---
title: Connect your instance
description: Connect your Commerce instance using an API key and a private key, and specify the data space in the configuration.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
---
# Connect your instance

[!DNL Payment Services] is powered by Commerce Services and deployed as SaaS (software as a service). You connect your Commerce instance using an API key and a private key, and specify the data space in the configuration. You set up this connection only once.

See [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target="_blank"} in the core user guide for detailed information about this service. 

## Obtain API credentials

To consume a Commerce SaaS service, you must use your instance's API keys, which are created and managed in your [My Account dashboard](https://account.magento.com/customer/account/login){target="_blank"}. Two different API key pairs can be created for a Commerce account---one for sandbox and one for production (live payments)---though only one pair can be actively used at a time.

>[!NOTE]
>
>Need help with accessing your [!UICONTROL My Account] dashboard? See [Create a Commerce account](https://docs.magento.com/user-guide/magento/magento-account-create.html){target="_blank"} in the core user guide.

A given API key pair is valid for all Commerce Services in an environment, so if you already have Commerce Services configured for your Commerce instance your API key pair is already present in the Admin. If your private API key is lost, a new API key pair must be generated and applied to the Commerce Services configuration in the Admin.

To learn how to generate an API key for either sandbox or production environments, see [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target="_blank"} in the core user guide.

>[!IMPORTANT]
>
>If you regenerate an API key pair and change the SaaS Identifier, all Commerce Services used by this instance connect to a different data store and your access (including previously stored data) is lost. It is recommended that you do not regenerate an API key pair and change the SaaS Identifier on an active production instance.

### Commerce API key and private key

Some Adobe Commerce and Magento Open Source features are deployed as SaaS (software as a service)---known as Commerce Services. To use these services, you must connect your Commerce instance to these services using an API key and a private key, and specify the desired data space in the [configuration](https://docs.magento.com/user-guide/configuration/services/saas.html){target="_blank"}.

When you create a Commerce account, identified by a MageID, you can generate a Commerce API key and private key. To use Commerce Services, such as [!DNL Payment Services], [!DNL Product Recommendations], or [!DNL Live Search], the license-holder must generate these keys in order to pass entitlement validation. These keys can then be passed to the systems integrator or development team that manages the projects and environments on behalf of the license-holder. If you are a solution integrator, you are also entitled to use these services for your own needs. In that case, the signer of the Commerce partner contract should generate the keys.

### Generate an API key and private key

1. Log in to your Commerce account at [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. Under the **[!UICONTROL Magento]** tab, select **[!UICONTROL API Portal]** on the sidebar.
1. From the _[!UICONTROL Environment]_ menu, select **[!UICONTROL Sandbox]**, then **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >API keys are required for both environments.

1. Enter a name in the _[!UICONTROL API Keys]_ section and click **[!UICONTROL Add New]**.

   This action opens a dialog for downloading the new key.

   >[!IMPORTANT]
   >
   >This dialog is the only opportunity you have to copy or download your key.

1. Click **[!UICONTROL Download]** then click **[!UICONTROL Cancel]**.

   The _[!UICONTROL API Keys]_ section now displays your API key.
   
1. Copy both the API key and private key when you select or create a SaaS project.

   See [SaaS](https://docs.magento.com/user-guide/system/saas.html){target="_blank"} in the core user guide for more detailed information.

The same API key can be used across instances, but each instance must have its own SaaS Data Space.

When you create a SaaS project, Commerce generates one or more SaaS data spaces depending on your Commerce license:

* Adobe Commerce - One production data space; two testing data spaces
* Magento Open Source - One production data space; no testing data spaces

### Configure SaaS project

>[!NOTE]
>
>If you do not see the _[!UICONTROL Commerce Services Connector]_ section in the Commerce configuration, you must install the Commerce modules for your desired Commerce Service, such as [[!DNL Payment Services]](install.md).

To select or create a SaaS project, request the Commerce API key from the Commerce license holder for your store.

1. On the _Admin_ sidebar, go to **[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]**.
1. In the left panel, expand **[!UICONTROL Services]** and choose **[!UICONTROL Commerce Services Connector]**.
1. In the _[!UICONTROL API Keys]_ section, paste your key values.

   >[!IMPORTANT]
   >
   >Add key values for both **[!UICONTROL sandbox]** and **[!UICONTROL production]** environments.

1. Click **[!UICONTROL Save Config]**.

   When you save, if there are any SaaS projects associated with your API key, those projects appear in the _[!UICONTROL SaaS Project]_ field in the _[!UICONTROL SaaS Identifier]_ section.

1. If no SaaS projects exist, click **[!UICONTROL Create Project]**. Then enter a name for your SaaS project in the **[!UICONTROL Project Name]** field.
1. To use for the current configuration of your Commerce store, select the **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>If you regenerate your keys in the API Portal section of My Account, immediately update the API keys in the Admin configuration. If you generate new keys and do not update them in the Admin, your SaaS extensions will no longer work and you will lose valuable data.

You can change the names by clicking the **[!UICONTROL Rename this Project]** or **[!UICONTROL Rename Data Space]** buttons respectively.

## Configure Commerce Services

The first step in onboarding [!DNL Payment Services] is to configure your Commerce Services in the Admin.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Click **[!UICONTROL Configure Commerce Services]**.

   This option is visible if you have not yet configured Commerce Services for your account.

   You are directed to the configuration area in the Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]** > **[!UICONTROL Commerce Services Connector]**, to configure your Commerce Services Connector.

1. To configure your Commerce Services, follow the steps described in [Commerce Services](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target="_blank"}.
