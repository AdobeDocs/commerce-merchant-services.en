---
title: "[!DNL Live Search] Boundaries and Limits"
description: "Learn about the boundaries and limits for [!DNL Live Search] to ensure it meets the needs of your business."
role: Admin, Developer
---
# Boundaries and limits

Review the following boundaries and limits to ensure that [!DNL Live Search] and [!DNL Catalog Service] meet the needs of your business.

## General

- The [Advanced Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
- [Tier Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) and [Special Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) are not supported in the [!DNL Live Search] field and Product Listing Page Widget.
- [!DNL Live Search] cannot aggregate inventory data from multiple sources.
- Product prices do not include value-added tax (VAT).
- Content search is not supported.
- There is a limit of 10k products that can be paginated.

## Indexing

- [!DNL Live Search] [indexes](indexing.md) up to a total of 450 product attributes per store view. These are distributed as follows:
   - 50 sortable attributes
   - 200 filterable attributes
   - 200 searchable attributes
- Indexes only products from the Adobe Commerce database.
- CMS pages are not indexed.

## Facets

- A maximum of 100 attributes can be configured as facets from the 200 filterable attributes that can be indexed.
- Within a facet, a maximum of 30 buckets can be returned. If more than 30 buckets need to be returned, [create a support ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) so Adobe can analyze the performance impact and determine if it is feasible to increase this limit for your environment.
- Dynamic facets can cause performance issues in large indexes and indexes with high ordinality. If you have created dynamic facets and notice any performance deterioration or page not loading with timeout errors, try changing your facets to pinned to determine if that resolves your performance issue.
- Stock status (`quantity_and_stock_status`) is not supported as a facet. You can use `inStock: 'true'` to filter out of stock products. This is supported out of the box in the `LiveSearchAdapter` module when "Display out of stock products" is set to "True" in the [!DNL Commerce] Admin.

## Query

- [!DNL Live Search] does not have access to the full taxonomy of the category tree, which makes some layered navigation search scenarios beyond its reach.
- [!DNL Live Search] uses a unique GraphQL endpoint for queries to support features such as dynamic faceting and search-as-you-type. Although similar to the [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/), there are a few differences and some fields may not be fully compatible.
- The maximum number of results that can be retured in a search query is 10,000.

## Rules

- The maximum number of search merchandising [rules](rules.md) per store view is 50.
- Category merchandising can have one rule per category.
- The maximum number of conditions per rule is 10.
- The maximum number of events per rule is 25.

## Synonyms

- [!DNL Live Search] can manage up to 200 [synonyms](synonyms.md) per store view.
- Multiword synonyms are not supported.

## Category merchandising

- One rule per category can be created for each store view. Each rule can have:
   - Up to ten conditions
   - Up to 25 events

## B2B and category permissions

- Products are not displayed if they are not added to a default shared catalog.
- To restrict customer groups using Catalog permissions:
   - Products must be assigned to the Root category.
   - The "Not Logged in" customer group must be given "Allow" browsing permissions.
   - To restrict products to the "Not Logged In" customer group, go to each category and set permission for each customer group.
- Support for B2B with Live Search for PWA Studio is not supported at this time.
