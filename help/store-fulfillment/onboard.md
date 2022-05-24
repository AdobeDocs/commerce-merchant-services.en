---
title: Onboard "[!DNL Store Fulfillment]"
description: Connect your Commerce instance to the [!DNL Store Fulfillment Manager] service by completing a few onboarding steps.
role: User, Admin
level: Intermediate
---

# Onboard Store Fulfillment by Walmart Technologies

Onboard Store Fulfillment by installing the extension on your Commerce instance and configuring the API connections. These connections enable communication and data synchronization between your Commerce instance, third-party systems for inventory management, and the Store Assist app.

After you complete onboarding, configure and manage the solution from the Commerce Admin

![[!DNL Store Fulfillment Service] configuration in Admin view](assets/store-fulfillment-admin-home.png)

## Onboarding overview

1. Install the Store Fulfillment by Walmart Technologies extension for Adobe Commerce.

1. From the Admin, enable the solution and complete general configuration for the integration, its active features, and complete the onboarding intake form to connect to fulfillment services.

1. Configure the Delivery Methods.

1. Set up sources as your physical stores and configure products in your catalog.

1. Select and configure the email templates to manage customer communication for buy online, pickup in-store (BOPIS) transactions.

1. Create users and roles for the Store Assist app.

1. Configure the schedules for for background processes to sync data to the fulfillment service.

## Prerequisites

* Verify that you have the required [Walmart Marketplace prerequisites](walmart-prerequisites.md) to integrate with Channel Manager.

* **Commerce account information**–Downloading and installing [!DNL Channel Manager] requires a [Commerce account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. You need an account ID and credentials with Owner or Admin access to the [!DNL Adobe Commerce] or [!DNL Magento Open Source] instance.

  * **MAGE ID**–[Log in](https://account.magento.com/customer/account/login/) to the Commerce account to get the ID from **[!UICONTROL My Account - Magento settings]**. You need this ID to register for the [!DNL Channel Manager] service Beta program.

     ![[!DNL MAGEID] on Commerce account settings](assets/mageid-my-commerce-account.png) 

  * **Access keys**– Get authentication keys to download Commerce extensions from the Commerce Composer repository `([!DNL repo.magento.com]`).

    ![[!UICONTROL Commerce Marketplace access keys]](assets/commerce-marketplace-access-keys.png)

    On Adobe Commerce and Magento Open Source projects, the owner can set up [Shared Access](https://docs.magento.com/user-guide/magento/magento-account-share.html) to allow trusted employees and service providers to download extensions using credentials from the Owner or license holder account.

    For [!DNL Adobe Commerce] on cloud infrastructure projects, software installers must have the following access to the [!DNL Commerce] instance:

    * Super User access to the Cloud project
    * Admin access to a specific environment
    * An [!DNL Adobe Commerce] or [!DNL Magento Open Source] account with permissions to access the Composer repository
    
    See [Manage user access](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Access to the Store Fulfillment by Walmart Technologies software archive to install the store Fulfillment solution on your Adobe Commerce instance**–Provide the Beta coordinator for Adobe Channel with the MAGE ID of the [!DNL Commerce] account used to manage the service for your organization.

* **Experience using Composer and the [!DNL Commerce CLI]** –See [General CLI Installation](https://devdocs.magento.com/extensions/install/){target="_blank"} for information about using these tools to install and manage extensions on [!DNL Adobe Commerce] or [!DNL Magento Open Source] platforms.

* [!DNL Inventory Management] extension for Adobe Commerce and Magento Open Source

   You must have the Inventory Management extension installed and enabled on your Adobe Commerce and Magento Open Source instance. Typically, this extension is installed and enabled by default on Adobe Commerce and Magento Open Source 2.3.x and later. For more information, see [Install Inventory Management](https://devdocs.magento.com/extensions/inventory-management/) in the Adobe Commerce Developer documentation.

## Requirements

The Store Fulfillment solution is available for Adobe Commerce and Magento Open Source customers. You must meet the following system and business requirements to install, deploy, and use the solution.

### System requirements

The Store Fulfillment by Walmart Technologies extension has been tested for compatibility with the following software versions.

**Software Compatibility**

| **Software**   | **Minimum Version** | **Maximum Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0               | 2.4.4               |
| Composer       | 1.x                 | 2.x                 |
| MariaDB        | 10.2                | 10.4                |
| MySQL          | 5.7                 | 8.0                 |
| PHP            | 7.4                 | 8.1                 |

For detailed requirements, review the Adobe Commerce [System requirements](<https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) in the Developer documentation.

### Business Requirements

Your business must meet the following minimum criteria to implement the Store Fulfillment solution.

* US-Based business

* B2C Retailers, CPG Manufacturers selling D2C, or Distributors selling D2C or to small businesses

* At least one physical store or warehouse

* Manage your product inventory with Inventory Management for Commerce (was MSI)

* Ability to syndicate merchant inventory

* Store Wi-Fi availability at all locations that support the Store Fulfillment solution

* Store and warehouse associates have access to iOS or Android mobile devices during their shifts, either personal or provided by the merchant

* Products managed by using the Store Fulfillment solution must have product attributes that include either a SKU or UPC product.

### Supported platforms

* Adobe Commerce on Cloud (ECE) : 2.4.x
* Adobe Commerce on premises (EE) : 2.4.x
* Magento Open Source 2.4.x
