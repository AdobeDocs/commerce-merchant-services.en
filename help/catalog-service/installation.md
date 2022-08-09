---
title: "Onboarding and Installation"
description: "Learn how to install [!DNL Catalog Service]"
---

# Onboarding and Installation

Partners and customers are welcome to start using the [!DNL Catalog Service] Beta version released on Aug 9, 2022. To participate, you must read and agree to our [Adobe Commerce Beta program terms](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Once you've signed the agreement, reach out to our team on the [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) public Slack channel. We will provide all information and the next steps needed to work with the [!DNL Catalog Service] Beta version.

## Prerequisites

>[!NOTE]
>
>You must install [[!DNL Live Search]](../live-search/install.md) before installing [!DNL Catalog Service].

The onboarding process for [!DNL Catalog Service] requires access to the command line of the server. If you are not familiar with working from the command line, ask a developer or system integrator to help.

### Software requirements

-  Adobe Commerce 2.4.x
-  PHP 8.1, 7.4, 7.3
-  Composer: 2.x, 1.x

### Supported platforms

-  Adobe Commerce on cloud infrastructure: 2.4.x
-  Adobe Commerce on premises: 2.4.x

## Install the extension

The [!DNL Catalog Service] for Adobe Commerce is installed with Composer keys, which are linked to the Magento ID ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) provided in the signup process. Composer uses these keys during the initial installation of [!DNL Adobe Commerce], or in situations in which the Composer keys were not previously saved to the `auth.json` file.

See [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) for more information about obtaining Composer keys.

### Adobe Commerce on cloud infrastructure

Use this method for installing the [!DNL Catalog Service] extension for a Commerce Cloud instance.

1. Install [!DNL Live Search], if you have not done so already. You can use the following command to determine whether [!DNL Live Search] has been installed.

   ```bash
   composer show magento/module-live-search | grep version
   ```

1. Run the following command to download the [!DNL Catalog Service ] modules:

   ```bash
   composer require magento/module-product-variant-data-exporter
   composer require magento/module-saas-product-variant
   ```

1. Update dependencies and install the extension:

   ```bash
   composer update
   ```

   The command updates all dependencies.

1. Commit and push your changes.

### On-premises

Use this method for installing the [!DNL Catalog Service] extension for an on-premises instance.

1. Install [!DNL Live Search], if you have not done so already. You can use the following command to determine whether [!DNL Live Search] has been installed.

   ```bash
   composer show magento/module-live-search | grep version
   ```

1. Run the following command to download the [!DNL Catalog Service ] modules:

   ```bash
   composer require magento/module-product-variant-data-exporter
   composer require magento/module-saas-product-variant
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

## Verify the installation

If you fully installed and configured [!DNL Live Search], the [Commerce Services Connector](../landing/saas.md) should already be set up. Review the connector settings to be sure.

To ensure that catalog export is running correctly, confirm that the [cron jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) and the [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) are running and the Product Feed indexer is set to Update by Schedule.
