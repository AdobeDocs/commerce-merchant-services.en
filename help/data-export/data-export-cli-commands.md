---
title: SaaS Data Export Command-line Interface
description: Learn how to use the command-line interface commands to manage feeds and processes for the [!DNL data export extension] for Adobe Commerce SaaS services.
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
---
# SaaS Data Export Command-line Interface Reference

Developers and system administrators can manage synchronization operations for SaaS data export using the [Adobe Commerce command-line tool](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI). The `saas:resync` command is included in the `magento/saas-export` package.

Adobe does not recommend using the `saas:resync` command regularly. Typical scenarios for using the command are:

- The initial sync
- The [SaaS Data Space ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) was changed, and you need to synchronize data to the new data space.
- Troubleshooting

## Initial Sync

>[!NOTE]
>If you are using Live Search or Product Recommendations, you do not need to run the initial sync. The process is initiated automatically after you connect the service to your Commerce instance.

When you trigger a `saas:resync` from the command line, depending on your catalog size, it can take from a few minutes to a few hours for the data to update.

For the initial sync, Adobe recommends running the commands in the following order:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Command examples

Before using `saas:resync` commands, review the [option descriptions](#command-options).

- Perform a full resync for an entity feed.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Feeds that have already been successfully exported are not resynchronized.

- Fully resync the specified feed and cleanup data

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Use only after performing a [!DNL Data Space ID Cleanup] operation.

- For immediate export feeds, resend all data to connected Commerce services without truncating index data in the feed table

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- List available commands and options with descriptions.

  ```
  bin/magento saas:resync --help
  ```

## Command options

The following options are available for managing `saas:resync` operations.

>[!NOTE]
>
>The `saas:resync` command also supports advanced options to improve data export commands by increasing batch size and adding multi-thread processing. See [Customize export processing](customize-export-processing.md).

### `feed`

This required option specifies which feed entity to resync, such as `products`.

The `feed` option value can include any of the available entity feeds:

- `products`: product data feed
- `productAttributes`: product attributes data feed
- `categories`: categories data feed
- `variants`: configurable product variations data feed
- `prices`: product prices data feed
- `categoryPermissions`: category permissions data feed
- `productOverrides`: product permissions data feed
- `inventoryStockStatus`: inventory stock status data feed
- `scopesWebsite`: websites with stores and store views data feed
- `scopesCustomerGroup`: customer groups data feed
- `orders`: sales orders data feed

Depending on which [Commerce Services](../landing/saas.md) are installed, you might have a different set of feeds available for the `saas:resync` command.

### `no-reindex`

This option resubmits the existing catalog data to [!DNL Commerce Services] without reindexing. If this option is not specified, the command runs a full reindex before syncing data.

The behavior of this option depends on whether the feed is exported in [legacy or immediate export mode](data-synchronization.md#synchronization-modes)

- For legacy export feeds, the synchronization process does not truncate indexed data in the feeds table. Instead, it resends all data to the Adobe Commerce service.
- For immediate export feeds, this option is ignored if specified. For these feeds, the resync process does not truncate the index and only resynchronizes updates or items that previously failed.

### `cleanup`

This option cleans up the feed indexer table before a sync. When specified, SaaS data export runs a full resync for the specified feed and cleans up all existing data in the feed table.

Adobe recommends only using this command after performing the [!DNL Data Space ID Cleanup] operation.

>[!WARNING]
>
>**Do not use this option regularly**. It can cause data sync issues in Adobe Commerce Services. For example, the `delete product event` might not propagate to the Adobe Commerce service if the `cleanup` option is used.

## Troubleshooting

If you do not see expected data in connected Commerce Services, troubleshoot issues by checking data export error logs and using the `saas:resync` command with environment variables to review payloads and profiler data. See [Review logs and troubleshoot](troubleshooting-logging.md).
