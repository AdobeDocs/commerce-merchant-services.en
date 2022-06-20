---
title: Install and Configure Adobe Experience Platform Connector from Adobe Commerce
description: Learn how to install, configure, update, and uninstall the Adobe Experience Platform Connector from Adobe Commerce.
---
# Install and configure Experience Platform connector

Before you install the extension, [review the prerequisites](overview.md#prereqs).

## Install the extension

1. Install the Experience Platform connector metapackage.

   ```bash
   composer require magento/platform-connector
   ```
   
   This metapackage contains the following modules:

   * `module-platform-connector-admin` - Updates the Admin UI
   * `module-platform-connector` - Sets the `ImsOrgId` and `datastreamId` in the Magento Storefront Events SDK

1. Install Commerce Data Services extension to include profile and checkout events.

   ```bash
   composer require magento/data-services
   ```
   
   The Commerce Data Services extension provides attribute context for storefront events. For example, when a checkout event occurs, information about how many items were in the cart and product attribute data for those items are included.

1. Install the Commerce Service Connector.

   ```bash
   composer require magento/commerce-services
   ```

   The Commerce Service Connector lets you connect your Adobe Commerce instance to [Adobe Commerce SaaS](../landing/saas.md) and to the Adobe Experience Platform.
   
1. (Optional) To include [!DNL Live Search] data, which comprises search events, install the [[!DNL Live Search]](../live-search/install.md) extension.

## Update the Experience Platform connector {#update}

To update the Experience Platform connector, run the following from the command line:

```bash
composer update magento/platform-connector --with-dependencies
```

To update to a major version such as from 1.0.0 to 2.0.0, edit the project’s root [!DNL Composer] `.json` file as follows:

1. Open the root `composer.json` file and search for `magento/platform-connector`.

1. In the `require` section, update the version number as follows:

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Save** `composer.json`. Then, run the following from the command line:

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Uninstall the Experience Platform connector {#uninstall}

To uninstall the Experience Platform connector, refer to [uninstall modules](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
