---
title: "[!DNL Storefront Popover]"
description: The "[!DNL Live Search storefront popover]" dynamically returns suggested products and thumbnails.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
---
# [!DNL Storefront Popover]

When [!DNL Live Search] is [installed](install.md), a [!DNL popover] appears in the storefront when shoppers type in the [Search](https://docs.magento.com/user-guide/catalog/search-quick.html) box. With each character typed, the [!DNL popover] is updated with suggested products and thumbnail images of the top search results.

[!DNL Live Search] returns results for a query of two characters or more. For a partial match, the maximum number of characters per word is 20. The number of characters in a "search as you type" query is not configurable.

>[!NOTE]
>
>The [!DNL Live Search] [!DNL storefront popover] is available only for stores that use the *Luma* theme, or a customized theme that is based on *Luma*. The *Luma* theme is included in the [!DNL Commerce] sample data. The [!DNL popover] does not support the *Blank* theme. See [Styling [!DNL Popover] Elements](storefront-popover-styling.md) to learn more.

## Searchable attributes

To produce highly-targeted results, review the set of [searchable](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) product attributes. To ensure relevancy, make attributes searchable only if they contain content that has a clear and concise meaning. Avoid using attributes that contain less precise, lengthy text such as `description`, which although search-enabled by default, can reduce the precision of search results. For example, if a person searches for "shorts" and there are shirts with a description that includes the term "short sleeves", then the shirts will be included in the search results.

The following attributes are always searchable:

*  `sku`
*  `name`
*  `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] page size

The page size of the [!DNL popover] determines how many lines of autocompleted products can be returned. Previously, the page size was hardcoded as six lines. However, the `page_size` value is now a setting that can be configured from the *Admin*. During the Live Search installation, the `page_size` value changes to the current value of the [Catalog Search](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` setting.

 By default, the Catalog Search - Autocomplete Limit value is set to eight lines (or rows). To change the page size of the [!DNL popover], do the following:

1. On the *Admin* sidebar, go to **Stores** > Settings > **Configuration**.
1. In the left panel, expand **Catalog** and choose **Catalog** from the list of settings.
1. Expand the *Catalog Search* section.
1. Set the **Autocomplete Limit** to the number of lines that you want to allow in the [!DNL popover].
1. When complete, click **Save Config**.
