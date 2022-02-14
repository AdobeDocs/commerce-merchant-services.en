---
title: Storefront Popover
description: The Live Search storefront popover dynamically returns suggested products and thumbnails.
---
# Storefront Popover

When [!DNL Live Search] is [installed](install.html), a popover appears in the storefront when shoppers type in the [Search](https://docs.magento.com/user-guide/catalog/search-quick.html) box. With each character typed, the popover is updated with suggested products and thumbnail images of the top search results.

[!DNL Live Search] returns results for a query of two characters or more. For a partial match, the maximum number of characters per word is 20. The number of characters in a "search as you type" query is not configurable.

>[!NOTE]
>
>The [!DNL Live Search] storefront popover is available only for stores that use the *Luma* theme, or a customized theme that is based on *Luma*. The *Luma* theme is included in the [!DNL Commerce] sample data. The popover does not support the *Blank* theme. See [Working with a modified theme](#working-with-modified-theme) for more information.

## Searchable attributes

To produce highly-targeted results, review the set of [searchable](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) product attributes. To ensure relevancy, make attributes searchable only if they contain content that has a clear and concise meaning. Avoid using attributes that contain less precise, lengthy text such as `description`, which although search-enabled by default, can reduce the precision of search results. For example, if a person searches for "shorts" and there are shirts with a description that includes the term "short sleeves", then the shirts will be included in the search results.

The following attributes are always searchable:

*  `sku`
*  `name`
*  `categories`

![Live Search popover](assets/storefront-search-as-you-type.png)
