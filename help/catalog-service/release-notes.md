---
title: '[!DNL Catalog Service] Release Notes'
description: The latest release information for [!DNL Catalog Service] for Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
---
# [!DNL Catalog Service] Release Notes

These release notes describe the latest versions of [!DNL Catalog Service] and include:

*  ![New](../assets/new.svg) New features
*  ![Fix](../assets/fix.svg) Fixes and improvements
*  ![Bug](../assets/bug.svg) Known issues

## V1.0 Release

Release Date: 2022-10-04
Compatible with Adobe Commerce (EE): 2.4.x
Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
Stability: General Availability

![New](../assets/new.svg) Now support bundled and grouped products.
![New](../assets/new.svg) Added B2B visibility overrides. Products are now searchable and can be added to the cart for specific customer groups.
![Fix](../assets/fix.svg) Service is now more stable and has improved performance.

### Known limitations

These features are not yet supported:

*  Tier pricing
*  Updates are not received when variants are deleted from the catalog
*  Maximum size for the dynamic attributes payload is <9MB
*  Fixed price for bundle products
*  Total price for grouped products
*  Support for virtual, downloadable, and gift card product types
*  Minimum Advertised Price (MAP)

## 0.3 Release - Beta+

Release Date: 2022-09-12
Compatible with Adobe Commerce (EE): 2.4.x
Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
Stability: Beta

![New](../assets/new.svg) Images for variants support: product images are returned based on the selected options
![New](../assets/new.svg) Roles for prices support: allow only members of specific customer groups to see the price of products
![Fix](../assets/fix.svg) Improved stability and performance of the service
![New](../assets/new.svg) Updates are received when products are deleted from the catalog 

### Known limitations

These features are not yet supported:

*  Tier pricing
*  Bundle and grouped products
*  No updates are received when variants are deleted from the catalog
*  B2B visibility overrides: products can be searchable, or added to cart for specific customer groups

## Beta Release

Release Date: 2022-08-09
Compatible with Adobe Commerce (EE): 2.4.x
Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
Stability: Beta

![New](../assets/new.svg) The `products` and `refineProduct` queries return the following data:

*  Predefined (system) product attributes.
*  Dynamic product attributes and filter them by role (product display page/product list page).
*  Product options.
*  Product images and filter them by role (PDP/PLP).
*  A specific price for simple products and price ranges for configurable products.
*  Customer group prices and price ranges. They return a fallback default price on shoppers without a customer group.
*  Product types that use B2B customer-specific pricing.

### Known limitations

*  Bundle and grouped products are not supported.
*  Tier pricing is not supported.
*  In an array of images, only the first image contains roles.
*  Images for variants are not retrieved.
*  Updates are not received when products or variants are deleted from the catalog.
