---
title: "Onboarding Overview"
description: "[!DNL Live Search] onboarding flow, system requirements, boundaries and limitations"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
---
# Onboarding Overview

To get started using [!DNL Live Search] for Adobe Commerce, complete the onboarding process to install the extension, configure your API keys, and synchronize your catalog.

## Onboarding flow

![[!DNL Live Search] onboarding diagram](assets/onboarding-flow.svg)

## Requirements {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Supported platforms

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Boundaries and thresholds

At this time, the [!DNL Live Search] search/category API has the following supported limits and static boundaries:

### Indexing

* Indexes up to 300 product attributes per store view
* Indexes only products from the Adobe Commerce database
* Does not index CMS pages

### Query

* [!DNL Live Search] does not have access to the full taxonomy of the category tree, which makes some layered navigation search scenarios beyond its reach.
* [!DNL Live Search] uses a unique GraphQL endpoint for queries to support features such as intelligent faceting and search-as-you-type. Although similar to the [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql), there are a few differences and some fields may not be fully compatible at this time.

### Rules

* Maximum number of rules per Data Space ID is 50.
* Maximum number of conditions per rule is 10.
* Maximum number of events per rule is 25.

### Synonyms

* [!DNL Live Search] can manage up to 200 synonyms per `Data Space ID`.

### PWA beta release

* The current beta PWA implementation of Live Search requires more processing time to return search results than Live Search with the native Commerce storefront.
* The beta release of PWA for [!DNL Live Search] does not support [event handling](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* The following product attributes are not supported by GraphQL when used in relation to the beta release of [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Not supported at this time

* The [Advanced Search](https://docs.magento.com/user-guide/catalog/search-advanced.html) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
* [Customer groups](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Custom price groups](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Multiple inventory locations as used by [MCOM](https://docs.magento.com/user-guide/mcom.html) or other OMS extensions
* [Integrated B2B capabilities](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* Product prices do not include [value added tax](https://docs.magento.com/user-guide/tax/vat.html) (VAT).
* Out-of-stock products appear in search results regardless of the [Stock Options](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) configuration.
