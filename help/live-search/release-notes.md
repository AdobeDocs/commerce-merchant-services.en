---
title: "[!DNL Live Search] Release Notes"
description: "The latest release information for [!DNL Live Search] from Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
---
# [!DNL Live Search] Release Notes

These release notes describe the latest versions of [!DNL Live Search].
Support is provided for the current major released version. Release notes for older versions are provided for reference.
Updates include:

![New](../assets/new.svg) New features
![Fix](../assets/fix.svg) Fixes and improvements
![Bug](../assets/bug.svg) Known issues

## Hosted service updates

These notes describe updates that were published outside of a versioned release or improvements to the hosted service.

_October 27, 2023_

![New](../assets/new.svg) The [!DNL Live Search] PLP widget now supports color swatches.

_October 12, 2023_

![New](../assets/new.svg) Commerce administrators can now specify the language of the index for [!DNL Live Search]. See [Settings](settings.md).
![Fix](../assets/fix.svg) The "Search Rules" tab has been renamed to "Search Merchandising".

_June 13, 2023_

![Fix](../assets/fix.svg) Fixed an issue where some characters such as quotes or apostrophes caused ranking issues. Reindexing will solve these issues.

 _April 25, 2023_

![New](../assets/new.svg) [!DNL Live Search] customers can now take advantage of the new [SaaS price indexer](../price-index/index.md).

## [!DNL Live Search] 4.0.0 {#400}

 _Nov 13, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

### New Features

![New](../assets/new.svg) [!DNL Live Search] now supports color swatches in the PLP widget.
![New](../assets/new.svg) [!DNL Live Search] now displays the category name rather than the category Id.
![New](../assets/new.svg) [!DNL Live Search] now supports strikethrough prices in the PLP widget.
![New](../assets/new.svg) Introduced the "Hide Filters" button to hide the filters panel.


### Updates

![Fix](../assets/fix.svg) The [!DNL Live Search] PLP widget is now enabled by default for new installations.
![Fix](../assets/fix.svg) Reconfigured CSS styles to better isolate widget classes.
![Fix](../assets/fix.svg) Minor bug fixes

Merchants must upgrade the [!DNL Live Search] extension to version >= 4.0.0 to access these features.

After installing version 3.1.1 or higher, enable the new indexers: 

* Product Prices Feed
* Scopes website data feed
* Scopes customer groups data feed

After upgrading, test the updated configuration in QA or Staging before pushing the changes to production. 

## Previous versions

+++3.1.1 and prior

## [!DNL Live Search] 3.1.1 {#311}

 _Sept 15, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer



![New](../assets/new.svg) New Category Merchandising tab has been added. Users can now add Intelligent Rankings and Manual Rankings (pin, boost, bury, hide) per category
![New](../assets/new.svg) Users can add a single category rule with intelligent or manual ranking
![New](../assets/new.svg) Users can now add Intelligent Ranking rules to subcategories
![New](../assets/new.svg) Detailed information is provided when deleting subcategories with intelligent ranking
![New](../assets/new.svg) Added the ability to delete rules for inherited ranking strategies
![New](../assets/new.svg) Added the ability to delete rules for a single category
![New](../assets/new.svg) Users can now search by category name when adding a rule
![New](../assets/new.svg) With the Category Tree View, users can now view which category has rules applied.
![New](../assets/new.svg) Category Preview only shows the selected category.
![New](../assets/new.svg) AEM CIF [Popover widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) and [PLP widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) components allow AEM sites to take advantage of [!DNL Live Search].

### Updates

![Fix](../assets/fix.svg) The table size of the Products and Price feeds have been greatly reduced. Tables `catalog_data_exporter_products` and `catalog_data_exporter_product_prices` should see a substantial size reduction.
![Fix](../assets/fix.svg) The 'Rules' tab is renamed to 'Search Rules'
![Fix](../assets/fix.svg) When ranking by 'trending', you can now choose between:
    * 3 days (default)
    * 14 days
    * 30 days
![Fix](../assets/fix.svg) 'Events' (Boost/Pin/Bury/Hide) has been renamed to 'Manual Ranking'
![Fix](../assets/fix.svg) 'Ranking Type' has been renamed to 'Intelligent ranking'
![Fix](../assets/fix.svg) Minor bug fixes

## [!DNL Live Search] 3.1.0 {#310}

 _Sept 1, 2023_

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

### Updates

