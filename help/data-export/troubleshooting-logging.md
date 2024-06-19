---
title: Review logs and troubleshoot
description: Learn how to troubleshoot [!DNL data export] errors using the data-export and saas-export logs.
feature: Services
recommendations: noCatalog
exl-id: 55903c19-af3a-4115-a7be-9d1efaed8140
---
# Review Logs and Troubleshoot

The [!DNL data export] extension provides logs to track data collection and synchronization processes.

## Logs

Logs are available in the `var/log` directory on the Commerce application server.

| log name | filename | description |
|-----------------| ----------| -------------|
| SaaS data export log |`commerce-data-export.log` | Provides information about data export activities such as entity events and full resync triggers.  Each log record has a specific structure and provides information about the feed, operation, status, elapsed time, process id, and the caller.|
| SaaS data export error log | `data-export-errors.log` | Provides error messages and stack traces for errors that occur during the data synchronization process.|
| SaaS export log | `saas-export.log` | Provides information about the data sent to Commerce SaaS services.|
| SaaS export error log | `saas-export-errors.log` | Provides information about errors that occur when sending data to Commerce SaaS services.|

If you do not see expected data for an Adobe Commerce Service, use the error logs for the data export extension to determine where the problem occurred.

You can extend logs with additional data for tracking and troubleshooting. See [Extended logging](#extended-logging).

### Log format

Each log record has the following structure.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>The JSON-based string is beautified for better readability.

The following table describes the operation types that can be recorded in the logs.

| Operation                  | Description                                                                                                                                 | Caller example                                                                       |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| full sync | Full sync collects and sends all data to the SaaS for a given feed. | `bin/magento saas:resync --feed=products`                                              |
| partial reindex            | Partial sync collects and sends data to SaaS for only updated entities in a given feed. This log is present only if updated entities exist.              | `bin/magento cron:run --group=index`                                                   |
| retry failed items         | Resends items for a given feed to SaaS if the previous sync operation failed due to a Commerce application or server error. This log is present only if failed items exist.| `bin/magento cron:run --group=saas_data_exporter`  (any "*_data_exporter" cron group)  |
| full sync (legacy)          | Full sync for a given feed in legacy export mode.                                                   | `bin/magento saas:resync --feed=categories`                                            |
| partial reindex (legacy)   | Sends updated entities to SaaS for a given feed in legacy export mode. This log is present only if updated entities exist.             | `bin/magento cron:run --group=index`                                                   |
| partial sync (legacy)      | Sends updated entities to SaaS for a given feed in legacy export mode. This log is present only if updated entities exist.              | `bin/magento cron:run --group=saas_data_exporter` (any "*_data_exporter" cron group)   |


### Logging examples

During a full resync, progress is tracked and logged every 30 seconds by default. Here is an example log entry.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

In this example, the `status` values provide information about the sync operation:

- **`"Progress 2/5"`** indicates that 2 of 5 iterations have been completed. The number of iterations depends on the number of exported entities.
- **`"processed: 200"`** indicates that 200 items have been processed.
- **`"synced: 100"`** indicates that 100 items were sent to SaaS. It's expected that `"synced"` is not equal to `"processed"`. Here is an example:
    - **`"synced" < "processed"`** means that the feed table didn't detect any changes in the item, compared to the previously synced version. Such items are ignored during the sync operation.
    - **`"synced" > "processed"`** the same entity id (for example, `Product ID`) can have multiple values in different scopes. For example, one product can be assigned to five websites. In this case, you might have "1 processed" item and "5 synced" items.

+++ Example: Full resync log for the price feed

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## View and troubleshoot logs with New Relic

If you store Adobe Commerce logs in the New Relic, you can add parsing rules to improve the readability and query experience.

1. Log in to New Relic.

1. Go to `Logs => Parsing`.

1. Click `Create parsing rule`.

1. Configure the parsing rule by adding the following values.

   - **Filter logs based on NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Parsing rule**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

This example adds a rule that allows you to query New Relic logs by specific feed type, operation, and so on.

**Example query string**—`feed.feed:"products" and feed.status:"Complete"`

## Extended logging

You can use environment variables to extend logs with additional data for tracking and troubleshooting.

### Check the feed payload

Include the feed payload in the SaaS export log by adding te `EXPORTER_EXTENDED_LOG=1` environment variable when you resync the feed.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

After the operation completes, the feed payload is available for review in the SaaS export log (`var/.log/saas-export.log`).

### Preserve payload in feed index table

For the Commerce SaaS data export extension (`magento/module-data-exporter`) 103.3.0 and later, immediate export feeds keep only the minimum required data in the index table. The feeds include all catalog and inventory stock status feeds.

Preserving payload data in the index table is not recommended in production environments, but it can be useful in a developer environment. Include the feed payload in the index by adding the `PERSIST_EXPORTED_FEED=1` environment variable when you resync the feed.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Run profiler to troubleshoot slow performance

If the reindex process of a specific feed takes an unreasonable amount of time, run the profiler to collect additional data that might be useful for the Support Team.

Run the profiler by adding the `EXPORTER_PROFILER=1` environment variable when you run the reindex command.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profiler data is stored in the data export log (`var/log/commerce-data-export.log`) in the following format:

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```
