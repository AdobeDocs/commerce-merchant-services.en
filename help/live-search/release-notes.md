---
title: [!DNL Live Search] Release Notes
description: [!DNL Live Search] from Adobe Commerce delivers a lightning fast, super-relevant, and intuitive search experience.
---
# [!DNL Live Search] Release Notes

These release notes describe the latest versions of [!DNL Live Search] and include:

* New features
* Fixes and improvements
* Known issues

## [!DNL Live Search] 1.3.1

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable

* FIX - [Custom price attribute](https://docs.magento.com/user-guide/stores/attributes-input-types.html) no longer returns an error when configured as a [facet]({% link live-search/facets-add.md %}).
* FIX - Fixed issue that caused an error to occur when no [currency symbol](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) is available.
* FIX - [Storefront popover](storefront-popover.html) now shows the [Special Price](https://docs.magento.com/user-guide/catalog/product-price-special.html) (minimum final price) when available.

## [!DNL Live Search] 1.3.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable

* NEW - [Performance](https://docs.magento.com/user-guide/live-search/performance.html) reporting dashboard provides insight into search terms that shoppers use.
* NEW - [!DNL Live Search] [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) provides access to a common data layer with event publishing and subscription services, and metrics.
* FIX - The [Storefront Popover](https://devdocs.magento.com/live-search/storefront-popover.html) has a new `active` class for the `.search-autocomplete` container that controls visibility.
* FIX - In the storefront, the [Search Terms](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) footer link is removed and its cache disabled for [!DNL Live Search] installations.
* BUG - Patch for Search adapter handles duplicate products.
* BUG - [!DNL Live Search] supports [single-source](https://docs.magento.com/user-guide/catalog/inventory-sources.html) (physical) inventory locations with multiple (virtual) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Multiple inventory sources are not supported at this time.

## [!DNL Live Search] 1.2.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable

* NEW - Storefront [popover](storefront-popover.html) displays suggested products and thumbnail images of top search results as shoppers type queries into the Search box.
* NEW - Commerce Admin session stays open during extended periods of keyboard inactivity
* NEW - [!DNL Live Search] is automatically enabled after onboarding
* FIX - Initial indexing time is less than an hour
* FIX - Incremental product updates near real time (after install and setup)
* FIX - Sortable columns in Synonym editor
* FIX - [!DNL Live Search] no longer throws an error if search criteria contains empty sort order value
* FIX - Range filtering no longer breaks if attribute codes contain strings "to" or "from"

## [!DNL Live Search] 1.1.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable

* BUG - The [!DNL Live Search] service supports only the [base currency](https://docs.magento.com/user-guide/stores/currency-configuration.html) of the Adobe Commerce installation.
* BUG - When adding a facet, the Product Attributes Feed does not update correctly when set to `Update on Save`. To avoid this problem, go to [Index Management](https://docs.magento.com/user-guide/system/index-management.html) and set Product Attributes Feed to `Update by Schedule`.
* BUG - [!DNL Live Search] synonyms are defined per store view, but are currently stored per website and identified with a combination of `environmentId` + `storeViewCode`. As a result, all websites and store views within the Adobe Commerce installation share the same set of synonyms. The most recently created set of synonyms for the store view takes precedence.
* BUG - If a synonym term contains multiple words, each word is treated as a separate synonym. For example, if you define “time piece” as a synonym of “watch”, both “time” and “piece” are treated as synonyms of watch.

## Documentation

To learn more:

* [Adobe Commerce Developer Documentation](https://devdocs.magento.com/)
* [Adobe Commerce User Guide](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] on Marketplace](https://marketplace.magento.com/magento-live-search.html)
