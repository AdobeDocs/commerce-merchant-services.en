---
title: Install and Configure Adobe Experience Platform Connector from Adobe Commerce
description: Learn how to install, configure, update, and uninstall the Adobe Experience Platform Connector from Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
---
# Install and configure the Experience Platform connector

Before you install the extension, [review the prerequisites](overview.md#prereqs).

## Install the extension

The Experience Platform connector extension is installed from the command line of the server and connects to your Adobe Commerce installation as a [service](../landing/saas.md). When the process is complete, **Experience Platform Connector** appears on the **System** menu under **Services** in the Commerce _Admin_.

The Experience Platform connector is installed as an extension from [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html).

1. To download the `experience-platform-connector` package, run the following from the command line:

   ```bash
   composer require magento/experience-platform-connector
   ```
   
   This metapackage contains the following modules and extensions:

   * `module-platform-connector-admin` - Updates the Admin UI so you can select the Datastream ID for a specific Adobe Commerce instance
   * `module-platform-connector` - Sets the `Organization ID` and `datastreamId` in the Storefront Events SDK
   * `data-services` - Provides attribute context for storefront events. For example, when a checkout event occurs, information about how many items were in the cart and product attribute data for those items are included.
   * `services-id` - Connects your Adobe Commerce instance to [Adobe Commerce SaaS](../landing/saas.md) using sandbox and production API keys and to the Adobe Experience Platform to retrieve the IMS Organization ID

1. (Optional) To include [!DNL Live Search] data, which comprises search events, install the [[!DNL Live Search]](../live-search/install.md) extension.

## Update the Experience Platform connector {#update}

To update the Experience Platform connector, run the following from the command line:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

To update to a major version such as from 1.0.0 to 2.0.0, edit the project’s root [!DNL Composer] `.json` file as follows:

1. Open the root `composer.json` file and search for `magento/platform-connector`.

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

## Uninstall the Experience Platform connector {#uninstall}

To uninstall the Experience Platform connector, refer to [uninstall modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
