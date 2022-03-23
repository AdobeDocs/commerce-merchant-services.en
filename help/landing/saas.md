---
title: Commerce Services Connector
description: Learn how to integrate your Adobe Commerce or Magento Open Source instance to services using an API key and a private key.
---

# [!DNL Commerce Services Connector]

Some Adobe Commerce and Magento Open Source features are powered by [!DNL Commerce Services]  and deployed as SaaS (software as a service). To use these services, you must connect your [!DNL Commerce] instance using an API key and a private key, and specify the data space in the [configuration](https://docs.magento.com/user-guide/configuration/services/saas.html). You only need to set this up once.

## Available services

The following lists the [!DNL Commerce] features you can access through the [!DNL Commerce Services Connector]:

| Service | Availability |
| ---|--- |
|[Product Recommendations powered by Adobe Sensei](./product-recommendations/overview.md) | Adobe Commerce|
|[Live Search powered by Adobe Sensei](./live-search/overview.md) | Adobe Commerce|
|[Payment Services](./payment-services/index.md) | Adobe Commerce and Magento Open Source|

## Architecture

At a high level, the [!DNL Commerce Services Connector] is made up of the following core elements:

![Commerce Services Connector Architecture](assets/saas-config-sync-workflow.png)

The following sections discuss each of these elements in more detail.

## Credentials {#apikey}

The API key and private key are generated from the [!DNL Commerce] account of the license holder, which is identified by a unique [!DNL Commerce] ID (MageID). To pass entitlement validation for services such as [!DNL Product Recommendations] or [!DNL Live Search], the license holder of the merchant's organization can generate the set of API keys as long as the account is in good standing. The keys can be shared on a "need to know" basis with the systems integrator or development team that manages projects and environments on behalf of the license holder. Additionally, solution integrators are also entitled to use [!DNL Commerce Services]. If you are a solution integrator, the signer of the [!DNL Commerce] partner contract should generate the API keys.

### Generate an API key and private key {#genapikey}

1. Log in to your [!DNL Commerce] account at [https://account.magento.com](https://account.magento.com/){:target="_blank"}.

1. Under the **Magento** tab, select **API Portal** on the sidebar.

1. From the _Environment_ menu, select **Production** or **Sandbox**.

   >[!NOTE]
   >
   >For [!DNL _Product Recommendations_] and [!DNL _Live Search_], select **Production**. Production keys give you access to production and non-production data spaces. Sandbox keys are not used for these services.

1. Enter a name in the _API Keys_ section and click **Add New**.

   This opens a dialog for downloading the new key.

   ![Download private key](assets/download-api-private-key.png)

   >[!WARNING]
   >
   >This is the only opportunity that you have to copy or download your key.

1. Click **Download** then click **Cancel**.

   The **API Keys** section now displays your API key. You need both the API key and private key when you [select or create a SaaS project](#createsaasenv).

## SaaS configuration {#saasenv}

[!DNL Commerce] instances must be configured with a SaaS Project and a SaaS Data Space so that [!DNL Commerce Services] can send data to the right location. A SaaS Project groups all SaaS Data Spaces. The SaaS Data Spaces are used to collect and store data that enables [!DNL Commerce Services] to work. Some of this data may be exported from the [!DNL Commerce] instance and some may be collected from shopper behavior on the storefront. That data is then persisted to secure cloud storage.

For [!DNL Product Recommendations], the SaaS data space contains catalog and behavioral data. You can point a [!DNL Commerce] instance to a SaaS data space by [selecting it](https://docs.magento.com/user-guide/configuration/services/saas.html) in the [!DNL Commerce] configuration.

>[!WARNING]
>
>Use your production SaaS data space only on your production [!DNL Commerce] installation to avoid data collisions. Otherwise, you risk polluting your production site data with testing data, which causes deployment delays. For example, your production product data could be mistakenly overwritten from staging data, such as staging URLs.

### Select or create a SaaS project {#createsaasenv}

>[!NOTE]
>
>If you do not see the **Commerce Services Connector** section in the [!DNL Commerce] configuration, you must install the [!DNL Commerce] modules for your desired [!DNL Commerce Service], such as [Product Recommendations](./recommendations/install-configure.md).

To select or create a SaaS project, request the [!DNL Commerce] API key from the [!DNL Commerce] license holder for your store.

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.

1. In the left panel, expand **Services** and choose **Commerce Services Connector**.

1. In the _API Keys_ section, paste your key values for the **Production API Key** and the **Production Private Key**.

   Private keys must include `----BEGIN PRIVATE KEY---` at the beginning of the key and `----END PRIVATE KEY----` at the end of the private key.

1. Click **Save Config**.

  Any SaaS projects that are associated with your API key appear in the **SaaS Project** field.

1. If no SaaS projects exist, click **Create Project**. Then in the **Project Name** field, enter a name for your SaaS project.

   When you create a SaaS project, [!DNL Commerce] generates one or more SaaS data spaces depending on your [!DNL Commerce] license:
   - Adobe Commerce - One production data space; two testing data spaces
   - Magento Open Source - One production data space; no testing data spaces

1. Select the **SaaS Data Space** to use for the current configuration of your [!DNL Commerce] store.

>[!WARNING]
>
>If you generate new keys in the API Portal section of My Account, immediately update the API keys in the Admin configuration. If you generate new keys and do not update them in the Admin, your SaaS extensions no longer work and you lose valuable data.

To change the SaaS project or data space names, click the **Rename this Project** or **Rename Data Space** respectively.

## Catalog sync

When your [!DNL Commerce] instance successfully connects to [!DNL Commerce Services], the catalog sync process exports product data from your [!DNL Commerce] server to [!DNL Commerce Services]. [Learn more](catalog-sync.md) about the catalog sync process.
