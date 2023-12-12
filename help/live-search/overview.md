---
title: Introduction to [!DNL Live Search]
description: "[!DNL Live Search] from Adobe Commerce delivers a lightning fast, super-relevant, and intuitive search experience."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
---
# Introduction to [!DNL Live Search]

[!DNL Live Search] is a service for Adobe Commerce that replaces the standard search capabilities. The [!DNL Live Search] module is installed with Composer and connects your [!DNL Commerce] installation to the [!DNL Live Search] [service](../landing/saas.md). When it is configured, the default search text field is replaced with the [!DNL Live Search] text field. [!DNL Live Search] also installs the Product Listing Page (PLP) widget which provides robust filtering capabilities when browsing search results.

[!DNL Live Search] appears on the *Marketing* menu under *SEO & Search* in the [!DNL Commerce] *Admin*.

The Adobe Commerce side of the architecture includes hosting the search *Admin*, synchronizing catalog data, and running the query service. After [!DNL Live Search] is installed and configured, Adobe Commerce begins sharing search and catalog data with SaaS services. At this point, Admin users can set up, customize, and manage search [facets](facets.md), [synonyms](synonyms.md), and [merchandising rules](category-merch.md).

## Live Search components

* [!DNL Live Search] [popover widget](storefront-popover.md) is the box that opens under the search field that contains the search results.
* [Product Listing Page widget](plp-styling.md) provides a searchable product listing page with facets and synonym support.
* AEM CIF components: The [Popover widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) and the [PLP Widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) allow AEM sites to take advantage of [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) is where rules, facets, and synonyms are configured.

## Workflow overview

[!DNL Live Search] works by moving catalog data to the Adobe Commerce SaaS infrastructure and building indexes that are used for quickly delivering search results as users type. 

### 1. Installation

[!DNL Live Search] is [installed](install.md) into your Adobe Commerce instance through [Composer](https://getcomposer.org/). This installs the required modules that connect to the service and configures the Commerce instance to override the default search field. It also installs Commerce Admin options for configuring the service.

### 2. Sync data

[!DNL Live Search] moves catalog data to Adobe's SaaS infrastructure. The data is indexed and search results are delivered from this index directly to the storefront. Depending on the size and complexity, indexing can take from 30 minutes to a couple hours.

### 3. Configure data

Getting your product data configured correctly ensures good search results for your customers. There are a couple setup steps required: assigning categories and configuring attributes.

#### Assign categories

Product returned in [!DNL Live Search] must be assigned a [category](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). In Luma, for example, products are put into categories such as "Men", "Women", and "Gear". Subcategories are also set up for "Tops", "Bottoms", and "Watches". This allows for better granularity when filtering.

#### Searchable and filterable fields

Products are assigned [attributes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) that can be used for searching and filtering. Attributes are things such as "Color", "Size", "Material Type". With these attributes, users can look for "green tops". Each product may have many attributes defined in the Commerce admin.

Each of these attributes can be defined as ["searchable"](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) in the admin. When set as "searchable", those attributes are available to be searched by [!DNL Live Search].

[Facets](facets.md) are product attributes that are defined in [!DNL Live Search] to be filterable. Any filterable attribute may be set as a facet in [!DNL Live Search] but there are limits to how many facets can be searched at one time.

[Synonyms](synonyms.md) are terms that you can define to help guide users to the correct product. Users looking for pants might type in "trousers" or "slacks". You can set synonyms so that these search terms will get users to the "pants" results.

## [!DNL Live Search] workspace

The [!DNL Live Search] [workspace](workspace.md) is the area in the Amin where you configure [!DNL Live Search] features such as synonyms, facets, and Category Merchandising.

## Events

[!DNL Live Search] uses [events](events.md) to calculate [Intelligent Merchandising](category-merch.md) and [performance](performance.md) dashboards. Eventing is provided with default implementations. Eventing for headless storefronts should be manually enabled.

## Customizing widgets

Most store owners will want to ensure that the [!DNL Live Search] widgets conform to their store look and feel.

The popover and PLP widgets can be styled by defining custom CSS rules as needed. See [Styling Popover Elements](storefront-popover-styling.md) and [Product Listing Page Widget](plp-styling.md).

If you wish to extend the functionality of the widgets, the source code for each is available in a public repo.
In this scenario, you can customize the JavaScript for your own needs and then host your custom code on your site. This custom script communicates with the [!DNL Live Search] service and returns the results like normal, allowing you to control the functionality of the widget.

* [PLP widget repo](https://github.com/adobe/storefront-product-listing-page)
* [Search bar repo](https://github.com/adobe/storefront-search-as-you-type)

Get more details about [!DNL Live Search] in the [Technical Overview](technical-overview.md).

## [!DNL Live Search] demo

Watch this video to learn about [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

For a more in-depth video of how to use and configure Live Search, see the [Full Demonstration on [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) topic.
