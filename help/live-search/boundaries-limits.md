---
title: 'Boundaries and Limits'
description: Learn about the boundaries and limits for [!DNL Live Search] to ensure it meets the needs of your business.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
---
# Boundaries and limits

When it comes to site search, Adobe Commerce gives you options. Review the following boundaries and limits to ensure that [!DNL Live Search] and [!DNL Catalog Service] meet the needs of your business. If you need advanced search capabilities such as content search, bring-your-own-algorithm (BYOA), or attribute-based merchandising, consider a third-party search solution.

## General

- The [Advanced Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) module is disabled when [!DNL Live Search] is installed, and the Advanced Search link in the storefront footer is removed.
- [Tier Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) and [Special Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) are not supported in the [!DNL Live Search] field and Product Listing Page Widget.
- Product prices do not include value-added tax (VAT).
- Content search is not supported.
- There is a limit of 10k products that can be paginated. While this limit can be increased, it can impact performance. Make sure you provide meaningful ways to filter products in case a category or search result has a large number of products so that shoppers do not have to use deep pagination.
- There is a hard limit of 1MB per attribute, including description and custom attributes.
- The search adapter does not support product attributes that are created with a custom source model and used as facets. To support this functionality, you must use the [Product Listing Page Widget](plp-styling.md).
- Custom product types are not supported.

## Indexing

- [!DNL Live Search] [indexes](indexing.md) up to a total of 450 product attributes per store view. These are distributed as follows:
   - 50 sortable attributes
   - 200 filterable attributes
   - 200 searchable attributes
- [!DNL Live Search] indexes only products from the Adobe Commerce database.
- CMS pages are not indexed.
- SKU, name, and category attributes are searchable by default and cannot be excluded from the search. Make sure you unassign the products from the categories if they are not intended to be in those categories.

## Facets

- A maximum of 100 attributes can be configured as facets from the 200 filterable attributes that can be indexed.
- Within a facet, a maximum of 100 buckets can be returned. If you need to return more than 100 buckets, [create a support ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) so Adobe can analyze the performance impact and determine if it is feasible to increase this limit for your environment.
- Dynamic facets can cause performance issues in large indexes and indexes with high ordinality. If you have created dynamic facets and notice any performance deterioration or page not loading with timeout errors, try changing your facets to pinned to determine if that resolves your performance issue.
- Stock status (`quantity_and_stock_status`) is not supported as a facet. You can use `inStock: 'true'` to filter out of stock products. This is supported out of the box in the `LiveSearchAdapter` module when "Display out of stock products" is set to "True" in the [!DNL Commerce] Admin.
- Date type attributes are not supported as a facet.

## Query

- [!DNL Live Search] uses a unique [GraphQL endpoint](https://developer.adobe.com/commerce/services/graphql/live-search/) for queries to support features such as dynamic faceting and search-as-you-type. Although similar to the [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/), there are a few differences and some fields may not be fully compatible.
- The maximum number of results that can be returned in a search query is 10,000.
- It is not possible to filter results using a date type attribute.

## Rules

- The maximum number of search merchandising [rules](rules.md) per store view is 50.
- Category merchandising can have one rule per category.
- The maximum number of conditions per rule is 10.
- The maximum number of events per rule is 25.
- To avoid unpredictable results in paginated responses, the number of pinned products should not exceed the requested page size.

## Synonyms

- [!DNL Live Search] can manage up to 200 [synonyms](synonyms.md) per store view.
- Multiword synonyms might not always work as expected. Be sure to test these synonyms in the staging environment before using them in production, as they can potentially have an adverse effect on relevancy.

## Category merchandising

- One rule per category can be created for each store view. Each rule can have:
   - Up to ten conditions
   - Up to 25 events

## B2B and category permissions

- Products are not displayed if they are not added to a default shared catalog.
- To restrict customer groups using [category permissions](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions):
   - Products must be assigned to the root category.
   - The "Not Logged in" customer group must be given "Allow" browsing permissions.
   - To restrict products to the "Not Logged In" customer group, go to each category and set permission for each [customer group](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- Out-of-the-box support for B2B with the PLP widget on PWA Studio is not supported at this time. However, you can [use the API](install.md#pwa-support) to implement this functionality.
- Category facets in [!DNL Live Search] might display categories that are not displayable to a specific [customer group](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- [!DNL Live Search] can support up to 1,000 customer groups.

## [!DNL Storefront popover]

- The [[!DNL popover]](storefront-popover.md) is available only for stores that use the *Luma* theme, or a customized theme that is based on *Luma*. Breadcrumbs on the search results page will not have *Luma* styling.
- The [!DNL popover] does not support the *Blank* theme.
- The [!DNL popover] is not supported on the Quick Order form.
- Wishlists and product comparisons are not supported.
- The currency symbol for the Peruvian sol (PEN) is not supported.

## Troubleshooting

For help with troubleshooting some common issues in [!DNL Live Search], see the following knowledgebase articles:

- [[!DNL Live Search] catalog not synchronized](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync)
- [[!DNL Live Search] dashboard and search result ranking is incorrect](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-dashboard-ranking-incorrect)
- [[!DNL Live Search] displays out-of-stock products regardless of stock status settings in Admin](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-displays-out-of-stock-products)
- [[!DNL Live Search] facets are not alphabetically sorted](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-facets-not-sorted)

If you need additional assistance, contact [support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