![Fix](../assets/fix.svg) The Product Listing widget has been updated to use the [Catalog Service API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

 _August 7, 2023_

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

### New Features

![New](../assets/new.svg) The following values have been added to the `storeDetails` object:

* "Allow All Products per Page"
* Currency rate
* "Products per Page on Grid Allowed Values"
* "Products per Page on Grid Default Value"
* Store language

### Updates

![Fix](../assets/fix.svg) Catalog Service modules have been added to the metapackage to support advanced data retrieval.
![Fix](../assets/fix.svg) The **My Account** page navigation no longer disappears when using the Product Listing Page widget.

Merchants must upgrade the [!DNL Live Search] extension version >= 3.0.2 to access these features.

It is recommended to upgrade and test before pushing to production. Consider upgrading the production environment during off-peak hours after verifying their testing environment results.

### Limitations

Using the Live Search Product Listing Page widget will cause Google Tag Manager to fail. Use the default Search Adapter if Google Tag Manager is needed.

## [!DNL Live Search] 3.0.1 {#301}

 _March 14, 2023_

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

### New Features

![New](../assets/new.svg) Product Item Card in Rules preview 
![New](../assets/new.svg) [Product Listing Page widget](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
![New](../assets/new.svg) [Category filtering options](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![New](../assets/new.svg) Added the ability to drag and drop to create Pin events
![New](../assets/new.svg) New Pin actions:
    * Pin to spot - Pin button to create Pin event with one click
    * Pin to top - Places product in the first position
    * Pin to bottom - Places the product at the bottom of the results
    * Unpin an event with one click
![New](../assets/new.svg) [Intelligent Ranking for rules](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)
![New](../assets/new.svg) [!DNL Live Search] now supports full [Inventory Management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) capabilities in Commerce (formerly knows as Multi-Source Inventory, or MSI). To enable full support, you must [update](install.md#update) the dependency module `commerce-data-export` to version 102.2.0+.

### Updates

![Fix](../assets/fix.svg) Configure Rules now automatically sorts positions uniquely
![Fix](../assets/fix.svg) Deleting an existing event now updates preview
![Fix](../assets/fix.svg) Rules with no events can be saved
![Fix](../assets/fix.svg) Remove faceting "Select Type" selector
![Fix](../assets/fix.svg) Added new "Editing" status for unsaved rules

### Fixes

![Fix](../assets/fix.svg) Fixed server error when there is an unfinished event during save
![Fix](../assets/fix.svg) Fixed correctly deleting specific event when there are multiple events
![Fix](../assets/fix.svg) Fixed existing rule event not updating when new event has been added
![Fix](../assets/fix.svg) Fixed on second "Edit" click from details, [!DNL Live Search] page requiring reload
![Fix](../assets/fix.svg) Synonyms: Fixed an issue when a user clicked out of input, they could not return the focus to the field
![Fix](../assets/fix.svg) Other minor bug fixes and performance updates


![Bug](../assets/bug.svg) - Ranking by "Recommended for you" is only supported within the Live Search widgets. It is not supported with the default Luma and PWA search functionality.
![Bug](../assets/bug.svg) - Custom price attribute facets do not render correctly in Luma, but the API properly filters on them.

Merchants must upgrade the [!DNL Live Search] extension version >= 3.0.1 to access these features.

It is recommended to upgrade and test before pushing to production. Consider upgrading the production environment during off-peak hours after verifying their testing environment results.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![Fix](../assets/fix.svg) - Live Search would throw an error when SDK resources were not available due to network issues. This bug is fixed.

Merchants must upgrade the Live Search extension version >= 2.0.5 to access these features.

It is recommended to upgrade and test before pushing to production. Consider upgrading the production environment during off-peak hours after verifying their testing environment results.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Live Search now supports filtering by the 'Display Out of Stock Products' setting in the admin. If 'Display Out of Stock Products' is set to false, `inStock = true` is added to the filter.
![Fix](../assets/fix.svg) To improve performance, the 'Suggestions' block has been removed from the Live Search popup. The data is still passed through GraphQL, in case you want to replace the feature.
![Fix](../assets/fix.svg) `categories` and `categoryPath` have replaced `categoryIds` for category filtering. Read more in the [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) topic.
![Fix](../assets/fix.svg) Previously, a user tied to a B2B company would receive an incorrect Customer Group Code when doing searches. Live Search now returns the correct value.
![Fix](../assets/fix.svg) Previously, when searching for a term that does not exist, Live Search would return an error. That bug is now fixed.

Merchants must upgrade the [!DNL Live Search] extension version >= 2.0.4 to access these features.

Users are advised to upgrade and test before pushing to production. Consider upgrading the production environment during off-peak hours after verifying their testing environment results.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) Live Search now supports B2B features by honoring category permissions, shared catalogs, and customer group-specific pricing.

Merchants must upgrade the [!DNL Live Search] extension version >= 2.0.3 to access these features.

Users are advised to upgrade and test before pushing to production. Consider upgrading the production environment during off-peak hours after verifying their testing environment results.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.4 and newer

Existing [!DNL Live Search] installations must be upgraded to [!DNL Live Search] 2.0.0 to take advantage of the following new features, fixes, and improvements:

![New](../assets/new.svg) [!DNL Live Search] now supports PHP 8.1 for installations running Adobe Commerce 2.4.4.
![New](../assets/new.svg) The `Magento_ElasticsearchCatalogPermissionsGraphQl` module is added to the list of modules that are disabled during the installation.
![New](../assets/new.svg) The number of available lines in the [[!DNL storefront popover]](quick-tour.md) can be configured from the *Admin*.
![New](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) supported for [!DNL Live Search].
![New](../assets/new.svg) The [!DNL Live Search] installation process is updated with advanced process changes.
![Fix](../assets/fix.svg) [Advanced Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) link removed from the storefront footer.
![Bug](../assets/bug.svg) The following product attributes are not supported by [Commerce GraphQL API](https://developer.adobe.com/commerce/services/graphql/live-search/) when used in relation to the beta release of PWA: `description`, `name`, `short_description`
![Bug](../assets/bug.svg) The beta release of PWA for [!DNL Live Search] does not support [event handling](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Fix](../assets/fix.svg) [Custom price attribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) no longer returns an error when configured as a [facet]({% link live-search/facets-add.md %}).
![Fix](../assets/fix.svg) Fixed issue that caused an error to occur when no [currency symbol](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) is available.
![Fix](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) now shows the [Special Price](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (minimum final price) when available.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) [Performance](performance.md) reporting dashboard provides insight into search terms that shoppers use.
![New](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) provides access to a common data layer with event publishing and subscription services, and metrics.
![Fix](../assets/fix.svg) The [[!DNL Storefront popover]](storefront-popover.md) has a new `active` class for the `.search-autocomplete` container that controls visibility.
![Fix](../assets/fix.svg) In the storefront, the [Search Terms](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) footer link is removed and its cache disabled for [!DNL Live Search] installations.
![Bug](../assets/bug.svg) Patch for Search adapter handles duplicate products.
![Bug](../assets/bug.svg) [!DNL Live Search] supports [single-source](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) (physical) inventory locations with multiple (virtual) [stocks](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Multiple inventory sources are not supported now.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![New](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) displays suggested products and thumbnail images of top search results as shoppers type queries into the Search box.
![New](../assets/new.svg) Commerce *Admin* session stays open during extended periods of keyboard inactivity
![New](../assets/new.svg) [!DNL Live Search] is automatically enabled after onboarding
![Fix](../assets/fix.svg) Initial indexing time is less than an hour
![Fix](../assets/fix.svg) Incremental product updates near real time (after install and setup)
![Fix](../assets/fix.svg) Sortable columns in Synonym editor
![Fix](../assets/fix.svg) [!DNL Live Search] no longer throws an error if search criteria contains empty sort order value
![Fix](../assets/fix.svg) Range filtering no longer breaks if attribute codes contain strings "to" or "from"

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Supported]{type="Informative" tooltip="Supported"} Adobe Commerce versions 2.4.x and newer

![Bug](../assets/bug.svg) The [!DNL Live Search] service supports only the [base currency](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) of the Adobe Commerce installation.
![Bug](../assets/bug.svg) When adding a facet, the Product Attributes Feed does not update correctly when set to `Update on Save`. To avoid this problem, go to [Index Management](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) and set Product Attributes Feed to `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] synonyms are defined per store view, but are currently stored per website and identified with a combination of `environmentId` and `storeViewCode`. As a result, all websites and store views within the Adobe Commerce installation share synonyms. The most recently created set of synonyms for the store view takes precedence.
![Bug](../assets/bug.svg) If a synonym term contains multiple words, each word is treated as a separate synonym. For example, if you define "time piece" as a synonym of "watch", both "time" and "piece" are treated as synonyms of watch.

+++

## Documentation

To learn more:

* [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce User Guide](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] on Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
