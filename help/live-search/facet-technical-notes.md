---
title: Facet Technical Notes
description: Technical notes about using Live Search facets.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
---
# Facet Technical Notes

Faceting is a high-performance filtering method that uses multiple dimensions of searchable static and dynamic attribute values as search criteria.

[!DNL Live Search] uses the `productSearch` query which returns faceting and other data that is specific to [!DNL Live Search]. Refer to [`productSearch` query](https://devdocs.magento.com/live-search/product-search.html) for code examples.

## Facet aggregation

Facet aggregation is performed as follows if the storefront has three facets (categories, color and price) and the shopper filters on all three (color = blue, price is from $10.00-50.00, categories = `promotions`).

*  `categories` aggregation - Aggregates `categories`, applies `color` and `price` filters, but not the `categories` filter.
*  `color` aggregation - Aggregates `color`, applies `price` and `categories` filters, but not the `color` filter.
*  `price` aggregation - Aggregates `price`, applies `color` and `categories` filters, but not the `price` filter.

## Default attribute values

The following product attributes have some [storefront properties](https://docs.magento.com/user-guide/stores/attributes-product.html) that are enabled by default.

| Property | Storefront Property | Attribute |
|---|---|---|
| Sortable | Used for Sorting in Product Listing | `price`|
| Searchable | Use in Search | `price` <br />`sku`<br />`name`|
| FilterableInSearch | Use in Layered Navigation - Filterable (with results)| `price`<br />`visibility`<br />`category_name`|
