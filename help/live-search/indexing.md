---
title: [!DNL Live Search] Indexing
description: How [!DNL Live Search] indexes product attribute properties
---
# Indexing

Product attribute properties (metadata) determine how an attribute can be used in the catalog, its appearance and behavior in the store, and the data that is included in data transfer operations. The scope of attribute metadata is `website/store/store view`.

The [!DNL Live Search] API allows a client to sort by any product attribute that has the [storefront property](https://docs.magento.com/user-guide/stores/attributes-product.html) `Use in Search` set to `Yes` in the Adobe Commerce Admin.

[!NOTE]

[!DNL Live Search] does not index deleted products or those set to `Not Visible Individually`.

## Indexing pipeline

The client calls the search service from the storefront to retrieve (filterable, sortable) index metadata. Only searchable product attributes with the *Use in Layered Navigation* property set to `Filterable (with results)` and *Use for Sorting in Product Listing* set to `Yes` can be called by the search service.
To construct a dynamic query, the search service needs to know which attributes are searchable and their weight. [!DNL Live Search] honors {{site.data.var.ee}} search weights (1-10, where 10 is the highest priority). The list of data that is synced and shared with the catalog service can be found in the schema, which is defined in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] indexing client search diagram](/assets/indexing-pipeline.svg?lang=en)

1. Check merchant for [!DNL Live Search] entitlement.
1. Get store views with changes to attribute metadata.
1. Store indexing attributes.
1. Reindex search index.

### Full index

When [!DNL Live Search] is configured and synchronized during onboarding, it can take up to eight hours to build the initial index. The process begins after `cron` submits the feed and finishes running.

The following events trigger a full sync and index build:

*  Onboarding [catalog data sync](install.html#synchronize-catalog-data)
*  Changes to attribute metadata

For example, changing the `Use in Search` property of the `color` attribute from `No` to `Yes` changes the attribute metadata to `searchable=true`, and triggers a full sync and reindex. The following attribute metadata trigger a full sync and reindex when changed:

*  `filterableInSearch`
*  `searchable`
*  `sortable`
*  `visibleInSearch`

### Streaming product updates

After the initial index is built during [onboarding](install.html#synchronize-catalog-data), the following incremental product updates are continuously synced and reindexed:

*  New product(s) added to the catalog
*  Changes to product attribute values

For example, adding a new swatch value to the `color` attribute is handled as a streaming product update.
Streaming update workflow:

1. Updated products are synced from the Adobe Commerce instance to the catalog service.
1. The indexing service continuously looks for product updates from the catalog service. Updated products are indexed as they arrive in the catalog service.
1. It can take up to fifteen minutes for a product update to become available in [!DNL Live Search].

## Client search

The [!DNL Live Search] API allows a client to sort by any sortable product attribute by setting the [storefront property](https://docs.magento.com/user-guide/catalog/product-attributes.html), *Used for sorting in product listings* to `Yes`. Depending on the theme, this setting causes the attribute to be included as an option in the [Sort by](https://docs.magento.com/user-guide/catalog/navigation.html) pagination control on catalog pages. Up to 300 product attributes can be indexed by [!DNL Live Search], with [storefront properties](https://docs.magento.com/user-guide/stores/attributes-product.html) that are searchable and filterable.
The index metadata is stored in the indexing pipeline and is accessible by the search service.

![[!DNL Live Search] index metadata API diagram](/assets/index-metadata-api.svg?lang=en)

### Sortable attribute workflow

1. Client calls Search Service.
1. Search Service calls Search Admin Service.
1. Search Service calls Indexing Pipeline.

## Indexed for all products

The order of the fields in this list reflects the typical order of columns in exported product data.

*  `environment_id`
*  `website_code`
*  `store_code`
*  `store_view_code`
*  `product_id`
*  `sku`
*  `name`
*  `type`
*  `displayable`
*  `deleted`
*  `url`
*  `currency`
*  `meta_description`
*  `meta_keyword`
*  `meta_title`
*  `description`
*  `short_description`
*  `weight`
*  `image`
*  `small_image`
*  `thumbnail_image`
*  `prices`
*  `in_stock`
*  `low_stock`

The following field is indexed for all configurable products:

*  `childrenSkus`
