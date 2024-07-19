---
title: Commerce Services Connector
description: Learn how to integrate your Adobe Commerce or Magento Open Source instance to services using production and sandbox API keys.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
---
# [!DNL Commerce Services Connector]

Some Adobe Commerce and Magento Open Source features are powered by [!DNL Commerce Services] and deployed as SaaS (software as a service). To use these services, you must connect your [!DNL Commerce] instance using production and sandbox API keys, and specify the data space in the [configuration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). You only need to configure the connection one time for each Commerce instance.

## Available services {#availableservices}

The following lists the [!DNL Commerce] features you can access through the [!DNL Commerce Services Connector]:

| Service | Availability |
| ---|--- |
|[[!DNL Product Recommendations]](/help/product-recommendations/overview.md) powered by Adobe Sensei| Adobe Commerce|
|[[!DNL Live Search]](/help/live-search/overview.md) powered by Adobe Sensei | Adobe Commerce|
|[[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce and Magento Open Source|
|[[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)|Adobe Commerce|
|[[!DNL Catalog Service]](/help/catalog-service/overview.md)|Adobe Commerce|
|[[!DNL Data Connection]](/help/data-connection/overview.md)|Adobe Commerce|

## Architecture

At a high level, the [!DNL Commerce Services Connector] is made up of the following core elements:

![Commerce Services Connector Architecture](assets/saas-config-sync-workflow.png)

The following sections discuss each of these elements in more detail.

## Credentials {#apikey}

The production and sandbox API keys are generated from the [!DNL Commerce] account of the [license owner](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding). The Commerce account is identified by a unique [!DNL Commerce] ID (MageID). The license owner for the merchant's organization can generate API keys for services like Product Recommendations or Live Search, as long as the account is in good standing.

The keys can be shared on a "need-to-know" basis with the systems integrator or development team that manages projects and environments on behalf of the license holder. Developers who have been granted [!DNL Shared Access] by the license owner cannot generate the keys on their behalf even if the merchant's organization is present in the [!DNL Switch Accounts] dropdown on their account.

Additionally, solution integrators are also entitled to use [!DNL Commerce Services]. If you are a solution integrator, the signer of the [!DNL Commerce] partner contract should generate the API keys.

>[!NOTE]
>
>The license owner is typically the Primary Contact on the Adobe Commerce account and is not always the same as the Project Owner of the Adobe Commerce on cloud infrastructure project.

### Generate the production and sandbox API keys {#genapikey}

1. Log in to your [!DNL Commerce] account at [https://account.magento.com](https://account.magento.com/){:target="_blank"}.

1. Under the **Magento** tab, select **API Portal** on the sidebar.

1. From the _Environment_ menu, select **Production** or **Sandbox**.

1. Enter a name in the _API Keys_ section, and click **Add New** to open the dialog to download the new key.

   ![Download private key](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > This dialog provides the only opportunity that you have to copy or download your keys.

1. Click **Download** then click **Cancel**.

1. Repeat the above steps for each environment (production and sandbox).

   The **API Keys** section now displays your API (Public) keys. You need both the production and sandbox keys (Public+Private) when you [select or create a SaaS project](#createsaasenv).

## SaaS configuration {#saasenv}

[!DNL Commerce] instances must be configured with a SaaS project and a SaaS data space so that [!DNL Commerce Services] can send data to the right location. A SaaS project groups all SaaS data spaces. The SaaS Data Spaces are used to collect and store data that enables [!DNL Commerce Services] to work. Some of this data may be exported from the [!DNL Commerce] instance and some may be collected from shopper behavior on the storefront. That data is then persisted to secure cloud storage.

For [!DNL Product Recommendations], the SaaS data space contains catalog and behavioral data. You can point a [!DNL Commerce] instance to a SaaS data space by [selecting it](https://docs.magento.com/user-guide/configuration/services/saas.html) in the [!DNL Commerce] configuration.

>[!WARNING]
>
> Use your production SaaS data space only on your production [!DNL Commerce] installation to avoid data collisions. Otherwise, you risk polluting your production site data with testing data, which causes deployment delays. For example, your production product data could be mistakenly overwritten from staging data, such as staging URLs.

### Select or create a SaaS project {#createsaasenv}

To select or create a SaaS project, request the [!DNL Commerce] API key from the [!DNL Commerce] license owner for your store:

>[!NOTE]
>
> If you do not see the **[!UICONTROL Commerce Services Connector]** section in the [!DNL Commerce] configuration, you must install the [!DNL Commerce] modules for your desired [[!DNL Commerce] service](#availableservices).

1. On the _Admin_ sidebar, go to **System** > Services > **Commerce Services Connector**.

   If you do not see the **[!UICONTROL Commerce Services Connector]** section in the [!DNL Commerce] configuration, install the [!DNL Commerce] modules for your desired [[!DNL Commerce] service](#availableservices). Also, make sure that the `magento/module-services-id` package is installed.

1. In the _Sandbox API Keys_ and _Production API Keys_ sections, paste your key values.

   Private keys must include `----BEGIN PRIVATE KEY---` at the beginning of the key and `----END PRIVATE KEY----` at the end of the private key.

1. Click **Save**.

  Any SaaS projects that are associated with your keys appear in the **Project** field in the **SaaS Identifier** section.

1. If no SaaS projects exist, click **Create Project**. Then in the **Project** field, enter a name for your SaaS project.

   When you create a SaaS project, [!DNL Commerce] generates one or more SaaS data spaces depending on your [!DNL Commerce] license:
   - Adobe Commerce - One production data space; two testing data spaces only. On Cloud Pro projects with multiple Staging environments, you can request additional testing data spaces for each Staging environment by [submitting a Support request](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
   - Magento Open Source - One production data space; no testing data spaces

1. Select the **Data Space** to use for the current configuration of your [!DNL Commerce] store.

>[!NOTE]
>
>If you have separate instances to integrate with Commerce Services, [submit a Support ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) to request a new SaaS project for each additional instance. After support has created the SaaS project, configure the Commerce Services integration for the instance using the same API key and selecting the new SaaS project for the data space.

>[!WARNING]
>
> If you generate new keys in the API Portal section of My Account, immediately update the API keys in the Admin configuration. If you generate new keys and do not update them in the Admin, your SaaS extensions no longer work and you lose valuable data.

To change the names of your SaaS project or data space, click **Rename** next to either one. Changing the name does not affect your service because the name is only a label to help you identify and differentiate between projects and data spaces.

## IMS Organization (optional) {#organizationid}

To connect your Adobe Commerce instance to the Adobe Experience Platform, sign in to your Adobe account using your Adobe ID. After you sign in, the IMS organization associated with your Adobe account is displayed in this section.

## SaaS data export

When your [!DNL Commerce] instance successfully connects to [!DNL Commerce Services], the SaaS data export process exports Commerce data from your [!DNL Commerce] server to [!DNL Commerce SaaS Services] so it can be synchronized to connected Commerce Services. In the Admin, you can check synchronization status using the [Data Management dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). For details, see the [SaaS Data Export Guide](../data-export/overview.md).
