---
title: Facet Technical Notes
description: Technical notes about using [!DNL Live Search] facets.
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
