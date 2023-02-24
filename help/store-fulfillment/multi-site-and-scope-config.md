---
title: Multiple Website and Scope Configuration
description: Configure stocks and delivery methods for multiple websites and store scopes.
role: User, Admin
level: Intermediate
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
---
# Multiple Website and Scope Configuration

You can set the [Scope](https://docs.magento.com/user-guide/configuration/scope.html) for a few elements to accommodate multiple websites, stores, and store views:

- [Manage Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html) per scope

- Manage [!DNL Delivery Methods] per scope

You can assign stock to a website or store scope. Then, update store sources to set available delivery methods (home delivery, store pickup).

After updating the configuration successfully, the store pickup options on the product detail page (PDP) in the Adobe Commerce storefront can be selected only for products available from a stock source that allows store pickup.

## Manage In-Store Pickup settings

Enable or disable the [!UICONTROL In-Store Pickup] options for each website or store scope from the [Delivery Method Configurations](enable-general.md#delivery-methods) in the Admin.

1. Navigate to **[!UICONTROL Stores > Configuration]**.

1. Select the scope (Website ot Store) to configure.

1. With scope selected, navigate to **[!UICONTROL Sales > Delivery Methods]**.

1. Disable or enable the **[!UICONTROL In-Store Pickup]** Delivery method.

You can also manage whether curbside or in-store pickup is available globally in this section.

Manage the [!UICONTROL In-Store Pickup] and [!UICONTROL Delivery Method] settings per stock source. Numerous other configurations exist to full flexibility over your implementation.
