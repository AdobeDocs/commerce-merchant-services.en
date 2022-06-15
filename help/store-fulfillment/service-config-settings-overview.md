---
title: Configuration overview for Store Fulfillment
description: Learn about the Admin configuration settings categories available for the Store Fulfillment solution and how they are configured.
role: User, Admin
level: Intermediate
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
---
# Configuration Overview for Store Fulfillment

In the Adobe Commerce Admin, the configuration settings for Store Fulfillment Services by Walmart Commerce Technologies are categorized by type.

**Store Fulfillment configuration settings by type**

| **Type**                                                                 | **Description**                                                                                                                                                          | **API Configurable** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [General Configuration](enable-general.md)                               | General integration set up for the Store Fulfillment solution, its active features, and credentials to connect to fulfillment services.                                  | No                   |
| [Sales Email Configuration](sales-emails.md)                             | Set up additional e-mail templates for customer notifications sent during the check-in process.                                                                          | No                   |
| [Merchant Store Configuration](merchant-store-configuration.md)          | Set up enhanced Inventory Management sources as merchant stores.                                                                                                         | Yes                  |
| [Product Stock Management](product-stock.md)                             | Configure the merchant stock messaging and features available to customers.                                                                                              | Yes                  |
| [Inventory Management Source Transfer](inventory-stock-transfer.md)      | Set up a new stock, transfer inventory out of default stock.                                                                                                             | Yes                  |
| [Multiple Website/Scope Configuration](multi-site-and-scope-config.md)   | Configure stocks and delivery methods for multiple websites/store scopes.                                                                                                | No                   |
| [Background Process System Configuration](background-processes.md)       | Configure the schedules for background processes used in synchronizing data with the fulfillment services.                                                               | No                   |
| [Store Location and Mapping Setup](store-location-map-provider-setup.md) | Configure the ability to use a distance provider to search for retail stores and to display this information in the SLS map                                              | Yes                  |
| [Check-In Experience Setup](store-location-map-provider-setup.md)        | Configure the car color and car make options that will be available during the check-in process                                                                          | Yes                  |
| [User Setup](user-setup.md)                                              | Manage user accounts, roles, and permissions for store associates that use the Store Assist app. scopes.                                                                 | Yes                  |
| [App Setup](app-setup.md)                                                | Review available configurations for the Store Assist App required to complete the onboarding process. These settings cannot be configured from the Adobe Commerce Admin. | Yes                  |


## Use the configuration reference

View the configuration reference for each setting type by selecting the type name in the _Store Fulfillment configuration settings by type_ table. 

In the configuration reference for each type, the configuration details are displayed in a table with the following column headers:

- **Field** refers to the name of the field to configure

- **Description** provides important details about the purpose and behavior of the field

- **Scope** indicates the Adobe Commerce configuration scope for the setting (global, website, store)

- **Required** value indicates whether a value must be set on the field

For technical reference, you can also find the internal configuration path for each field.
