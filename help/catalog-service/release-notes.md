---
title: '[!DNL Catalog Service] Release Notes'
description: The latest release information for [!DNL Catalog Service] for Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
---
# [!DNL Catalog Service] Release Notes

These release notes describe the latest versions of [!DNL Catalog Service].
Support is provided for the current major released version. Release notes for older versions are provided for reference.
Updates include:

![New](../assets/new.svg) New features
![Fix](../assets/fix.svg) Fixes and improvements
![Bug](../assets/bug.svg) Known issues

## Current major version

### V1.12 Release

_September 19, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Catalog Service now uses [SaaS price indexing](../price-index/index.md).
![Fix](../assets/fix.svg) This release contains bug fixes and improvements on the service side.

#### Known limitations

These features are not yet supported:

* Bundle products with fixed price
* Maximum size for dynamic attributes payload is 9 MB.
* Group product price. Can be calculated with simple product prices.
* In an image array, only the first image contains roles.

The following limitations can be solved by using the API Mesh and the Core GraphQL API:

* Minimum Advertised Price
* [Tier pricing](mesh.md)
* Downloadable products and gift cards

## Previous versions

+++ Previous versions

### V1.11 Release

_July 18, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Catalog Service now supports the [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) GraphQL query for Product Recommendations.

### V1.10 Release

_June 27, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Catalog Service API now supports "related products".

### V1.7 Release

_April 12, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Catalog Service now cleans up deleted product variants.
![Fix](../assets/fix.svg) Infrastructure scalability and performance improvements.

### V1.6 Release

_March 28, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Added swatches to the [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) query.
![New](../assets/new.svg) Added the ability to get `entityId` using [API Mesh](mesh.md).

### V1.5 Release

_March 6, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Added [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL functionality.
![Fix](../assets/fix.svg) Improved performance and API scalability.

### V1.4 Release

_February 7, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Published catalog-service metapackage to simplify installation steps.
![Fix](../assets/fix.svg) API scalability and performance improvements.

### V1.3 Release

_January 17, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Simplified and improved the onboarding experience.
![New](../assets/new.svg) New customer sandbox endpoints are available for pre-production testing.
![New](../assets/new.svg) Support added for virtual products.
![Fix](../assets/fix.svg) API scalability and performance improvements.

### V1.1 Release

_November 18, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Catalog Service now supports Adobe's [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Improved API scalability and overall performance.

### V1.0 Release

_October 4, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Now support bundled and grouped products.
![New](../assets/new.svg) Added B2B visibility overrides. Products are now searchable and can be added to the cart for specific customer groups.
![Fix](../assets/fix.svg) Service is now more stable and has improved performance.

### 0.3 Release - Beta+

_September 12, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) Images for variants support: product images are returned based on the selected options
![New](../assets/new.svg) Roles for prices support: allow only members of specific customer groups to see the price of products
![Fix](../assets/fix.svg) Improved stability and performance of the service
![New](../assets/new.svg) Updates are received when products are deleted from the catalog 

### Beta Release

_August 9, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) The `products` and `refineProduct` queries return the following data:

* Predefined (system) product attributes.
* Dynamic product attributes and filter them by role (product display page/product list page).
* Product options.
* Product images and filter them by role (PDP/PLP).
* A specific price for simple products and price ranges for configurable products.
* Customer group prices and price ranges. They return a fallback default price on shoppers without a customer group.
* Product types that use B2B customer-specific pricing.

+++
