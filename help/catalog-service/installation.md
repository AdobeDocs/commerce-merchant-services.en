---
title: "Installation"
description: "Learn how to install, update, and uninstall [!DNL Catalog Service]"
---

# Installation

{{catalog-service-beta}}

The [!DNL Catalog Service] for Adobe Commerce is installed with Composer keys, which are linked to the Magento ID ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) provided in the signup process. Composer uses these keys during the initial installation of [!DNL Adobe Commerce], or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) for more information about obtaining Composer keys.

## Install the extension

Deploying [!DNL Catalog Service] to your storefront and Admin requires that you install the module and configure the [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce on cloud infrastructure

Use this method for installing the [!DNL Catalog Service] extension for a Commerce Cloud instance.

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

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```
   The command updates all dependencies.

1. Commit and push your changes.

### On-premises

Use this method for installing the [!DNL Catalog Service] extension for an on-premises instance.

1. Open the `<Commerce_root>/composer.json` file in a text editor and update the `require` section as follows:

   ```json
   "require": {
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

To ensure that catalog export is running correctly, confirm that the [cron jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) and the [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) are running and the Product Feed indexer is set to Update by Schedule.
