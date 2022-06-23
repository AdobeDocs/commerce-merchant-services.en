---
title: Installation
description: "Install the [!DNL Store Fulfillment solution] for an Adobe Commerce storefront using Composer for PHP."
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
---

# Installation

Complete the initial installation of the [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] extension in a non-production environment with queue manager running and caching configured to allow exception handling. Ensure that your development environment includes development tools to ensure best practices for operating and maintaining your Adobe Commerce instance. 

## Prerequisites

Review the [requirements](solution-requirements.md) for the Store Fulfillment solution and gather required information before you install the [!DNL Store Fulfillment] extension for Adobe Commerce.

If you have installed a pre-release or beta version of the Store Fulfillment for Adobe Commerce extension, use the following command to remove it before installing the current version.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installation requirements

- **Access to the Store Fulfillment by Walmart Commerce Technologies software archive (.zip file)**—During the onboarding and enablement process, work with your Account Manager to get access to the installation file for the Store Fulfillment extension.

- **Adobe Commerce account information**—Installing the [!DNL Store Fulfillment] solution requires a [Commerce account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. You need an account ID and credentials with Owner or Admin access to the [!DNL Adobe Commerce] project.

- For [!DNL Adobe Commerce] on cloud infrastructure projects, software installers must have administrator access to the Cloud project. See [Manage user access](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Experience using Composer and the [!DNL Commerce CLI]**—See [General CLI Installation](https://devdocs.magento.com/extensions/install/){target="_blank"} for information about using these tools to install and manage extensions on the [!DNL Adobe Commerce] platform.

- **Experience installing third-party extensions on Adobe Commerce**—For reference, see the Adobe Commerce documentation.  
  
  - [Install an extension for an Adobe Commerce on cloud infrastructure instance](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).
  
  - [Install an extension for an Adobe Commerce on-premises instance](https://devdocs.magento.com/extensions/install/).

### Step 1: Download the extension bundle

Follow the instructions provided by your account representatives to download the archive file that contains the Composer packages for installing the Store Fulfillment Services extension.

### Step 2: Extract extension artifacts to your application

Extract the archive file that contains the integration bundle to install the Store Fulfillment Services extension.

1. Create a target directory for the extracted files.

   - From the command line, go to the web server doc root directory.

   - Create an `artifacts` directory.

1. Extract the archive file to the new directory. 

1. Verify that the extracted files by reviewing the file listing.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Step 3: Configure your app using Composer

Use Composer to configure the source directory for the installation and install the Store Fulfillment Services extension. 

1. Configure the source repository for the Composer installation.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```
   
1. Add the Store Fulfillment Services extension to `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>For better performance on Adobe Commerce on-premises instances, you can [update the autoload configuration](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Step 4: Upgrade the database schema and data

Complete the installation by using the `bin/magento setup:upgrade` to update the database schema and data with the changes to support the Store Fulfillment solution.

>[!NOTE]
>
>For Adobe Commerce on cloud infrastructure projects, you do not have to register the extension. Instead, commit the code changes from the previous step, and push them to your environment branch. The commands to update the database schema and data are run automatically during the cloud build and deployment process.

### Step 5: Complete the installation

1. Register the extension with Adobe Commerce by using the `setup:upgrade` Magento CLI command.

   ```terminal
   bin/magento setup:upgrade
   ```

1. If prompted, recompile your [!DNL Commerce] project.

   ```bash
   bin/magento setup:di:compile
   ```

1. Clean the cache.

   ```bash
   bin/magento cache:clean
   ```

1. Disable maintenance mode.

   ```bash
   bin/magento maintenance:disable
   ```

### Step 6: Verify the installation

From the Adobe Commerce server, verify that the modules for the Store Fulfillment Services extension are installed and enabled.

1. Log in to the server.

   For installations on Adobe Commerce on cloud infrastructure, [use SSH to log in to the remote environment](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. Verify that the Store Fulfillment Services modules are enabled.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   The output should include the following modules:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Additional Steps

If needed, use the [setup:static-content:deploy](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy){target="_blank"} CLI command to deploy static view files to your production environment.

```terminal
php bin/magento setup:static-content:deploy -f
```

The `-f` option is required if you are using a blank theme.

>[!NOTE]
>
>For more information, see [Static content deploy best practices in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360031624091) in the Adobe Commerce Help Center. 
