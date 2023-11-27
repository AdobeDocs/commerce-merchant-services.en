---
title: "Implementation Overview"
description: "[!DNL Live Search] implementation flow overview"
recommendations: noCatalog
---
# Implementation Overview

[!DNL Live Search] for Adobe Commerce is a SaaS that provides performant, filterable and sortable search results for your online store.
This topic provides a high-level overview of how to install and configure [!DNL Live Search] for Adobe Commerce.

## [!DNL Live Search] components

[!DNL Live Search] consists of two components:

* Search Field/Popover - installing [!DNL Live Search] replaces the default search text field with a [!DNL Live Search] text field, which is delivered through the service in Javascript. Typing into this search field sends the query to the [!DNL Live Search] SaaS infrastructure and the results are returned within the [!DNL Live Search] popover widget, showing live results under the search text field.
* Product Listing Page (PLP) widget - When you click Enter to send the final search query, the search results are returned within the PLP widget, which is build and served from the Adobe SaaS infrastructure to your storefront. The PLP widget allows for filtering/faceting, depending on your store configuration.
* [!DNL Live Search] admin - Where you can define facets, synonyms and other [!DNL Live Search] features

## Workflow overview

[!DNL Live Search] works by moving catalog data to the Adobe Commerce SaaS infrastructure and building indexes that are used for quickly delivering search results as users type. 

### Installation

[!DNL Live Search] is [installed](install.md) into your Adobe Commerce instance through Composer. This installs the required modules that connect to the service and configures the Commerce instance to override the default search field. It also installs Commerce admin options for configuring the service.

### Sync data

[!DNL Live Search] moves catalog data to Adobe's SaaS infrastructure. The data is indexed and search results are delivered from this index directly to the storefront. Depending on the size and complexity, this can take from 30 minutes to a couple hours.

### Configure data

Getting your product data configured correctly ensures good search results for your customers. There are a couple setup steps required.

#### Categories

Product returned in [!DNL Live Search] must be assigned a [category](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). In Luma, for example, products are put into categories such as "Men", "Women", and "Gear". Sub-categories are also set up for "Tops", "Bottoms", and "Watches". This allows for better granularity when filtering.

#### Searchable and filterable fields

Products are assigned [attributes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) that can be used for searching and filtering. Attributes are things such as "Color", "Size", "Material Type". With these attributes, users can look for "green tops". Each product may have many attributes defined in the Commerce admin.

Each of these attributes can be defined as "searchable" in the admin. When set as "searchable", those attributes are available to be searched by [!DNL Live Search].

[Facets](facets.md) are product attributes that are defined in [!DNL Live Search] to be filterable. Any filterable attribute may be set as a facet in [!DNL Live Search] but there are limits to how many facets can be searched at one time.

[Synonyms](synonyms.md) are terms that you can define to help guide users to the correct product. Users looking for pants might type in "trousers" or "slacks". You can set synonyms so that these search terms will get users to the "pants" results.

## [!DNL Live Search] workspace

The [!DNL Live Search] [workspace](workspace.md) is the area in the admin where you configure [!DNL Live Search] features such as synonyms, facets and Category Merchandising.

## Customizing widgets

Most store owners will want to ensure that the [!DNL Live Search] widgets conform to their store look and feel.

The popover and PLP widgets can be styled by defining custom CSS rules as needed. See [Styling Popover Elements](storefront-popover-styling.md) and [Product Listing Page Widget](plp-styling.md).

If you wish to extend the functionality of the widgets, the source code for each is available in a public repo.
In this scenario, you can customize the javascript for your own needs and then host your custom code on your site. This custom script communicates with the [!DNL Live Search] service and returns the results like normal, allowing you to control the functionality of the widget.

* [PLP widget repo](https://github.com/adobe/storefront-product-listing-page)
* [Search bar repo](https://github.com/adobe/storefront-search-as-you-type)

Get more details about [!DNL Live Search] in the [Technical Overview](onboarding-overview.md).
