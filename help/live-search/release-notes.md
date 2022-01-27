---
title: [!DNL Live Search] Release Notes
description: [!DNL Live Search] from Adobe Commerce delivers a lightning fast, super-relevant, and intuitive search experience.
---
# [!DNL Live Search] Release Notes

These release notes describe the latest versions of [!DNL Live Search] and include:

* New features
* Fixes and improvements
* Known issues

## [!DNL Live Search] 1.4.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable

## [!DNL Live Search] 1.3.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable
* NEW - [Performance](https://docs.magento.com/user-guide/live-search/performance.html) reporting dashboard provides insight into search terms that shoppers use.
* NEW - [!DNL Live Search] [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) provides access to a common data layer with event publishing and subscription services, and metrics.
* FIX - The [Storefront Popover](https://devdocs.magento.com/live-search/storefront-popover.html) has a new `active` class for the `.search-autocomplete` container that controls visibility.
* FIX - In the storefront, the [_Search Terms_](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) footer link is removed and its cache disabled for [!DNL Live Search] installations.
* ISSUE - Patch for Search adapter handles duplicate products.
* ISSUE - [!DNL Live Search] supports [single-source](https://docs.magento.com/user-guide/catalog/inventory-sources.html) (physical) inventory locations with multiple (virtual) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Multiple inventory sources are not supported at this time.
## [!DNL Live Search] 1.2.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable
* {:.new} Storefront [popover]({% link live-search/quick-tour.md %}) displays suggested products and thumbnail images of top search results as shoppers type queries into the Search box.
* {:.new} Commerce Admin session stays open during extended periods of keyboard inactivity
* {:.new} [!DNL Live Search] is automatically enabled after onboarding
* {:.fix} Initial indexing time is less than an hour
* {:.fix} Incremental product updates near real time (after install and setup)
* {:.fix} Sortable columns in Synonym editor
* {:.fix} [!DNL Live Search] no longer throws an error if search criteria contains empty sort order value
* {:.fix} Range filtering no longer breaks if attribute codes contain strings "to" or "from"

## [!DNL Live Search] 1.1.0

* Compatible with Adobe Commerce (EE): 2.4.x
* Compatible with Adobe Commerce for Cloud (ECE): 2.4.x
* Stability: Stable
* {:.bug}The [!DNL Live Search] service supports only the [base currency]({% link stores/currency-configuration.md %}) of the Adobe Commerce installation.
* {:.bug}When adding a facet, the _Product Attributes Feed_ does not update correctly when set to `Update on Save`. To avoid this problem, go to [Index Management]({% link system/index-management.md %}) and set _Product Attributes Feed_ to `Update by Schedule`.
* {:.bug}[!DNL Live Search] synonyms are defined per store view, but are currently stored per website and identified with a combination of `environmentId` + `storeViewCode`. As a result, all websites and store views within the Adobe Commerce installation share the same set of synonyms. The most recently created set of synonyms for the store view takes precedence.
* {:.bug}If a synonym term contains multiple words, each word is treated as a separate synonym. For example, if you define “time piece” as a synonym of “watch”, both “time” and “piece” are treated as synonyms of watch.

## Documentation

To learn more:

* [Adobe Commerce Developer Documentation]({{ site.devdocs_url }}/live-search/overview.html)
* [Adobe Commerce User Guide]({% link live-search/overview.md %})
* [[!DNL Live Search] on Marketplace](https://marketplace.magento.com/magento-live-search.html)
