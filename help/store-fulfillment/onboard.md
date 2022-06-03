---
title: Onboarding Overview
description: "Connect your [!DNL Commerce] instance to the [!DNL Store Fulfillment Manager] service by completing a few onboarding steps."
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
---
# Onboarding Overview

Onboard Store Fulfillment by installing the extension on your Commerce instance and configuring the API connections. These connections enable communication and data synchronization between your Commerce instance, third-party systems for inventory management, and the Store Assist app.

After you complete onboarding, configure and manage the solution from the Commerce Admin

![[!DNL Store Fulfillment Service] configuration in Admin view](assets/store-fulfillment-admin-home.png)

## Onboarding Overview

1. Install the Store Fulfillment by Walmart Technologies extension for Adobe Commerce.

1. From the Admin, enable the solution and complete general configuration for the integration, its active features, and complete the onboarding intake form to connect to fulfillment services.

1. Configure the delivery methods.

1. Set up sources as your physical stores and configure products in your catalog.

1. Select and configure the email templates to manage customer communication for buy online, pickup in-store (BOPIS) transactions.

1. Create users and roles for the Store Assist app.

1. Configure the schedules for background processes to sync data to the fulfillment service.

## Requirements

You must meet the following requirements to install, deploy, and use the solution.

* **Commerce account information**-Installing [!DNL Channel Manager] requires a [Commerce account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. You need an account ID and credentials with Owner or Admin access to the [!DNL Adobe Commerce] instance.

* For [!DNL Adobe Commerce] on cloud infrastructure projects, software installers must have administrator access to the Cloud project. See [Manage user access](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Access to the Store Fulfillment by Walmart Technologies software archive (.zip file) to install the Store Fulfillment solution**–During the onboarding and enablement process, your customer account representative will provide download access to the installation file.

* **Experience using Composer and the [!DNL Commerce CLI]**—See [General CLI Installation](https://devdocs.magento.com/extensions/install/){target="_blank"} for information about using these tools to install and manage extensions on [!DNL Adobe Commerce] and [!DNL Magento Open Source] platforms.

* [!DNL Inventory Management] extension for Adobe Commerce and Magento Open Source

   You must have the Inventory Management extension installed and enabled on your Adobe Commerce and Magento Open Source instance. Typically, this extension is installed and enabled by default on Adobe Commerce 2.3.x and later. For more information, see [Install Inventory Management](https://devdocs.magento.com/extensions/inventory-management/) in the Adobe Commerce Developer documentation.

## Platform and version requirements

The [!DNL Store Fulfillment] solution is available to Adobe Commerce customers on the following platforms.

* Adobe Commerce on cloud infrastructure (ECE)
* Adobe Commerce on premises (EE)

The Store Fulfillment solution is compatible with the following software versions.

**Software Compatibility**

| **Software**   | **Minimum Version** | **Maximum Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0               | 2.4.4               |
| Composer       | 1.x                 | 2.x                 |
| MariaDB        | 10.2                | 10.4                |
| MySQL          | 5.7                 | 8.0                 |
| PHP            | 7.4                 | 8.1                 |

For detailed requirements, review the Adobe Commerce [System requirements](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) in the Developer documentation.

### Business Requirements

Your business must meet the following minimum criteria to implement the Store Fulfillment solution.

* US-Based businesses only

* B2C Retailers, CPG Manufacturers selling D2C, or Distributors selling D2C or to small businesses

* At least one physical store or warehouse

* Manage your product inventory with Inventory Management for Adobe Commerce (was MSI)

* Ability to syndicate merchant inventory

* Store Wi-Fi availability at all locations that support the Store Fulfillment solution

* Store and warehouse associates have access to iOS or Android mobile devices during their shifts, either personal or provided by the merchant

* Products managed by using the Store Fulfillment solution must have product attributes that include either a SKU or UPC product code
