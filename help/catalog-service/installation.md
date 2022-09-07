---
title: Onboarding and Installation
description: Learn how to install [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
---
# Onboarding and Installation

Partners and customers are welcome to start using the [!DNL Catalog Service] for Adobe Commerce Beta version released on Aug 9, 2022. To participate, you must read and agree to our [Adobe Commerce Beta program terms](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Once you have signed the agreement, reach out to our team on the [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) public Slack channel. We will provide all information and the next steps needed to work with the [!DNL Catalog Service] Beta version.

## Prerequisites

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server. If you are not familiar with working from the command line, ask a developer or system integrator to help.

### Software requirements

-  Adobe Commerce 2.4.x
-  PHP 8.1, 7.4, 7.3
-  Composer: 2.x, 1.x

### Supported platforms

-  Adobe Commerce on cloud infrastructure: 2.4.x
-  Adobe Commerce on premises: 2.4.x

## Install the extension

You can install the [!DNL Catalog Service] extension for both Adobe Commerce on cloud infrastructure and on-premises instances.

The [!DNL Catalog Service] is installed with Composer keys, which are linked to the Magento ID ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) provided in the signup process. Composer uses these keys during the initial installation of [!DNL Adobe Commerce], or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) for more information about obtaining Composer keys.

### Adobe Commerce on cloud infrastructure

Use this method for installing the [!DNL Catalog Service] extension for a Commerce Cloud instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the `require` section as follows:

   ```json
   "require": {
    "magento/composer-root-update-plugin": "^2.0.2",
    "magento/magento-cloud-metapackage": ">=2.4.5 <2.4.6",
    "magento/saas-export": "^101.4.0",
    "magento/commerce-data-export": "^101.3.1",
    "magento/commerce-data-export-ee": "^101.3.1",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
    }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Test the new configuration locally and update dependencies:

   ```bash
   composer update
   ```

   The command updates all dependencies.

1. Commit and push your changes for `composer.json` and `composer.lock`.

### On-premises

Use this method for installing the [!DNL Catalog Service] extension for an on-premises instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the `require` section as follows:

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
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

## Configure catalog export

After you install [!DNL Catalog Service], you must configure the [Commerce Services Connector](../landing/saas.md) by specifying API Keys and selecting a SaaS Data Space.

To ensure that the catalog export is running correctly, confirm that the [cron jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) and the [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) are running and the `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`, and `Product Variant Feed` are set to `Update by Schedule`.
