---
title: Feed Ingestion Service
description: Learn about the Feed Ingestion Service for Adobe Commerce
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
---
# Feed Ingestion Service

The Feed Ingestion Service allows customers with large and/or complex catalogs to send data to Adobe Commerce services directly.

The Feed Ingestion Service decreases the time that it takes to process product changes (price updates, adding new attributes) by bypassing the Adobe Commerce instance and moving catalog data from a third-party Enterprise Resource Planning (ERP) directly to Adobe Commerce services.

This service is for customers that store and manage their product catalog in a system external to the core Adobe Commerce application. It is provided as an API, so that customers can integrate it into their existing systems, providing added flexibility in how it is deployed.

Customers with large, complex catalogs, or catalogs that get frequent updates are concerned that the new data could take longer than desired to appear in the live store. Since the Catalog Service knows what data it needs to process these updates, there is no need to send the data through the core Commerce product, only to be forwarded to Catalog Service. Removing this intermediate step is where efficiency gains are found.

## Feed ingestion flows

Depending on the Adobe Commerce configuration, data storage and data flows can take different paths.

* In a standard Adobe Commerce instance, the product catalog is stored within the core database.
* When using Adobe Commerce Services, catalog data is copied from the core database to the service and is processed and delivered from there.
* When storing catalog data in a third-party system (ERP, MDM, PIM), data flows through the core Commerce application and then to the Commerce services.
* With the Feed Ingestion Service, product data goes directly from the third-party system to the Commerce services infrastructure. 

![Feed ingestion service](assets/feed-ingestion.png)

By bypassing the core Commerce application and moving data directly to the Commerce services, product updates are reflected in the store quicker. Core catalog data, such as SKUs, are sent to the core Commerce application for separate processing.

## API

The [Feed Ingestion Service API documentation](https://developer.adobe.com/commerce/services/feed-ingestion) provides details on how to implement the service.
