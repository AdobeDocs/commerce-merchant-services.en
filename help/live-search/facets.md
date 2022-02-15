---
title: Facets
description: Live Search facets use multiple dimensions of attribute values as search criteria.
---
# Facets

Faceting is a method of high-performance filtering that uses multiple dimensions of attribute values as search criteria. Faceted search is similar, but considerably “smarter” than the standard [layered navigation](https://docs.magento.com/user-guide/catalog/navigation-layered.html). The list of available filters is determined by the [filterable attributes](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) of products returned in the search results. Up to 100 facets can be configured with [!DNL Live Search].

![Filtered search results](assets/storefront-search-results-run.png)

## Faceting requirements

The category and product attribute requirements for faceting are similar to the filterable attributes used for layered navigation. The storefront properties of each attribute must be set to `filterable (with results)`.

| Setting | Description |
|--- |--- |
| [Category display settings](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | Anchor - `Yes` |
| [Attribute properties](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [Catalog Input type](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Attribute storefront properties | Use in Layered Navigation - `Filterable (with results)` |

## Default non-system attribute properties

The following table shows the default search and filterable properties of non-system attributes, including those that are specific to the Luma sample data. Setting the *Use in Search* attribute property to `Yes` makes the attribute searchable in both [!DNL Live Search] and native Adobe Commerce.

| Attribute Code | Searchable | Use in Layered Navigation |
|--- |--- |--- |
| activity | Yes | Filterable (with results) |
| attributes_brand | Yes | No |
| brand | Yes | No |
| climate | Yes | Filterable (with results) |
| collar | Yes | Filterable (with results) |
| color | Yes | Filterable (with results) |
| cost | Yes | No |
| eco_collection | Yes | Filterable (with results) |
| gender | Yes | Filterable (with results) |
| manufacturer | Yes | Filterable (with results) |
| material | Yes | Filterable (with results) |
| purpose | Yes | Filterable (with results) |
| strap_bags | Yes | Filterable (with results) |
| style_general | Yes | Filterable (with results) |

## Default system attribute properties

The following table shows the default search and filterable properties of system attributes.

| Attribute Code | Searchable | Use in Layered Navigation |
|--- |--- |--- |
| allow_open_amount | Yes | Filterable (with results) |
| description | Yes | No |
| name | Yes | No |
| price | Yes | Filterable (with results) |
| short_description | Yes | No |
| sku | Yes | No |
| status | Yes | No |
| tax_class_id | Yes | No |
| url_key | Yes | No |
| weight | Yes | No |
