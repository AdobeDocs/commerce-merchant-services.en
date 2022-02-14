---
title: Types of Facets
description: Live Search facets are dynamic, and appear in the Filters list when relevant.
---
# Types of facets

All [!DNL Live Search] facets are dynamic and appear in the *Filters* list only when relevant. The list of available facets changes according to the products returned. The following characteristics affect their presentation and behavior:

* Pinned facets  - The most commonly-used facets can be pinned to the top of the list. The remaining facets are listed in *Sort type* order after the pinned facets.
* Intelligent facets - Product attributes that [Adobe Sensei](https://www.adobe.com/sensei.html) finds most relevant to a product set and query. The calculation takes into account the attribute metadata of the entire catalog and determines at query time the most relevant facets for the query.
* Popular facets - Product attributes that are most often present in search results.
* Price facets - Return products by price range. You can specify the number of selections and the price range interval on the [*Settings*](settings.html) tab.

At query time, [!DNL Live Search] generates the search results in groups of intelligent and popular facets.

![Facets - Price](assets/storefront-search-results-run-price.png?lang=en)

## Storefront and headless options

Facets that are rendered for the [!DNL Commerce] storefront are processed by the search adapter, which routes requests and renders the results in the storefront. All [!DNL Commerce] storefront facets are sorted alphabetically with single-select options, regardless of the input type that is assigned to the corresponding attribute. Facets that are available in the storefront are rendered according to the current theme and reflect any customizations made to the presentation of layered navigation.

In contrast, [headless](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/webapi-vision.html) implementations are processed by the API and support additional options. Headless facets can be sorted alphabetically or by count, and can have either single- or multi-select options.

### Select type

For headless implementations, facets can be defined as `single select` or `multi-select` with logical operators that determine the returned product set. For example, `green AND blue` or `green OR blue`.

![Facets - Select type](assets/facets-select-type.png?lang=en)

| Select type | Description |
|--- |--- |
| Single select | A single-select facet offers multiple options, but allows the shopper to choose only one value. |
| Multi-select (or) | (Headless only) Shoppers can choose more than one option and returned product(s) can match any selected value. Example: `green OR blue` |
| Multi-select (and) | (Headless only) Shoppers can choose more than one option, and returned products must match all selected values. Example: `green AND blue` |

### Facet labels

For [!DNL Commerce] storefronts, the facet label is determined by the [*Attribute Properties*](https://docs.magento.com/user-guide/stores/attribute-product-create.html). For stores with multiple views, additional labels can be defined under *Manage Labels*. For headless implementations, labels are edited from the [faceting workspace](faceting-workspace.html).

### Sort type

All facets rendered for the storefront are sorted alphabetically. For headless implementations, facets can be sorted alphabetically or by count.

| Sort type | Description |
|--- |--- |
| Alphabetic | In the storefront *Filters* list, facets are sorted alphabetically. |
| Count | (Headless only) For headless implementations, facets can also be sorted by the number of values found per facet in the current set of returned products. |
