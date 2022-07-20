---
title: Product Stock Management
description: Configure the merchant stock messaging and features available to customers.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
---
# Product stock management

As a merchant, you can use Adobe Commerce [Inventory Management](https://docs.magento.com/user-guide/catalog/inventory-management.html) stock and source options. Additionally, you can control other inventory availability options relating to
your merchant store operations with the Store Fulfillment solution.

- Home delivery option from Merchant stores

- Allow / Available for Store Pickup

- UPC / SKU / Other Unique Product Identifiers

- Out of Stock Threshold

- Decrementing Inventory from specific locations upon order

Configure Product Stock options from the Admin: **[!UICONTROL Catalog > Products > Select Product]**

## **Product Stock Options**

| **Field**                                                | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | **Scope**  | **Required** |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Available for Home Delivery**                          | Sets the Home Delivery (Ship-from-Store) availability for the product. When enabled, any assigned merchant store locations with available inventory for the product are considered eligible for the Home Delivery option. When disabled, the product is never eligible for Home Delivery, even if a merchant store has available inventory.</br></br>In most cases, setting this option at the merchant store level is sufficient. However, there might be unique cases for specific products, such as those under federal shipping restrictions, which should not be eligible for Home Delivery. | Website    | No           |
| **[!UICONTROL Available for Store Pickup]**              | Set the Store Pickup availability for the product. When enabled, any assigned merchant store locations with available inventory for the product are considered eligible for the Store Pickup option. When disabled, the product is never eligible for Store Pickup, even if a merchant store has available inventory.</br></br>This option may be useful for cases where you are tracking merchant inventory in the system, but you do not want to sell it from your ecommerce channel.                                                                                                           | Website    | No           |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | This attribute should already exist as a product attribute and relates to the **[!UICONTROL Barcode Source / Barcode Type]** setting. This attribute is used to track a scannable barcode for your products. This value might be sent when an order is sent to your merchant stores for picking. Store associates can use the value with the pick list to match products on the shelf using a barcode scanner.                                                                                                                                                                                    | Store View | No           |

{style="table-layout:auto"}

## Sources for product-level inventory

| **Field**                               | **Description**                                                                                                                                                                                                                                                                                                                                                                                      | **Scope** | **Required** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Set the stock threshold for the item within each source. When stock falls below the threshold, it is considered out of stock at the source.</br></br>To use the global Store Configuration setting, check the **[!UICONTROL Use Default]** option.                                                                                                                                                   | Global    | No           |
| **[!UICONTROL Allow Store Pickup]**     | Explicitly set whether the item is available for store pickup, regardless of available inventory or merchant store location configuration.</br></br> To use the product-level setting, uncheck the [!UICONTROL Use Default] option and make your selection. Otherwise, this setting is chosen based on the configuration for **[!UICONTROL Allow In-Store Pickup]** that is set on the stock source. | Global    | No           |

{style="table-layout:auto"}

