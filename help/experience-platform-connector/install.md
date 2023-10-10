---
title: Install and Configure Adobe Experience Platform Connector from Adobe Commerce
description: Learn how to install, configure, update, and uninstall the Adobe Experience Platform Connector from Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
---
# Install and configure the Experience Platform connector

Before you install the extension, [review the prerequisites](overview.md#prereqs).

## Install the extension

The Experience Platform connector extension is available from the [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). When you install this extension from the command line of the server, it connects to your Adobe Commerce installation as a [service](../landing/saas.md). When the process is complete, **Experience Platform Connector** and **Commerce Services Connector** appear on the **System** menu under **Services** in the Commerce _Admin_.

>[!NOTE]
>
>![B2B for Adobe Commerce](../assets/b2b.svg) For B2B merchants, there is a separate extension you must install. This extension adds support for B2B specific events. [Learn more](#install-the-b2b-extension).

1. To download the `experience-platform-connector` package, run the following from the command line:

   ```bash
   composer require magento/experience-platform-connector
   ```

   This metapackage contains the following modules and extensions:

   * `module-experience-connector-admin` - Updates the Admin UI so you can select the Datastream ID for a specific Adobe Commerce instance.
   * `module-experience-connector` - Sets the `Organization ID` and `datastreamId` in the Storefront Events SDK.
   * `data-services` - Provides attribute context for storefront events. For example, when a checkout event occurs, information about how many items were in the cart and product attribute data for those items are included.
   * `services-id` - Connects your Adobe Commerce instance to [Adobe Commerce SaaS](../landing/saas.md) using sandbox and production API keys and to the Adobe Experience Platform to retrieve the IMS Organization ID.
   * `orders-connector` - Connects the order status service to your Adobe Commerce instance.

1. (Optional) To include [!DNL Live Search] data, which comprises [search events](events.md#search-events), install the [[!DNL Live Search]](../live-search/install.md) extension.

### Configure the orders connector

After you install the `experience-platform-connector`, you must finalize installation of the `orders-connector` module based on the deployment type: on-premises or Adobe Commerce on Cloud infrastructure.

#### On-premises

In on-premises environments, you need to manually enable code generation and Adobe Commerce Events:

   ```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### On Cloud infrastructure

In Adobe Commerce on Cloud infrastructure, enable the `ENABLE_EVENTING` global variable in `.magento.env.yaml`. [Learn more](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

   ```bash
   stage:
      global:
         ENABLE_EVENTING: true
   ```

Commit and push updated files to the Cloud environment. When deployment is finished, enable sending events with the following command:

   ```bash
   bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

### Install the B2B extension

For B2B merchants, install the following extension to include [requisition list](events.md#b2b-events) event data.

Download the `magento/experience-platform-connector-b2b` extension by running the following from the command line:

   ```bash
   composer require magento/experience-platform-connector-b2b
   ```

## Update the Experience Platform connector {#update}

To update the Experience Platform connector, run the following from the command line:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

or, for B2B merchants:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

To update to a major version such as from 1.0.0 to 2.0.0, edit the project's root [!DNL Composer] `.json` file as follows:

1. Open the root `composer.json` file and search for `magento/experience-platform-connector`.

1. In the `require` section, update the version number as follows:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Save** `composer.json`. Then, run the following from the command line:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   or, for B2B merchants:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Uninstall the Experience Platform connector {#uninstall}

To uninstall the Experience Platform connector, refer to [uninstall modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
