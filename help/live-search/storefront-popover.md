---
title: "[!DNL Storefront Popover]"
description: "The [!DNL Live Search storefront popover] dynamically returns suggested products and thumbnails."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
---
# [!DNL Storefront Popover]

When [!DNL Live Search] is [installed](install.md), a [!DNL popover] appears in the storefront when shoppers type in the [Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) box. With each character typed, the [!DNL popover] is updated with suggested products and thumbnail images of the top search results.

[!DNL Live Search] returns results for a query of two characters or more. For a partial match, the maximum number of characters per word is 20. The number of characters in a "search as you type" query is not configurable.

By default, [!DNL Live Search] supports [search term redirects](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Learn how to set product attributes as searchable in the [Setting up Live Search](workspace.md) article.

## [!DNL Popover] page size

The page size of the [!DNL popover] determines how many lines of autocompleted products can be returned. During the Live Search installation, the `page_size` value changes to the current value of the [Catalog Search](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` setting.

By default, the Catalog Search - Autocomplete Limit value is set to eight lines (or rows). To change the page size of the [!DNL popover], do the following:

1. On the *Admin* sidebar, go to **Stores** > Settings > **Configuration**.
1. In the left panel, expand **Catalog** and choose **Catalog** from the list of settings.
1. Expand the *Catalog Search* section.
1. Set the **Autocomplete Limit** to the number of lines that you want to allow in the [!DNL popover].
1. When complete, click **Save Config**.

## Styling [!DNL Popover] example

You can customize the look and feel of the [!DNL Popover] widget to match your company's style and branding guidelines.

The [!DNL storefront popover] always displays the product `name` and `price`, and the selection of fields is not configurable. However, [!DNL popover] elements can be styled using [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) classes. For example, the following declarations change the background color of the [!DNL popover] container and footer.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Container visibility

The parent component of the `.livesearch.popover-container` is `.search-autocomplete`.  The `.active` class indicates the visibility of the container. The `.active` class is conditionally added when the [!DNL popover] is open.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

For more information about styling storefront elements, refer to [Cascading style sheets (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) in the [Frontend Developer Guide](https://developer.adobe.com/commerce/frontend-core/guide/).

## Class selectors

You can use the following class selectors to style the container and product elements in the [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

### Container Class Selectors

#### .livesearch.popover-container

![[!DNL Popover] container](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![View all footer](assets/livesearch-view-all-footer.png)

### Product Class Selectors

#### .livesearch.products-container

![Product container](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Product result](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Product name](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Product price](assets/livesearch-product-price.png)

#### .livesearch product-link

![Product result](assets/livesearch-product-link.png)

## Working with a modified theme {#working-with-modified-theme}

You can use the [!DNL storefront popover] with a customized [theme](https://developer.adobe.com/commerce/frontend-core/guide/themes/) that inherits the required files from *Luma*. The `top.search` block in the `header-wrapper` of the `Magento_Search` module must not be modified.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Disabling the [!DNL popover]

To disable the [!DNL popover] and restore the standard [Quick Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) functionality, enter the following command:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Headless implementations

For those with headless implementations, you can install the [!DNL Live Search popover] using an [npm package](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
