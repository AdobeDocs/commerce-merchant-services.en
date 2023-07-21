---
title: Store Fulfillment Requirements
description: Requirements for provisioning and onboarding the [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
---
# Store Fulfillment Requirements for Adobe Commerce

The following sections detail the technical and business requirements for installing and enabling the Store Fulfillment solution for Adobe Commerce.

## Platform and software version requirements

The [!DNL Store Fulfillment] solution is available to Adobe Commerce customers on the following platforms.

- Adobe Commerce on cloud infrastructure (ECE)
- Adobe Commerce on premises (EE)

The Store Fulfillment solution is compatible with the software versions listed in the *Software Compatibility* table.

**Software compatibility**

| **Software**   | **Minimum Version** | **Maximum Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0               | 2.4.5               |
| Composer       | 1.x                 | 2.x                 |
| MariaDB        | 10.2                | 10.4                |
| MySQL          | 5.7                 | 8.0                 |
| PHP            | 7.4                 | 8.1                 |

For detailed requirements, review the Adobe Commerce [System requirements](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) in the *Adobe Commerce Installation Guide*.

## Store Assist app requirements

The end-to-end process to manage store pickup orders is managed through the Store Assist app installed on mobile devices. These devices—provided by the retailer or by store employees using their personal smart phones—must meet the following requirements:

**Minimum operating system requirements**

- Android 6
- iOS 12

**Minimum hardware requirements**

- 1 GB RAM
- 600 MB free disk space

## Business requirements

Your business must meet the following minimum criteria to implement the Store Fulfillment solution:

- US-based businesses only

- Business to Consumer (B2C) Retailers, Consumer Packaged Goods (CPG) Manufacturers selling directly to consumers (D2C), or distributors selling directly to consumers or small businesses

- At least one physical store or warehouse

- Manage your product inventory with Inventory Management for Adobe Commerce (aka MSI)

- Ability to syndicate merchant inventory

- Store Wi-Fi availability at all locations that support the Store Fulfillment solution: 3 Mbps minimum Internet speed

- Store and warehouse associates have access to iOS or Android mobile devices during their shifts, either personal or provided by the merchant

- Products managed by using the Store Fulfillment solution must have product attributes that include either a SKU or UPC product code
