---
title: Inventory Management Source Transfer
description: "Configure stocks for the [!DNL Store Fulfillment solution] with Adobe Commerce Inventory Management. Set up a new stock and transfer inventory out of default stock so that you can assign it to sources configured to enable Store Pickup capabilities required by the Store Fulfillment solution."
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
---

# Inventory Management Source Transfer

The [!DNL Store Fulfillment] solution uses native Adobe Commerce Inventory Management. By default, the [!DNL Commerce] configuration assigns all web inventory to the default stock, which can not have additional sources assigned. Because a website can only be assigned a single stock, a merchant must configure a new stock and optionally transfer their default source inventory to a source that is assigned to the appropriate scope. Then, the source can be assigned to the new stock.

>[!IMPORTANT]
>
>Merchants must maintain the default source for all products included in group and bundle product types. These products need an inventory quantity that meets the minimum quantity threshold for in stock items and include a stock status of [!UICONTROL In Stock].

These configuration changes help you accomplish three things:

1. [Transfer inventory to source](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) to move inventory from the default stock/source to the new stock/source.

1.  [Bulk assign sources](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) to add the new sources for all your products.

1.  [Complete bulk updates for product attributes](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) to add the `Allow Store Pickup` and `Allow Home Delivery` attributes to existing products. When the solution is installed, the attributes have the optimal *default* values. However, these attributes are not applied to existing products until you complete the bulk updaContes process.

Inventory is deducted from the selected source (retail store location or ecommerce warehouse). Sources used as ecommerce warehouses must be assigned to the same stock as the store pickup location and prioritized before the retail locations. For additional information, see [Prioritizing Sources for a Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

For more information on managing inventory, stocks, and sources, see the Adobe Commerce user documentation:

- [Managing Inventory](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Managing Inventory Quantities](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Managing Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Managing Sources](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Prioritizing Sources for a Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Bulk Updates for Product Attributes](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Changing the configuration for inventory and stock sources can also have downstream impact on integrated systems. Ensure that you understand how the changes to the inventory configuration impact these systems.
