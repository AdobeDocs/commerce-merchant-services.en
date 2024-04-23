---
title: "Get Started with [!DNL Live Search]"
description: "Learn the system requirements and installation steps for [!DNL Live Search] from Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
---
# Set up for success with [!DNL Live Search] and [!DNL Catalog Service]

This article provides step-by-step instructions for integrating Adobe Commerce [!DNL Live Search] and [!DNL Catalog Service] into your commerce platform.

When you install [!DNL Live Search] with [!DNL Catalog Service] you enable a fast, relevant, and intuitive search system that can personalize your customers' shopping experience.

[!DNL Live Search] also installs the Product Listing Page (PLP) widget, which provides robust filtering capabilities when browsing search results.

The Adobe Commerce side of the architecture includes hosting the search *Admin*, synchronizing catalog data, and running the query service. After [!DNL Live Search] is installed and configured, Adobe Commerce begins sharing search and catalog data with SaaS services. At this point, Admin users can set up, customize, and manage search [facets](facets.md), [synonyms](synonyms.md), and [merchandising rules](category-merch.md).

![Live Search Data Flow](assets/ls-cs-data-flow.png)

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

Review the following boundaries and limits to ensure that [!DNL Live Search] and [!DNL Catalog Service] meets the needs of your business.

### General

- The [Advanced Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
- [Tier Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) and [Special Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) are not supported in the [!DNL Live Search] field and Product Listing Page Widget.
- [!DNL Live Search] cannot aggregate inventory data from multiple sources.
- Product prices do not include value-added tax (VAT).
- Content search is not supported.
- There is a limit of 10k products that can be paginated.

### Indexing

- [!DNL Live Search] [indexes](indexing.md) up to a total of 450 product attributes per store view. These are distributed as follows:
   - 50 sortable attributes
   - 200 filterable attributes
   - 200 searchable attributes
- Indexes only products from the Adobe Commerce database.
- CMS pages are not indexed.

### Facets

- A maximum of 100 attributes can be configured as facets from the 200 filterable attributes that can be indexed.
- Within a facet, a maximum of 30 buckets can be returned. If more than 30 buckets need to be returned, [create a support ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) so Adobe can analyze the performance impact and determine if it is feasible to increase this limit for your environment.
- Dynamic facets can cause performance issues in large indexes and indexes with high ordinality. If you have created dynamic facets and notice any performance deterioration or page not loading with timeout errors, try changing your facets to pinned to determine if that resolves your performance issue.
- Stock status (`quantity_and_stock_status`) is not supported as a facet. You can use `inStock: 'true'` to filter out of stock products. This is supported out of the box in the `LiveSearchAdapter` module when "Display out of stock products" is set to "True" in the [!DNL Commerce] Admin.

### Query

- [!DNL Live Search] does not have access to the full taxonomy of the category tree, which makes some layered navigation search scenarios beyond its reach.
- [!DNL Live Search] uses a unique GraphQL endpoint for queries to support features such as dynamic faceting and search-as-you-type. Although similar to the [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/), there are a few differences and some fields may not be fully compatible.

### Rules

- The maximum number of search merchandising [rules](rules.md) per store view is 50.
- Category merchandising can have one rule per category.
- The maximum number of conditions per rule is 10.
- The maximum number of events per rule is 25.

### Synonyms

- [!DNL Live Search] can manage up to 200 [synonyms](synonyms.md) per store view.
- Multiword synonyms are not supported.

### Category merchandising

- One rule per category can be created for each store view. Each rule can have:
   - Up to ten conditions
   - Up to 25 events

### B2B and category permissions

- Products are not displayed if they are not added to a default shared catalog.
- To restrict customer groups using Catalog permissions:
   - Products must be assigned to the Root category.
   - The "Not Logged in" customer group must be given "Allow" browsing permissions.
   - To restrict products to the "Not Logged In" customer group, go to each category and set permission for each customer group.
- Support for B2B with Live Search for PWA Studio is not supported at this time.

## Workflow overview

At a high level, onboarding [!DNL Live Search] requires that you install the extension, sync your catalog data, then configure your data.

![Live Search Workflow](assets/livesearch-workflow.png)

### 1. Install the [!DNL Live Search] extension

[!DNL Live Search] is [installed](install.md) into your Adobe Commerce instance through [Composer](https://getcomposer.org/). This installs the required modules that connect to the service and configures the Commerce instance to override the default search field. It also installs Commerce Admin options for configuring the service.

### 2. Sync your catalog data

[!DNL Live Search] moves catalog data to Adobe's SaaS infrastructure. The data is indexed and search results are delivered from this index directly to the storefront. Depending on the size and complexity, indexing can take from 30 minutes to a couple of hours.

### 3. Configure the data

Getting your product data configured correctly ensures good search results for your customers. After you install and configure the extension, sync your data, you then assign categories and configure attributes.

## Install [!DNL Live Search]

[!DNL Live Search] is installed as an extension from [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html). After you install and configure [!DNL Live Search], Adobe [!DNL Commerce] begins sharing search and catalog data with SaaS services. At this point, *Admin* users can set up, customize, and manage search facets, synonyms, and merchandising rules.

>[!NOTE]
>
>As of [!DNL Live Search] 3.0.2, the [!DNL Catalog Service] extension is bundled in with the [!DNL Live Search] installation.

After you install [!DNL Live Search], it appears on the *Marketing* menu under *SEO & Search* in the [!DNL Commerce] *Admin*.

### [!DNL Live Search] packages {#packages}

The [!DNL Live Search] extension consists of the following packages:

| Package | Description |
|--- |--- |
| `module-live-search` | Allows merchants to configure their search settings for faceting, synonyms, query rules, and so on, and provides access to a read-only GraphQL playground to test queries from the *Admin*. |
| `module-live-search-adapter` | Routes search requests from the storefront to the [!DNL Live Search] service and renders the results in the storefront. <br />- Category browse - Routes requests from the storefront [top navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) to the search service.<br />- Global search - Routes requests from the [quick search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) box in the upper-right of the storefront to the [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | A "search as you type" popover replaces the standard quick search and returns data and thumbnails of top search results. |

### [!DNL Live Search] dependencies {#dependencies}

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

### Before you begin {#before-you-begin}

Before you install [!DNL Live Search] with the [!DNL Catalog Service] extension, there are a few steps you need to complete in your existing Commerce instance.

1. Confirm that [cron jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) and [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are running.

   >[!IMPORTANT]
   >
   >Due to the Elasticsearch 7 end-of-support announcement for August 2023, it is recommended that all Adobe Commerce customers migrate to the OpenSearch 2.x search engine. For information about migrating your search engine during a product upgrade, see [Migrating to OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) in the _Upgrade Guide_.

1. Choose your installation method:

   - **Install without OpenSearch** - Storefront operations are interrupted while the [!DNL Live Search] service indexes all products in the catalog. During the installation, [!DNL Live Search] modules are enabled and [!DNL OpenSearch] modules are disabled.
   - **Install with OpenSearch** - [!DNL OpenSearch] temporarily manages search requests from the storefront while the [!DNL Live Search] service indexes all products in the background, without any interruption to normal storefront operations. [!DNL OpenSearch] is disabled and [!DNL Live Search] is enabled after all catalog data is indexed and synchronized.

## Method 1: Install without OpenSearch {#method-1}

This onboarding method is recommended when installing [!DNL Live Search] to a:

- New [!DNL Commerce] installation
- Staging environment

1. Download the `live-search` package and run the following from the command line:

   ```bash
   composer require magento/live-search
   ```

1. Run the following commands to disable [!DNL OpenSearch] and related modules, and install [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > While the data is indexed and synchronized, the search and category browse operations are not available in the storefront. Depending on the size of your catalog, the process can take at least an hour from the time `cron` runs to synchronize your data to [!DNL Live Search] services.

1. Verify that the following [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are set to "Update by Schedule":

   - Product Feed
   - Product Variant Feed
   - Catalog Attributes Feed
   - Product Prices Feed
   - Scopes Website Data Feed
   - Scopes Customer Groups Data Feed
   - Categories Feed
   - Category Permissions Feed

1. Configure your [API keys](#configure-api-keys) and verify that your catalog data is [synchronized](#synchronize-catalog-data) with [!DNL Live Search] services.

1. To make facets available as filters in the storefront, add the [facets](facets-add.md) you need, according to the [faceting requirements](facets.md).

   You should be able to add facets after `cron` runs the attribute feeds and exports attribute metadata.

1. Run the following command in this order:

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

1. [Verify](#verify-export) that the data was exported.

1. [Test](#test-the-connection) the connection from the storefront.

## Method 2: Install with OpenSearch {#method-2}

This onboarding method is recommended when installing [!DNL Live Search] to:

- An existing production [!DNL Commerce] installation

1. Download the `live-search` package and run the following from the command line:

   ```bash
   composer require magento/live-search
   ```

1. Run the following command to temporarily disable the [!DNL Live Search] modules that serve storefront search results.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] continues to manage search requests from the storefront while the [!DNL Live Search] service synchronizes catalog data and indexes products in the background.

1. Verify that the following [indexers](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) are set to "Update by Schedule":

   - Product Feed
   - Product Variant Feed
   - Catalog Attributes Feed
   - Product Prices Feed
   - Scopes website data Feed
   - Scopes customer groups data Feed

1. Configure your [API keys](#configure-api-keys) and verify that your catalog data is [synchronized](#synchronize-catalog-data) with [!DNL Live Search] services.

1. To make facets available as filters in the storefront, add the [facets](facets-add.md) you need, according to the [faceting requirements](facets.md).

   You should be able to add facets after `cron` runs the product and attribute feeds and exports attribute metadata to [!DNL Live Search] services.

1. Run the following command in this order:

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

1. After the sync is complete, use the [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) with the default query to verify the following:

   - The returned product count is close to what you expect for the store view.
   - Facets are returned.

1. Run the following commands to enable [!DNL Live Search] modules, disable [!DNL OpenSearch], and run `setup`.

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

1. [Test](#test-the-connection) the connection from the storefront.

You have now installed [!DNL Live Search] with [!DNL Catalog Service] based on your chosen method. In the next section, you sync your catalog data.

## Sync data {#synchronize-catalog-data}

Before you can sync the catalog data, you must configure the API keys.

### Configure API keys {#configure-api-keys}

The Adobe Commerce API key and its associated private key are required to connect [!DNL Live Search] to an installation of Adobe Commerce. The API key is generated and maintained in the account of the [!DNL Commerce] license holder, who can share it with the developer or SI. The developer can then create and manage the SaaS Data Spaces on behalf of the license holder. If you already have a set of API keys, you do not need to regenerate them.

#### Adobe Commerce license holder

To generate an API key and private key, refer to [Commerce Services Connector](../landing/saas.md).

#### Adobe Commerce developer or SI

The developer or SI configures the SaaS data space as described in the *Commerce Services* section of the configuration. In the *Admin*, Commerce Services becomes available in the **Configuration** sidebar when a SaaS module is installed.

### Monitor sync progress

[!DNL Live Search] requires synchronized product data for search operations, and synchronized attribute data to configure facets. The initial synchronization between the product catalog and the [!DNL Catalog Service] begins when [!DNL Live Search] is first connected. Depending on the installation method and size of the catalog, it can take up to 30 minutes for the data to be exported and indexed by [!DNL Live Search].

You can view the data that is synchronized and shared with the [!DNL Catalog Service] using the [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). This dashboard provides valuable insights into the availability of product data for your storefront, ensuring it can be promptly displayed to your shoppers.

![Data Management Dashboard](assets/data-management-dashboard.png)

#### Verify export {#verify-export}

To verify that the catalog data has been exported from your Adobe Commerce instance and is synchronized for [!DNL Live Search], look for entries in the following tables:

- `catalog_data_exporter_products`
- `catalog_data_exporter_product_attributes`

For additional help, refer to [[!DNL Live Search] catalog not synchronized](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in the Support Knowledge Base.

#### Future product updates

After the initial synchronization, it can take up to 15 minutes for incremental product updates to become available to storefront search. To learn more, go to [Indexing - Streaming Product Updates](indexing.md).

## Post installation configuration

In this section, you set the store view where the Live Search storefront features are configured, enable the product listing widgets, assign categories, and assign attributes.

### Set the store view

[!DNL Live Search] storefront features are configured within the store view scope. To set the store view where you want the Live Search features to appear, launch [!DNL Live Search] from the *Admin* and go to **[!UICONTROL Marketing]** > _[!UICONTROL SEO and Search]_ > **[!UICONTROL [!DNL Live Search]]**. Under **[!UICONTROL Scope]**, select the store view.

![Select Live Search Store View](assets/ls-set-scope.png)

All configurations you set on the Live Search page pertain to the selected store view.

### Enable Product Listing Widgets

When you install [!DNL Live Search] 4.0.0+, Product Listing Widgets are enabled. When widgets are enabled, a different UI component is used for the search results page and category browse Product Listing Page. This UI component makes direct calls to the [Catalog Service API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), which results in faster response times.

If you have a version older than 4.0.0+, you need to manually enable the Product Listing Widget.

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

## Test the connection {#test-connection}

In the storefront, verify the following:

- The [!UICONTROL Search] box returns results correctly
- Category browse returns results correctly
- Facets are available as filters on search results pages

If everything works correctly, congratulations! [!DNL Live Search] is installed, connected, and ready to use.

If you encounter problems in the storefront, check the `var/log/system.log` file for API communication failures or errors on the services side.

To allow Live Search through a firewall, add `commerce.adobe.io` to the allowlist.

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
