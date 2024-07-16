---
title: '[!DNL SaaS Data Export Extension] Release Notes'
description: The latest release information for [!DNL Data Export Extension] for Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
---
# [!DNL SaaS Data Export] Extension Release Notes

These release notes describe the latest versions of the [!DNL SaaS data export] extension. Support is provided for the current major released version. Release notes for older versions are provided for reference.

Updates include:

![New](../assets/new.svg) New features
![Fix](../assets/fix.svg) Fixes and improvements
![Bug](../assets/bug.svg) Known issues


>[!NOTE]
>
>The SaaS data export extension is a collection of modules that is installed automatically with Live Search, Product Recommendations, and the Catalog Service. You can check the version installed on your system using composer. In some cases, you might want to upgrade the data export extension on your system to pick up fixes or new capabilities without updating the Commerce Service version.

## Current major version

## 103.3.7 Release

![Fix](../assets/fix.svg) Removed unnecessary dependencies from the InventoryDataExporter module.
![Fix](../assets/fix.svg) Changed required versions for inventory modules included in the CatalogInventoryDataExporter module to support Adobe Commerce version 2.4.4.

## 103.3.6 Release

![Fix](../assets/fix.svg) Fixed deadlocks that occurred during feed reindexing in multi-thread mode. Queries are now separated into Insert and Update operations.
![Fix](../assets/fix.svg) Optimized the Prices query for large catalogs with many websites.
![New](../assets/new.svg) Added retry logic to re-run failed transactions when deadlocks occurs.

## 103.3.5 Release

![Fix](../assets/fix.svg) Set dependency for latest compatible data export version for the SaaS common module.

![Fix](../assets/fix.svg) Replaced `ScopeConfig` instance with `ServiceConfigInterface` to support different service configurations.

## 103.3.4 Release

![Fix](../assets/fix.svg) Improve Commerce SaaS data export logging by adding more details about the reindexing process.

## 103.3.3 Release

![New](../assets/new.svg) SaaS data export now caches Entity-Attribute-Value (EAV) attributes for the attribute metadata query.

![Fix](../assets/fix.svg) Fixed an issue where the `InventoryStockStatus` feed was not saved on retry if product was deleted.

## 103.3.2 Release

![Fix](../assets/fix.svg) Fixed an issue where the `modifiedAt` field was missing from removed entities feeds.

## 103.3.1 Release

![Fix](../assets/fix.svg) Fixed an issue that caused an `Invalid Template File` message to appear during products feed reindexing when Page Builder is installed.

## 103.3.0 Release

![New](../assets/new.svg) Migrated immediate export feed tables to the unified structure:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![New](../assets/new.svg) Migrated catalog and inventory feeds to the immediate export solution.

![New](../assets/new.svg) Renamed immediate export feed cron-jobs to `*_feed_resend_failed_items`.

![New](../assets/new.svg) Renamed immediate export feed and change log tables.

![Fix](../assets/fix.svg) Set `modified_at` field in feed data only for feeds that require it.

![Fix](../assets/fix.svg) Modify the `productAttributes` query to retrieve only product attributes.

## 103.2.6 Release

![Fix](../assets/fix.svg) Fixed an issue that prevented feeds from being reindexed when tables have a prefix.

## 103.2.5 Release

![Fix](../assets/fix.svg) Optimized the Price query.

## 103.2.4 Release

![Fix](../assets/fix.svg) Fixed incorrect Stock status that displayed for a product when Commerce Inventory Management is enabled.

## 103.2.3 Release

![Fix](../assets/fix.svg) Fixed website level special pricing.
![Fix](../assets/fix.svg) Added mutex for all feeds that are processed.


## 103.2.2 Release

![Fix](../assets/fix.svg) Improved feeds batching strategy for large catalogs. The batches table is now filled with a limited number of IDs to reduce memory usage.

![Fix](../assets/fix.svg) Eliminated hard dependency of CommerceInventoryDataExporter to MSI modules.

![Fix](../assets/fix.svg) Improved `commerce-data-exporter` logs to collect more information and organize by different exporting stages.

## 103.2.1 Release

- Released updated version.

## 103.2.0 Release

- Added multi-thread data sync for products and prices.
