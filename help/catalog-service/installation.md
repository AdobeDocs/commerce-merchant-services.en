---
title: Onboarding and Installation
description: "Learn how to install [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
---
# Onboarding and Installation

The following videos walk you through the [!DNL Catalog Service] process.

**Part 1**: Onboarding and installation

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Part 2**: Using the [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## Prerequisites

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server. If you are not familiar with working from the command line, ask a developer or system integrator to help.

**Software requirements**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Composer: 2.x

**Supported platforms**

- Adobe Commerce on cloud infrastructure: 2.4.4+
- Adobe Commerce on premises: 2.4.4+

>[!ENDSHADEBOX]

## Endpoints

[!DNL Catalog Service] has two endpoints available for onboarding:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`)—used for testing and validation before going live
- Production (`https://catalog-service.adobe.io/graphql`)—used for live traffic for Commerce merchants and websites

All test instances of Commerce should use the Sandbox endpoint.

Load testing should only be performed on the Sandbox endpoint. It is recommended that a [Support ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) be opened when load testing so the Services team can anticipate the additional server traffic.

## Installation and configuration

To get started with [!DNL Catalog Service] for Adobe Commerce, the following steps are required:

- Install the data export extensions
- Configure the service and data export
- Access the service

### Install the data export extensions

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server.

The [!DNL Catalog Service] extension can be installed on both Adobe Commerce cloud infrastructure and on-premises instances.

The [!DNL Catalog Service] is installed with Composer keys, which are linked to the Commerce account [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) provided during the signup process. Composer uses these keys during the initial installation of Adobe Commerce, or in situations in which the Composer keys were not previously saved to an external `auth.json` file.

See [Get your authentication keys](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) for more information about obtaining Composer keys.

#### Adobe Commerce on cloud infrastructure

Use this method for installing the [!DNL Catalog Service] extension for a Commerce Cloud instance.

1. On your local workstation, change to your project directory.
1. Add the Catalog Service module.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Update package dependencies.

   ```bash
   composer update
   ```

1. Commit and push code changes for the `composer.json` and `composer.lock` files.

#### On-premises

Use this method for installing the [!DNL Catalog Service] extension for an on-premises instance.

1. Use Composer to add the Catalog Service module to your project:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Clear the cache:

   ```bash
   bin/magento cache:clean
   ```

### Configure the service and data export

After you install [!DNL Catalog Service], you must configure the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) by specifying the API keys and selecting a SaaS Data Space.

After the SaaS configuration is complete, perform an initial data sync by using the [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard). You can use this dashboard to monitor the synchronization status for product data transferred from the Commerce database to Commerce SaaS services.

To ensure that the catalog export is running correctly:

- Confirm that cron jobs are running.
- Verify that the indexers are running.
- Ensure that the `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, and `Product Variant Feed` indexers are set to "Update by Schedule".

The initial sync could take from a few minutes to hours depending on the catalog size. After the initial sync, the Catalog exports product data from the Commerce server to Commerce services on an ongoing basis to keep the services up to date. To monitor the status of the sync, refer to the [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### Access the service

The [!DNL Catalog Service] API is accessible using POST commands over HTTPS.

To obtain the api-key, go to the Commerce Service Connector area in the admin and copy the public API key.

Read the [GraphQL documentation](https://developer.adobe.com/commerce/services/graphql/) to understand how to query and send the headers that are needed for generating API requests. 

To allow [!DNL Catalog Service] through a firewall, add `commerce.adobe.io` to the allowlist.

## Catalog Service and API Mesh

The [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) enables developers to integrate private or third-party APIs and other interfaces with Adobe products using Adobe IO.

See the  [[!DNL Catalog Service] and API Mesh](mesh.md) topic for installation and configuration details.

## Data Management Dashboard

Users can refer to the [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) for more data about [!DNL Catalog Service] data syncing.
