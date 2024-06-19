---
title: "[!DNL SaaS Data Export Guide]"
description: "Learn about using the [!DNL data export] extension for Adobe Commerce SaaS services that synchronizes data between Adobe Commerce and connected Commerce services."
role: Admin, Developer
recommendations: noCatalog
---
# [!DNL SaaS Data Export] Guide

[!DNL SaaS data export] improves frontend performance by optimizing data synchronization between an Adobe Commerce instance and connected Commerce Services. When you add Live Search, Product Recommendations, or the Catalog Service to an Adobe Commerce installation, the [!DNL Data export] extension is installed automatically.

The SaaS data export collects and exports various types of data, referred to as _feeds_, which aggregate specific types of information. Depending on which Commerce services are installed, the SaaS data export feeds include:

- **Catalog entity feeds** aggregate product data. Data includes products, product attributes, product prices, product variations, categories, category permissions, and product permissions.
- The **Scopes feed** aggregates data for customer groups, websites, stores, and store views.
- The **Sales Order feed** aggregates orders data including their related entities such as invoices, shipments, credit memos, and so on.
- The **Multi-Source Inventory feed** aggregates data about inventory stock status items.

The data export extension supports several methods to initiate and manage the data synchronization process.

- **Manual synchronization from the Admin or the command line**

  - The [Data Management dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) in the Commerce Admin provides a graphical view of the synchronization status. You can use the dashboard to perform a full resynchronization (_full sync_) of all feeds. However, Adobe recommends only performing a full sync the first time you connect Adobe Commerce to a Commerce service. See [Synchronization process](data-synchronization.md).

  - The [Adobe Commerce command-line tool](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) provides commands to synchronize specific feeds and includes additional options to customize feed processing.

- **Automated synchronization with cron jobs**

  - [Partial data synchronization](data-synchronization.md#partial-synchronization-with-cron-jobs)—Cron jobs trigger a partial data sync when a Commerce Admin user updates an entity. The data export process sends only these updates to connected Commerce services. The partial synchronization process is based on the MView mechanism and requires no actions from the Admin user or system integrator.

  - [Automatic retry for synchronization errors](data-synchronization.md#failed-items-sync-for-error-recovery)—Cron jobs trigger automatic retry of the synchronization process when errors occur during the data synchronization process.

- **Export scheduling and performance**

  - Developers and system integrators can estimate the time required for SaaS data export to synchronize data between Adobe Commerce and connected services. This estimation can help schedule data export processing to prevent site disruption. See [Estimate data volume and transmission time](estimate-data-volume-sync-time.md).

  - In cases where the sync needs to happen more quickly, SaaS data export provides customization options to improve export processing performance. See [Improve data export performance](customize-export-processing.md).

- **Track and troubleshoot data export activities**—Use data-export and saas-export logs to review sync status and feed payloads during the synchronization and indexation process. See [Logging and troubleshooting](troubleshooting-logging.md).



