---
title: Onboarding and Installation
description: Learn how to install [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
---
# Onboarding and Installation

## Prerequisites

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server. If you are not familiar with working from the command line, ask a developer or system integrator to help.

### Software requirements

-  Adobe Commerce 2.4.x
-  PHP 8.1, 7.4, 7.3
-  Composer: 2.x, 1.x

### Supported platforms

-  Adobe Commerce on cloud infrastructure: 2.4.x
-  Adobe Commerce on premises: 2.4.x

## Environments

Catalog Service has two environments available for onboarding:

- Sandbox (https://catalog-service-sandbox.adobe.io/graphql) - used for testing and validation before going live
- Production (https://catalog-service.adobe.io/graphql)- used for live traffic for Commerce merchants and websites

## Installation and configuration

To get started with Catalog Service for Adobe Commerce ,the following steps are required:

- Install the data export extensions
- Configure the service and data export
- Access the service

### Install the data export extensions

The onboarding process for Catalog Service requires access to the command line of the server.

The Catalog Service extension can be installed on both Adobe Commerce cloud infrastructure and on-premises instances.

The Catalog Service is installed with Composer keys, which are linked to the Commerce account [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) provided during the signup process. Composer uses these keys during the initial installation of Adobe Commerce, or in situations in which the Composer keys were not previously saved to an external `auth.json` file.

See [Get your authentication keys](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) for more information about obtaining Composer keys.

#### Adobe Commerce on cloud infrastructure

Use this method for installing the Catalog Service extension for a Commerce Cloud instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the require section as follows:

    ```json
    "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1",
      "magento/module-catalog-service-installer": "1.0.1"
    }
    ```

1. Test the new configuration locally and update dependencies:

```bash
composer update
```

The command updates all dependencies.

1. Commit and push your changes for `composer.json` and `composer.lock`.

#### On-premises

Use this method for installing the Catalog Service extension for an on-premises instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the require section as follows:

```json
"require": {
 "magento/module-saas-catalog": "^101.4.0",
 "magento/module-saas-product-override": "^101.4.0",
 "magento/module-saas-product-variant": "^101.4.0",
 "magento/module-bundle-product-data-exporter": "^101.3.1",
 "magento/module-catalog-data-exporter": "^101.3.1",
 "magento/module-catalog-inventory-data-exporter": "^101.3.1",
 "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
 "magento/module-configurable-product-data-exporter": "^101.3.1",
 "magento/module-data-exporter": "^101.3.1",
 "magento/module-parent-product-data-exporter": "^101.3.1",
 "magento/module-product-override-data-exporter": "^101.3.1",
 "magento/data-services": "^7.0.11",
 "magento/services-id": "^3.0.1",
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
}
```

1. Update dependencies and install the extension:

```bash
composer update
```

The command updates all dependencies.

1. Upgrade Adobe Commerce:

```bash
bin/magento setup:upgrade
```

1. Clear the cache:

```bash
bin/magento cache:clean
```

### Configure the service and data export 

After you install Catalog Service, you must configure the [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) by specifying the API keys and selecting a SaaS Data Space.

After the SaaS configuration is complete, perform an initial data sync by following the Catalog Sync guide. 

To ensure that the catalog export is running correctly:

- Confirm that cron jobs are running.
- Verify the indexers are running.
- Ensure that the `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, and `Product Variant Feed` indexers are set to "Update by Schedule".

The initial sync could take from a few minutes to hours depending on the catalog size. After the initial sync, the Catalog exports product data from the Commerce server to Commerce services on an ongoing basis to keep the services up to date.

### Access the service

The Catalog Service API is accessible using POST commands over HTTPS.

To obtain the api-key, go to the Commerce Service Connector area in the admin and copy the public API key.

Read the [GraphQL documentation](https://developer.adobe.com/commerce/webapi/graphql/) to understand how to query and send the headers that are needed for generating API requests. 

## Catalog Service and API Mesh

The [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) enables developers to integrate private or third-party APIs and other interfaces with Adobe products using Adobe IO.

See the  [Catalog Service and API Mesh](mesh.md) topic for installation and configuration details.
