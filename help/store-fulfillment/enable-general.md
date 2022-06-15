---
title: General configuration
description: Configure general settings to enable [!DNL Store Fulfillment] for your store. Configure global extension settings, system settings for logging, data synchronization, and security. Provide key data to enable the integration between Adobe Commerce and Store Fulfillment services.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
---
# General Configuration

In the Adobe commerce Admin, configure general configuration settings to enable [!DNL Store Fulfillment] services for your store, configure global extension settings, and provide key data for the integration by configuring the [!UICONTROL Account Credentials].

The integration must be connected to the Store Fulfillment service. Also, configure the Store Fulfillment general settings to enable and customize Store Fulfillment services based on your organization's capabilities and operational requirements.

The general configuration for [!DNL Store Fulfillment] includes the following configuration settings:

- [Enable the solution](#enable-the-store-fulfillment-solution)
- [Manage Account credentials to connect to Store Fulfillment services](#account-credentials)
- [Configure Logging](#configure-logging)
- [Set options for managing order and error synchronization operations](#order-synchronization)
- [Enable Store Fulfillment shipping options](#enable-store-fullment-shipping-options)
- [Configure security and authentication settings for the Store Fulfillment App](#store-fulfillment-app)
- [Set Delivery method availability and messaging configuration](#in-store-delivery-methods)

## Enable the Store Fulfillment solution

| **Field**                | **Description**                                                                                                                                                                                                                                                                                                                                                                                  | **Scope** | **Required** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | Enable or disable the solution. When enabled, configure and use Store Fulfillment capabilities and establish the connection between your Adobe Commerce store and Store Fulfillment services. When disabled, all Store Fulfillment features are disabled and there is no communication between Adobe Commerce and Store Fulfillment services. Order information cannot be processed or received. | Global    | Yes          |

To complete this setup, see **Stores → Configuration → Services → Store Fulfillment by Walmart Commerce Technologies**.

## Add Account Credentials

| **Field**                              | **Description**                                                                                                                                                                                                                                                                                                                                                               | **Scope** | **Required** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]**           | Can select *Sandbox* or *Production*:</br> Sandbox communicates with the fulfillment services in a test.</br>Production communicates with a live environment. Use **only** in production.</br>You are given a set of credentials for each environment and are able to manage both sets in the same installation. </br></br>Save credentials before validating the connection. | Global    | Yes          |
| **[!UICONTROL API Server URL]**        | The URL to the Walmart Store Fulfillment API endpoint. This must be fully-qualified URL that is provided to you during your onboarding process. Store Fulfillment customers receive both a Sandbox and Production URL. Please ensure to copy/paste the full URL, including trailing slash "/".                                                                                | Global    | Yes          |
| **[!UICONTROL Token Auth Server URL]** | The URL to the Walmart Store Fulfillment Authentication endpoint. The value must be the fully-qualified URL that is provided to you during your onboarding process. You receive both a Sandbox and Production URL. Please ensure to copy/paste the full URL, including trailing slash `/`".                                                                                   | Global    | Yes          |
| **[!UICONTROL Merchant Id]**           | Your unique merchant (tenant) ID provided to you during your onboarding process. Your ID is used to route your orders and ensures that your merchant stores are receiving them.                                                                                                                                                                                               | Global    | Yes          |
| **[!UICONTROL Consumer Id]**           | Your unique integration ID. This is provided to you during your onboarding process. It does not change. It is used to authenticate all communication with the fulfillment services.                                                                                                                                                                                           | Global    | Yes          |
| **[!UICONTROL Consumer Secret]**       | Your unique integration key. This is provided to you during your onboarding process. It is used to authenticate all communication with the fulfillment services.                                                                                                                                                                                                              | Global    | Yes          |

After you've configured the Account Credentials, select **[!UICONTROL Validate Credentials]** to verify and establish a connection to the fulfillment web service for the first time.

## Configure Logging

When logging is enabled, your log file can quickly expand. To prevent response time issues in production environments, be careful about enabling logging, and enable only for a short time when needed. 

Ask the system administrator to configure your environments to allow exception handling so that API-related exceptions can be captured through the firewall or cache. You can also ask your system administrator to set up log rotation on this file to minimize size.

| **Field**      | **Description**                                                                                                                                                                                                                                 | **Scope** | **Required** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Debug Mode** | Debug Mode is used to increase the logged activity within the integration. When disabled, no debug information is logged. When enabled, all debug information is logged.</br> All logged data can be found in file: `var/log/walmart-bopis.log` | Global    | No           |

## Manage Order synchronization

Configure the settings to manage error handling for order  synchronization, catalog attributes to use for barcode scanning during order picking, and configure order batch sizes for the store fulfillment queue.

You can view details about order synchronization operations from the Store Fulfillment Queue Management dashboard in the Admin (
**[!UICONTROL System > Tools > Store Fulfillment Queue]**).

### Synchronization Error Management

| **Field**                               | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | **Scope**  | **Required** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Retry Critical Error**                | Specifies the retry attempts for a record synchronization operation after a critical error occurs.</br></br>Critical errors occur anytime the integration fails to get a positive response from the fulfillment service. This can occur when the service is down or when there is an error in the order data being sent.</br></br>When the retry threshold is reached, the item remains in a queue but is not processed again. View all items with errors from **[!UICONTROL System → Tools → Store Fulfillment Queue]** Management in the Admin. To troubleshoot consistently failing items, contact your Account Manager. | Global     | No           |
| **Enable Error Notification Email**     | Enable error notifications to receive an email when the [!UICONTROL Retry Critical Error Threshold] is reached for an order. The notification includes any available details about the error.                                                                                                                                                                                                                                                                                                                                                                                                                               | Global     | No           |
| **Send Error Notification Email To**    | A comma-delimited list of recipient email addresses for error notifications.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Global     | No           |
| **Order Sync Exception Email Template** | Specifies the email template used to notify recipients about order synchronization errors. A default template is provided. It does not support customization.                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Store View | No           |

### Order Synchronization

| **Field**                            | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | **Scope** | **Required** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]**      | The catalog attribute that stores the scannable code for corresponding items in your merchant locations.</br></br>If you have only one existing merchant location, it is likely that you use UPC codes, while your e-commerce channel identifies products by SKU. If this is your scenario, select the catalog attribute that contains the UPC code.</br></br>This setting ensures that orders sent to your merchant stores list items with the correct identifier so that store associates can accurately scan items during the picking process.</br></br>If you are unsure, check with your fulfillment associates in the Shipping and Picking department to determine which attribute should be sent. You might need to add the appropriate attribute to the Adobe Commerce product attribute set if the attribute is not currently included in the database. | Website   | Yes          |
| **[!UICONTROL Barcode Type]**        | The catalog attribute that stores the barcode source for corresponding items in your merchant locations.</br></br>This setting ensures that orders sent to your merchant stores list items with correct identifier so that store associates can accurately scan items during the picking process. The options include - SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.</br></br>If you are unsure, select the option that most closely resembles the values contained in your [!UICONTROL Barcode Source] attribute. Store associates can still match items manually from their pick list.                                                                                                                                                                                                                                          | Website   | Yes          |
| **[!UICONTROL Max Number of Items]** | The maximum number of items to send from the store fulfillment queue at one time.</br></br>BOPIS orders are sent to the fulfillment service in batches, at regular intervals. This setting allows you to control the size of the batch.</br></br>The default value is 100 items. Depending on your order volume and capacity, you might need to adjust this value up or down.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Global    | No           |


## Enable Store Fulfillment shipping options

Configure the Store Fulfillment shipping options that determine the availability of in-store pickup and home delivery options for your Adobe Commerce stores.

### Ship To Store

| **Field**                             | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | **Scope** | **Required** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | The ship-to-store setting leverages your existing ship-to-store capabilities. If you use Inventory Management, or if you can accept and fulfill orders at merchant locations with no inventory via store-to-store inventory transfers, set this option to `Yes`.</br></br>If you cannot support the ship-to-store option or do not wish to offer it, set to `No`. When disabled, items in your catalog with zero inventory for a merchant store, or items that are below that location's [!DNL Out of Stock Threshold], are not offered with in-store pickup options.</br></br>This is a global setting that can be adjusted per merchant location. | Global    | No           |

### Ship From Store

| **Field**                               | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | **Scope** | **Required** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | Enables or disables the Home Delivery option in your merchant stores. When enabled, your merchant store locations are considered in aggregate with other assigned sources in the stock associated to your website.</br></br>In standard Inventory Management services, the [!DNL Ship from Store] is option is inherent and cannot be disabled. With the Store Fulfillment solution, you have the option to turn it on or off.</br></br>This is a global setting. You can also adjust this setting per merchant location and product. | Global    | No           |


## Manage Store Fulfillment App use accounts and permissions

Configure the settings for the Store Fulfillment App user account and password security and two-factor authentication.

### App Security

| **Field**                                                  | **Description**                                                                                                                                                                                      | **Scope** | **Required** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]**                     | The timeframe, in seconds, that a store associate user session remains active before automatic logout. Valid values range from 60 to 31536000.                                                       | Global    | No           |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | Specifies the number of failed login attempts allowed before a store associate is locked out of their account.</br></br>To disable account lockout, set the value to 0.                              | Global    | No           |
| **[!UICONTROL Lockout Time (minutes)]**                    | Number of minutes to lock an account after login failure.                                                                                                                                            | Global    | No           |
| **[!UICONTROL Force Password Change]**                     | Determines if a user password change is required.</br></br>`Yes`: Require the user to change their password after account setup.</br>`No`: Recommends that user change password after account setup. | Global    | No           |
| **Password Lifetime**                                      | The number of days that a password remains valid before a required password change. Leave empty to disable this option.                                                                              | Global    | No           |

### Two-factor authentication

| **Field**          | **Description**                                                                                                                                                                                                                                                                            | **Scope** | **Required** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **APP User 2FA**   | Enable or disable two-factor authentication for store associates. When enabled, the store associate is prompted to provide a one-time password generated by an authentication provider.                                                                                                    | Global    | No           |
| **APP 2FA Policy** | Sets the enforcement policy for two-factor authentication.</br></br>**[!UICONTROL Optional]**: The store associate can bypass two-factor authentication if no provider is set.</br></br>**[!UICONTROL Mandatory]**: The store associate is required to complete two-factor authentication. | Global    | No           |
| **2FA Providers**  | Select one or more authentication provider services to offer store associates. To set up two-factor authentication and authenticate, store associates must install the authentication app from one of the available providers installed on their mobile devices.                           | Global    | No           |

### Delivery Methods 

Store Fulfillment works by extending the native Adobe Commerce [!DNL In-Store Delivery] capabilities. 
After you install the extension, additional Admin configuration options are available for in-store delivery methods. Configure these additional options from the Admin by selecting **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

In the Store Fulfillment settings, you can configure the following delivery methods for In-Store Pickup orders.

- **In-store pick up**—Offer options for in-store delivery during the checkout process
This is the most common delivery scenario for BOPIS orders.

- **Curbside pick up**–Offer options for customers  to park at a store location and have their order delivered to them by a  store associate.

#### Delivery Methods Configuration

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **Field**                               | **Description**                                                                                                                                                                                                                                                                                                               | **Scope** | **Required** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | Enable or disable the in-store pick up option available during checkout for customers that choose store pickup. When in-store pickup is disabled, the option is not displayed.</br></br>This global setting applies to all retail store locations. When enabled, you can selectively disable it at the retail store location. | Website   | No           |
| **Enable Curbside Pickup**              | Enable or disable the curbside pick up option during the checkout process for customers that choose store pickup.</br></br>This global setting applies to all retail store locations. When enabled, you can selectively disable it at the retail store location.                                                              | Website   | No           |

For details about customizing the delivery methods at selected retail store locations, see **Retail Store Configuration**.

#### Delivery Method Title Configuration

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Home Delivery Title</strong></td>
<td>Specifies the title to display for the Home Delivery option in the product, cart, and checkout areas. Home delivery refers to the standard shipping capabilities of Adobe Commerce, from a warehouse, by a carrier, direct to the customer-provided shipping address.</br></br>This label does not affect the selected shipping carrier or their available shipping method labels.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Home Delivery Description</strong></td>
<td>An optional description that displays whenever the Home Delivery Title is shown to customers. Most often, the description is a static message to communicate your delivery promises. Some examples:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Store Pickup Title</strong></td>
<td>When a customer is presented with delivery options and in-store pickup is available, this label is shown.</br></br>You can customize this label, which displays in the product, cart, and checkout areas.</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Store Pickup Description</strong></td>
<td>Wherever the Store Pickup Title is shown, you can optionally include a description. This static message helps improve customer communications related to the store pickup experience. Some examples:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>In-Store Pickup Title</strong></td>
<td>When In-Store Pickup is enabled, this title is shown to customers as the Store Pickup delivery option. You can customize its label.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<tr>
<td><strong>Curbside Pickup Title</strong></td>
<td>When Curbside Pickup is enabled, the option is shown to customers as a type of Store Pickup delivery option. You can customize its label here.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>In-Store Pickup Instructions</strong></td>
<td>When an order is ready for pickup at your retail stores, the customer is notified by e-mail. If the customer selected [!DNL In-Store Pickup] during checkout, you can customize the pickup instructions here.</br></br>This is a global setting that applies to all retail store locations. You can also customize the instructions at the retail store location level.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Curbside Pickup Instructions</strong></td>
<td>Specifies customized order pick up instructions to include in customer email notifications for curbside pickup orders.</br></br>This is a global setting that applies to all retail store locations. You can also customize the instructions at the retail store location level.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Estimated Pickup Lead Time</strong></td>
<td>The number of minutes required before an order is received, fulfilled, and ready to be picked up. This information is shown to the customer when selecting a retail store location for Store Pickup delivery option.</br></br>This is a global setting and applies to all retail store locations. You can also customize the lead time at the retail store location level.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Estimated Pickup Time Label</strong></td>
<td>Displays the estimated time until an order is available for customer pickup. This information is shown to customers when they select a retail store location for Store Pickup delivery option.</br></br>When customizing this label, you can use the code <code>%1</code> to insert your <strong>Estimated Pickup Lead Time</strong>.For example:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>This is a global setting that applies to all retail store locations. You can also customize the lead time at the retail store location level.</td>
<td>Store View</td>
<td>No</td>
<tr>
<td><strong>Pickup Time Disclaimer</strong></td>
<td>The content displayed on the product page in the tooltip that lists store hours, holidays, unexpected closures, and so on</td>
<td>Store View
</td>
<td>No
</td>
</tr>
</tbody></table>

#### Stock Availability Titles Configuration

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>In-Stock</strong></td>
<td>When a customer is using the retail store locator, inventory availability for the current item(s) is shown for each location.</br></br>You can customize the “in-stock” status label here.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Out-of-Stock</strong></td>
<td>When a customer is using the retail store locator, inventory availability for any current items is shown for each location.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Partially In-Stock</strong></td>
<td>When a customer is using the retail store locator, inventory availability for any current items ia shown for each location.</br></br>You can customize the “partially in-stock” status label here.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>
