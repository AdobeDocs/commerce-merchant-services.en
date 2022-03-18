---
title: Styling Popover Elements
description: Technical notes about customizing the Live Search storefront popover.
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
---
# Styling popover elements

The [storefront popover](storefront-popover.md) always displays the product `name` and `price`, and the selection of fields is not configurable. However, popover elements can be styled using CSS classes. For example, the following declarations change the background color of the popover container and footer.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Container visibility

The parent component of the `.livesearch.popover-container` is `.search-autocomplete`.  The `.active` class indicates the visibility of the container. The `.active` class is conditionally added when the popover is open.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

For more information about styling storefront elements, refer to [Cascading style sheets (CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) in the [Frontend Developers Guide](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

## Class selectors

The following class selectors can be used to style the container, suggestion, and product elements in the popover.

*  `.livesearch.popover-container`
*  `.livesearch.view-all-footer`
*  `.livesearch.suggestions-container`
*  `.livesearch.suggestions-header`
*  `.livesearch.suggestion`
*  `.livesearch.products-container`
*  `.livesearch.product-result`
*  `.livesearch.product-name`
*  `.livesearch.product-price`

### Container Class Selectors

`.livesearch.popover-container`

![Popover container](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![View all footer](assets/livesearch-view-all-footer.png)

### Suggestion Class Selectors

`.livesearch.suggestions-container`
![Suggestions container](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`
![Suggestions header](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`
![Suggestion](assets/livesearch-suggestion.png)

### Product Class Selectors

`.livesearch.products-container`
![Product container](assets/livesearch-product-container.png)

`.livesearch.product-result`
![Product result](assets/livesearch-product-result.png)

`.livesearch.product-name`
![Product name](assets/livesearch-product-name.png)

`.livesearch.product-price`
![Product price](assets/livesearch-product-price.png)

## Working with a modified theme {#working-with-modified-theme}

The storefront popover can be used with a customized [theme](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) that inherits the required files from *Luma*. The `top.search` block in the `header-wrapper` of the `Magento_Search` module must not be modified.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Disabling the popover

To disable the popover and restore the standard [Quick Search](https://docs.magento.com/user-guide/catalog/search-quick.html) functionality, enter the following command:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
