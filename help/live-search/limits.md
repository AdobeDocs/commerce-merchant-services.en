---
title: "Limitations in [!DNL Live Search]"
description: "Learn about limitations in [!DNL Live Search]."
---
# Limitations in [!DNL Live Search]

[!DNL Live Search] is a robust search service for Adobe Commerce. This topic documents some of the limitations of the search functionality and highlights some differences between [!DNL Live Search] and the native Commerce search capabilities.

## Basic limitations

### Factets

[!DNL Live Search] faceting supports up to:

- 100 attributes configured as facets
- 50 sortable attributes
- 200 filterable attributes
- 200 searchable attributes

### Rules

- Maximum number of rules per store view is 50.
- Maximum number of conditions per rule is 10.
- Maximum number of events per rule is 25.

### Synonyms

- [!DNL Live Search] can manage up to 200 synonyms per store view.

## Widget and Adapter

The [!DNL Live Search] service can be implemented a two ways: The [!DNL Live Search] Search Adapter or the widget.

The Search Adapter is the default implementation of [!DNL Live Search]. It replaces the default search function when [!DNL Live Search] is installed. The Search Adapter support breadcrumbs and titles by default.

The [!DNL Live Search] widget does not have breadcrumbs and titles for search results.

Some other distinctions between the two are listed below.

| Search Adapter | Widget PLP |
| --- | --- |
| - Respects Magento Currency Picker settings in Magento storefront and can convert from Base Currency to other enabled currencies.<br>- Respects Default Display Currency per store view<br>- Add to Cart button<br>- Swatches; color, image, and text; this includes both facets and product tiles<br>- Wishlist<br>- Compare products<br>- Ignores most Live Search -> Faceting settings (e.g. name, select type, sort type)<br>- Respects Catalog -> Categories settings<br>- Not able to filter on Categories for most searches | - No Add to Cart button<br>- No swatches<br>- No wishlist<br>- No compare products<br>- Respects Live Search -> Faceting settings<br>- Ignores most of Catalog -> Categories settings<br>- Able to filter on Categories for most searches<br>- Quicker results |

To enable the widget:

1. Go to **Stores** > Settings > **Configuration** > **Live Search** > **Storefront Features** and set **Enable Product Listing Widgets** to "Yes".
1. Select **Save Config** to save the setting.
