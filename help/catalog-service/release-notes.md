---
title: "[!DNL Catalog Service] Release Notes"
description: "The latest release information for [!DNL Catalog Service] for Adobe Commerce."
---

# [!DNL Catalog Service] Release Notes

{{catalog-service-beta}}

These release notes describe the latest versions of [!DNL Catalog Service] and include:

* ![New](../assets/new.svg) - New features
* ![Fix](../assets/fix.svg) - Fixes and improvements
* ![Bug](../assets/bug.svg) - Known issues

## Beta Release

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Beta

* ![New](../assets/new.svg) - The `products` and `refineProduct` queries return the following data:
  * Predefined (system) product attributes.
  * Dynamic product attributes and filter them by role (product display page/product list page).
  * Product options.
  * Product images and filter them by role (PDP/PLP).
  * A specific price for simple products and price ranges for configurable products. 
  * Customer group prices and price ranges. They return a fallback default price on shoppers without a customer group.
  * Product types that use B2B customer-specific pricing.
