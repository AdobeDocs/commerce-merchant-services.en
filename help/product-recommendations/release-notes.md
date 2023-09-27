---
title: '[!DNL Product Recommendations] Release Notes'
description: The latest release information for [!DNL Product Recommendations] from Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
---
# [!DNL Product Recommendations] Release Notes

The release notes contain updates to the following [!DNL Product Recommendations] modules:

* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Page Builder support in [!DNL Product Recommendations] (optional) module: `magento/module-page-builder-product-recommendations`
* Visual similarity recommendation type support for [!DNL Product Recommendations] (optional) module: `magento/module-visual-product-recommendations`

Support is provided for the current major released version. Release notes for older versions are provided for reference.
The release notes include:

![New](../assets/new.svg) New features
![Fix](../assets/fix.svg) Fixes and improvements
![Bug](../assets/bug.svg) Known issues

See the developer documentation to [learn about product support](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Hosted service updates

These notes describe updates that were published outside of a versioned release or improvements to the hosted service.

+++Hosted service updates

 _July 18, 2023_

![New](../assets/new.svg) Product Recommendations now has a GraphQL [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) query.

 _April 25, 2023_

![New](../assets/new.svg) Product Recommendations customers can now take advantage of [SaaS price indexing](../price-index/index.md).

+++

## Current major version

### 5.0.1 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Added new modules to support the [Saas Price Indexer](../price-index/index.md).
![New](../assets/new.svg) Added new data export modules to support exporting more product types including bundled products and gift cards.

#### Known limitations

* The `websiteCode` value is incorrectly returned if it contains an underscore (_).

### Previous versions

+++5.0.0 and prior

### 5.0.0 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Updated Product Recommendations to support Adobe Commerce 2.4.6.
![New](../assets/new.svg) This is a major version release. [Edit](install-configure.md#update) the root `composer.json` file for your project. 

### 4.0.1 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![Fix](../assets/fix.svg) Previously, Product Recommendations would show an error when the display currency was switched to a non-default currency. Switching currencies now works properly.

### 4.0.0 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Added [readiness indicators](create.md) to help you visualize the training progress of each recommendation type.
![New](../assets/new.svg) This is a major version release. [Edit](install-configure.md#update) the root `composer.json` file for your project. This release also requires you to provide two API keys when installing and configuring Product Recommendations: [a production key and a sandbox key](../landing/saas.md).
![New](../assets/new.svg) [!DNL Product Recommendations] now supports Multi-Source Inventory (MSI). To use MSI, you must [install](install-configure.md#update) the `commerce-data-export` 102.2.0+ module.

#### Known limitations

* The `websiteCode` value is incorrectly returned if it contains an underscore (_).

### 3.3.7 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added PHP 8.1 support
![New](../assets/new.svg) Improved image resizing so that images sizing is handled more consistently in the reference display template

### 3.3.6 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Optimized [!DNL Product Recommendations] metapackage by explicitly listing the dependencies

### 3.3.5 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added [B2B support](onboarding.md#b2bsupport) in Product Recommendations
![New](../assets/new.svg) Added new feeds to [sync catalog data](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) to Commerce Services via the command line

### 3.3.3 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added new [recommendation types](type.md): Conversion (view to cart), Conversion (view to purchase), and Recently viewed. These new recommendation types are available in the `magento/product-recommendations` module 3.2.2 and later.
![Fix](../assets/fix.svg) Fixed an issue where Fastly's Web Application Firewall (WAF) was incorrectly blocking a cookie
![Fix](../assets/fix.svg) Fixed issue where products assigned to the non-default Store View were not being displayed in the _Recommendations Product Preview_ panel when creating a recommendation for that specific Store View
![Fix](../assets/fix.svg) Fixed issue where certain recommendation unit names in Page Builder prevented the recommendation unit to display on the storefront

### 3.3.2 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed missing dependency for B2B support

### 3.3.1 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added support for B2B customer group pricing. When you set a [price filter](filters.md) on a recommendation unit, B2B customers who are logged in see the customer group pricing set for the products displayed.

### 3.3.0 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added support for Adobe Client Data Layer to standardize behavioral data collection across Adobe Commerce features and services. See the [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) to learn more.

### 3.2.6 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed a JavaScript modal error
![Fix](../assets/fix.svg) Fixed an issue where Fastly's Web Application Firewall (WAF) was incorrectly blocking a cookie

### 3.2.5 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Renamed Magento Services to [Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) and improved usability in the Admin

### 3.2.4 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed the "Unable to retrieve configurable product options data" error when indexing product attributes

### 3.2.3 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed the "Unable to retrieve configurable product options data" error during Catalog Sync
![Fix](../assets/fix.svg) Fixed an issue where the store code was not being set correctly when you enabled the "Add store code to URL" configuration
![Fix](../assets/fix.svg) Improved detection of Admin Panel configuration changes to ensure that these changes are reflected in Catalog Sync data

### 3.2.2 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added the ability to [preview recommendation results](create.md) at creation time. This might require that you update your module to the latest version.
![New](../assets/new.svg) Added the ability to [monitor and manage](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) the catalog sync process from the Admin.
![New](../assets/new.svg) Added [filters](filters.md) to control which products are displayed in recommendations.
![New](../assets/new.svg) Added the [Visual similarity](type.md#visualsim) recommendation type.

### 1.2.1 of magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added support for the 3.2.0+ version of the `magento/product-recommendations` module

### 3.1.0 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added the ability to [resync](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) your catalog to SaaS services via command line.
![New](../assets/new.svg) Added support for database table prefixes
![Fix](../assets/fix.svg) Removed PHP 7.1 support

### 3.0.8 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed an issue where events were sent for data collection before the module was configured, causing invalid traffic

### 3.0.6 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) **(Beta)** Includes support for new [Visual similarity](type.md#visualsim) recommendation type.

### 1.0.0 of magento/module-visual-product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) **(Beta)** [Visual similarity](type.md#visualsim). With the _Visual similarity_ recommendation type, you can deploy a recommendation unit to your product detail page that displays products that are visually similar to the product being viewed.

### 3.0.5 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Fixed the "Unable to retrieve product options data" error that could occur during catalog export.
![Fix](../assets/fix.svg) The currency symbol in the _Revenue_ column on the _Product Recommendations_ dashboard now correctly reflects the configured base currency.

### 3.0.4 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Added support for Adobe Commerce 2.4.0

### 3.0.3 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) Improved symbol implementation in storefront template

### 1.0.4 of magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added Product Recommendation name when editing the Page Builder content type

### 3.0.2 magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Added a status column on the grid when selecting Recommendation units in Page Builder
![Fix](../assets/fix.svg) Fixed an issue with incorrect http/https protocols in product and image URLs

### 3.0.1 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

This is a major version release. [Edit](install-configure.md#update) your project's root composer.json file.

![New](../assets/new.svg) Fetch [!DNL Product Recommendations] from alternate SaaS Data Spaces. This allows you to use product recommendations computed in your product environment on other, non-production environments. [Switching SaaS Data Spaces](settings.md) further describes this feature.

![Fix](../assets/fix.svg) Fixed an issue where checkout was inhibited for shoppers using uBlock Origin
![Fix](../assets/fix.svg) Fixed an issue sending extraneous add-to-cart events

### 1.0.3 of magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Page Builder support. With the Page Builder integration, you can accurately and granularly place Recommendation units in any arbitrary location on Page Builder-authored content. You can also style the headings and recommendation units themselves. Go to [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) for more information.

### 2.0.0 of magento/product-recommendations

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) General availability release!

+++

## Documentation

To learn more about [!DNL Product Recommendations] and [!DNL Product Recommendations] development:

* [User Guide](overview.md)
* [Developer Documentation](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
