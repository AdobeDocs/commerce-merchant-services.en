---
title: "Get Started with [!DNL Live Search]"
description: "Learn the system requirements and installation steps for [!DNL Live Search] from Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
---
# Set up for success with [!DNL Live Search] and [!DNL Catalog Service]

This article provides step-by-step instructions for integrating Adobe Commerce [!DNL Live Search] and [!DNL Catalog Service] into your commerce platform.

When you install [!DNL Live Search] with [!DNL Catalog Service] you enable a fast, relevant, and intuitive search system that can personalize your customers' shopping experience.

## Audience

This article is intended for the developer or systems integrator on your team who is responsible for installing and configuring your Adobe Commerce instance.

## Requirements

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## Supported platforms

- Adobe Commerce on-prem (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

## Boundaries and limits

Review the [boundaries and limits](boundaries-limits.md) to ensure that [!DNL Live Search] and [!DNL Catalog Service] meet the needs of your business.

## Workflow overview

At a high level, onboarding [!DNL Live Search] requires that you:

- Install the extension
- Configure your API keys
- Sync your catalog data
- Verify the data was exported
- Configure your data
- Test the connection
- Customize for your storefront

![Live Search Workflow](assets/livesearch-workflow.png)

## 1. Install the [!DNL Live Search] extension

[!DNL Live Search] is installed as an extension from [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) through [Composer](https://getcomposer.org/). After you install and configure [!DNL Live Search], Adobe [!DNL Commerce] begins sharing search and catalog data with SaaS services. At this point, *Admin* users can set up, customize, and manage search facets, synonyms, and merchandising rules.

>[!NOTE]
>
>As of [!DNL Live Search] 3.0.2, the [!DNL Catalog Service] extension is bundled in with the [!DNL Live Search] installation.

1. Confirm that [cron jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) and [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are running.

   >[!IMPORTANT]
   >
   >Due to the Elasticsearch 7 end-of-support announcement for August 2023, it is recommended that all Adobe Commerce customers migrate to the OpenSearch 2.x search engine. For information about migrating your search engine during a product upgrade, see [Migrating to OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) in the _Upgrade Guide_.

1. Download the `live-search` package from the [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Run the following from the command line:

   ```bash
   composer require magento/live-search
   ```

   If you are adding the [!DNL Live Search] extension to a **new** Adobe Commerce installation, run the following to disable [!DNL OpenSearch] and related modules, and install [!DNL Live Search]. Then proceed to step 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   If you are adding the [!DNL Live Search] extension to an **existing** Adobe Commerce installation, run the following to temporarily disable the [!DNL Live Search] modules that serve storefront search results then proceed to step 4:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] continues to manage search requests from the storefront while the [!DNL Live Search] service synchronizes catalog data and indexes products in the background.

1. Run the following:

   ```bash
   bin/magento setup:upgrade
   ```

1. Verify that the following [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are set to "Update by Schedule":

   - Product Feed
   - Product Variant Feed
   - Catalog Attributes Feed
   - Product Prices Feed
   - Scopes Website Data Feed
   - Scopes Customer Groups Data Feed
   - Categories Feed
   - Category Permissions Feed

1. If you are installing [!DNL Live Search] on a new Commerce instance, you are done and can skip to the [2. Configure API keys](#2-configure-api-keys) section. If you are installing Live Search to an existing Commerce instance, proceed to the next step.

1. Run the following commands to enable the [!DNL Live Search] extension, disable [!DNL OpenSearch], and run `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

 If you are installing [!DNL Live Search] on an existing Commerce instance, you are done and can proceed to the [2. Configure API keys](#2-configure-api-keys) section.

## 2. Configure API keys

The Adobe Commerce API key and its associated private key are required to connect [!DNL Live Search] to an installation of Adobe Commerce. The API key is generated and maintained in the account of the [!DNL Commerce] license holder, who can share it with the developer or SI. The developer can then create and manage the SaaS Data Spaces on behalf of the license holder. If you already have a set of API keys, you do not need to regenerate them.

Learn how to configure your API keys in the [Commerce Services Connector](../landing/saas.md) article.

## 3. Sync your catalog data {#synchronize-catalog-data}

[!DNL Live Search] moves catalog data to Adobe's SaaS infrastructure. The data is indexed and search results are delivered from this index directly to the storefront. Depending on the size and complexity, indexing can take from 30 minutes to a couple of hours.

To begin the initial sync of your catalog data to SaaS services, run the following commands in this order:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

When you run these commands, the initial sync of your catalog data to SaaS services begins.

>[!WARNING]
>
> While the data is indexed and synchronized, the search and category browse operations are not available in the storefront. Depending on the size of your catalog, the process can take at least an hour from the time `cron` runs to synchronize your data to SaaS services.

With your catalog data now available in SaaS, you can make facets [available as filters](facets-add.md) in the storefront, according to the [faceting requirements](facets.md).

### Monitor sync progress

[!DNL Live Search] requires synchronized product data for search operations, and synchronized attribute data to configure facets. The initial synchronization between the product catalog and the [!DNL Catalog Service] begins when [!DNL Live Search] is first connected.

You can view the data that is synchronized and shared with the [!DNL Catalog Service] using the [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). This dashboard provides valuable insights into the availability of product data for your storefront, ensuring it can be promptly displayed to your shoppers.

![Data Management Dashboard](assets/data-management-dashboard.png)

#### Future product updates

After the initial synchronization, it can take up to 15 minutes for incremental product updates to become available to storefront search. To learn more, see [Indexing - Streaming Product Updates](indexing.md).

## 4. Verify the data was exported {#verify-export}

To verify that the catalog data has been exported from your Adobe Commerce instance and is synchronized for [!DNL Live Search], you have a couple of options:

- Look for entries in the following tables:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Use the [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) with the default query to verify the following:

   - The returned product count is close to what you expect for the store view.
   - Facets are returned.

For additional help, see [[!DNL Live Search] catalog not synchronized](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in the Support Knowledge Base.

## 5. Configure the data

Getting your product data configured correctly ensures good search results for your customers. In this section, you enable the product listing widgets and assign categories and attributes.

### Enable Product Listing Widgets

When you install [!DNL Live Search] 4.0.0+, Product Listing Widgets are enabled by default. When widgets are enabled, a different UI component is used for the search results page and category browse Product Listing Page. This UI component makes direct calls to the [Catalog Service API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), which results in faster response times.

If you have a [!DNL Live Search] version older than 4.0.0+, you need to manually enable the Product Listing Widget.

1. From the *Admin*, go to **[!UICONTROL Stores]** > _[!UICONTROL Settings]_ > **[!UICONTROL Configuration]**.
1. Under **[!UICONTROL Live Search]**, select **[!UICONTROL Storefront Features]**.
1. Set **[!UICONTROL Enable Product Listing Widgets]** to `Yes`.

   ![Enable Product Listing Widgets](assets/ls-admin-enable-widget.png)

When you change this configuration, the message `Page cache is invalidated` appears. You need to flush the Magento Cache to save your change.

1. Access the [Cache Management](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) page by doing one of the following:

   - Click the **[!UICONTROL Cache Management]** link in the message above the workspace.
   - On the _Admin_ sidebar, go to **[!UICONTROL System]** > _[!UICONTROL Tools]_ > **[!UICONTROL Cache Management]**.

1. Select the **Configuration** [!UICONTROL Cache Type] and click **[!UICONTROL Flush Magento Cache]**.

   Changes to the storefront are immediate after you flush the cache.

### Assign categories

Products returned in [!DNL Live Search] must be assigned to a [category](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). In Luma, for example, products are put into categories such as "Men", "Women", and "Gear". Subcategories are also set up for "Tops", "Bottoms", and "Watches". This allows for better granularity when filtering.

### Searchable and filterable fields

Products are assigned [attributes](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) that can be used for searching and filtering. Attributes are things such as "Color", "Size", "Material Type". With these attributes, users can look for "green tops". Each product may have many attributes defined in the [!DNL Commerce] Admin.

Each of these attributes can be defined as ["searchable"](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) in the Admin. When set as "searchable", those attributes are available to be searched by [!DNL Live Search].

[Facets](facets.md) are product attributes that are defined in [!DNL Live Search] to be filterable. Any filterable attribute may be set as a facet in [!DNL Live Search] but there are limits to how many facets can be searched at one time.

[Synonyms](synonyms.md) are terms that you can define to help guide users to the correct product. Users looking for pants might type in "trousers" or "slacks". You can set synonyms so that these search terms will get users to the "pants" results.

## 6. Test the connection {#test-connection}

In the storefront, verify the following:

- The [!UICONTROL Search] box returns results correctly
- Category browse returns results correctly
- Facets are available as filters on search results pages

If everything works correctly, congratulations! [!DNL Live Search] is installed, connected, and ready to use.

If you encounter problems in the storefront, check the `var/log/system.log` file for API communication failures or errors on the services side.

To allow [!DNL Live Search] through a firewall, add `commerce.adobe.io` to the allowlist.

## 7. Customize for your storefront

You have installed, synced, validated, and configured your data. Now, you can customize the look and feel of the [!DNL Live Search] Product Listing Page Widget and Storefront Popover to conform to your company's branding guidelines.

- [Product Listing Page Widget](plp-styling.md#styling-example)
- [Popover](storefront-popover-styling.md)

## Updating [!DNL Live Search] {#update}

Before updating Live Search, run the following from the command line to check the version of Live Search that is installed:

```bash
composer show magento/module-live-search | grep version
```

To update [!DNL Live Search], run the following from the command line:

```bash
composer update magento/live-search --with-dependencies
```

To update to a major version such as from 3.1.1 to 4.0.0, edit the project's root [!DNL Composer] `.json` file as follows:

1. If your currently installed `magento/live-search` version is `3.1.1` or below, and you are upgrading to version `4.0.0` or higher, run the following command before the upgrade:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   For information about the currently installed `magento/live-search` version, run the following command:

   ```bash
   composer show magento/live-search
   ```

1. Open the root `composer.json` file and search for `magento/live-search`.

1. In the `require` section, update the version number as follows:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Save*- `composer.json`. Then, run the following from the command line:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Uninstalling [!DNL Live Search] {#uninstall}

To uninstall [!DNL Live Search], refer to [Uninstall modules](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

The [!DNL Live Search] extension consists of the following packages:

| Package | Description |
|--- |--- |
| `module-live-search` | Allows merchants to configure their search settings for faceting, synonyms, query rules, and so on, and provides access to a read-only GraphQL playground to test queries from the *Admin*. |
| `module-live-search-adapter` | Routes search requests from the storefront to the [!DNL Live Search] service and renders the results in the storefront. <br />- Category browse - Routes requests from the storefront [top navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) to the search service.<br />- Global search - Routes requests from the [quick search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) box in the upper-right of the storefront to the [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | A "search as you type" popover replaces the standard quick search and returns data and thumbnails of top search results. |

## [!DNL Live Search] dependencies {#dependencies}

The following [!DNL Live Search] dependencies are captured by [!DNL Composer].
  
- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`
