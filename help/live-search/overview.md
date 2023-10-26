---
title: Introduction to [!DNL Live Search]
description: "[!DNL Live Search] from Adobe Commerce delivers a lightning fast, super-relevant, and intuitive search experience."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
---
# Introduction to [!DNL Live Search]

[!DNL Live Search] is a service for Adobe Commerce that replaces the standard search capabilities. The [!DNL Live Search] module is installed with Composer and connects your [!DNL Commerce] installation to the [!DNL Live Search] [service](../landing/saas.md). When it is configured, the default search text field is replaced with the [!DNL Live Search] text field.

[!DNL Live Search] appears on the *Marketing* menu under *SEO & Search* in the [!DNL Commerce] *Admin*.

The Adobe Commerce side of the architecture includes hosting the search *Admin*, synchronizing catalog data, and running the query service. After [!DNL Live Search] is installed and configured, Adobe Commerce begins sharing search and catalog data with SaaS services. At this point, Admin users can set up, customize, and manage search [facets](facets.md), [synonyms](synonyms.md), and [merchandising rules](category-merch.md).

![Live Search architecture diagram](assets/architecture-diagram.svg)

## Live Search components

* [!DNL Live Search] [popover](storefront-popover.md) is the box that opens under the search field that contains the search results.
* [Product Listing Page widget](plp-styling.md) provides a searchable product listing page with facets and synonym support.
* AEM CIF components: The [Popover widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) and the [PLP Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) allow AEM sites to take advantage of [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) is where rules, facets, and synonyms are configured.
* The Search Adapter is the default implementation of [!DNL Live Search].

## [!DNL Live Search] demo

Watch this video to learn about [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

For a more in-depth video of how to use and configure Live Search, see the [Full Demonstration on [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) topic.
