---
title: Merchant Stores Configuration
description: Setup enhanced Inventory Management sources as merchant stores.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
---
# Merchant Stores (Source) Configuration

This solution enhances the native Inventory Management capabilities by extending stock sources with operations-oriented features for merchants.

- Add geographic coordinates for the store location
- Designate the source as a [!DNL Store Pickup Location] and specify available shipping capabilities (Ship to Store, Ship from Store)
- Specify available pickup options (in-store or curbside), customized pickup instructions, and other information to communicate pickup details and instructions to customers

The terms _source_ and _merchant store location_ are used interchangeably. All records are inventory sources, but sources can also be merchant store locations, depending on the configuration settings.

Manage Merchant Stores configuration from the Admin: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>During the setup process, it might be necessary to flush the cache after you create sources or update existing sources.

## **General**

<table>
<tbody>
<tr>
<th>Field</th>
<th>Description</th>
<th>Scope</th>
<th>Required</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Latitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation.</td>
<td>Global</td>
<td>Yes</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Longitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation.</td>
<td>Global</td>
<td>Yes</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designate the source as an available Store Pickup location. This setting determines whether the source is  synchronized and displayed to visitors.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Configure ship-to-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Latitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation.</td>
<td>Global</td>
<td>Yes</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Longitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation.</td>
<td>Global</td>
<td>Yes</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designate the source as an available Store Pickup location. This setting determines whether the source is  synchronized and displayed to visitors.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Configure ship-to-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Configure ship-from-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
<td>Configure ship-from-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>



| **Field**                                                                                        | **Description**                                                                                                                                                                                                                      | **Scope** | **Required** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude`                                         | Latitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation.  | Global    | Yes          |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude`                                       | Longitudinal coordinate of the merchant store location. This required information is used in location search and map placement on the storefront experience. The value must match the exact address of the store to pass validation. | Global    | Yes          |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]`    | Designate the source as an available Store Pickup location. This setting determines whether the source is  synchronized and displayed to visitors.                                                                                   | Global    | No           |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]`      | Configure ship-to-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, **[!UICONTROL Enable Ship To Store]**.                                                    | Global    | No           |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Configure ship-from-store capabilities at the source level. For more information, see the [General Configuration](enable-general.md) option, [!UICONTROL Enable Ship From Store]                                                     | Global    | No           |

{style="table-layout:auto"}

## Pickup Location configuration

| **Field**                                                                                     | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | **Scope** | **Required** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | One of two pickup options. [!DNL In-Store Pickup] refers to the ability to allow a customer to enter the merchant store location to retrieve their order. </br></br>When enabled, this option might be presented to the customer during checkout. </br></br>This option also overrides the global configuration to [!UICONTROL Enable In-store Pickup] that was configured on the [!UICONTROL Delivery Method] for [!UICONTROL In-store Pickup]                                                                                                                                             | Global    | No           |
| **In-Store Pickup Instructions**</br>`Extension Attribute: store_pickup_instructions`         | A customizable message delivered to the customer in the **Order Ready For Pickup in Store** email notification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Global    | No           |
| **Allow Curbside**</br>`Extension Attribute: curbside_enabled`                                | One of two pickup options. Curbside delivery allows a customer to park their vehicle in a designated spot at the merchant store location. In this scenario, the order is delivered to the customer by a store associate. </br></br>When enabled, this option may be presented to the customer during checkout. Also, the customer might be asked to describe their vehicle and parking spot during the Check-In process. </br></br>This option also overrides the global configuration to **Enable Curbside Pickup** that was configured on the **Delivery Method** for **In-store Pickup** | Global    | No           |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions`       | A customizable message delivered to the customer in the [!UICONTROL Order Ready For Pickup in Store] email notification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Global    | No           |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time`       | The number of minutes required before an order is received, picked, and ready to be picked up. </br></br>This information is used display estimated times for order pickup to customers on the website.</br></br> Setting this option overrides the global configuration for **Estimated Pickup Lead Time** configured for the **Delivery Method** in the **In-store Pickup** configuration.                                                                                                                                                                                                | Global    | No           |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label`     | Label that displays the number of minutes until an order is ready to be picked up.</br></br> When customizing this label, you can use the code %1 to insert your **Estimated Pickup Lead Time**.</br></br> Setting this option overrides the global configuration for [!UICONTROL Estimated Pickup Time Label] configured for the [!UICONTROL Delivery Method] in the [!UICONTROL In-store Pickup].                                                                                                                                                                                         | Global    | No           |

### **Opening Hours**

| **Field**                                                                                            | **Description**                                                                                                                                                                                          | **Scope** | **Required** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone`                               | The timezone of the merchant store location. For each day, set the opening and closing times.</br></br>These settings are used to optimize estimated pickup times, and in fulfillment service reporting. | Global    | Yes          |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | The operating hours for the merchant store location. </br></br>This information can be used to optimize estimated pickup times, and in fulfillment service reporting.                                    | Global    | Yes          |

### Configure Check-in Experience interface options



| **Field**                                                                                                                 | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                | **Scope** | **Required** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled`                                       | Specify whether the merchant store location has designation parking spots for curbside pickup. </br></br>When enabled, you can configure available parking spots.                                                                                                                                                                                                                                                                              | Global    | No           |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory`                     | Specify whether parking spot identification is required for customers during shopping experience.</br></br>If enabled, the customer is prompted to specify their parking spot upon arrival. If disabled, the customer can skip this input.                                                                                                                                                                                                     | Global    | No           |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows`                 | The available parking spots available at this merchant store location for curbside pickup. Use the provided interface to name each spot.</br></br> You do not need to name every parking spot, only the spots designated for curbside. For example, you may have rows A-G of parking available, but only the first 8 spots of row A are designated for curbside pickup. In this scenario, you might define 8 spots; ex: A1, A2, A3, and so on. | Global    | No           |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled`                  | When enabled, this setting allows the customer to describe their parking spot during Check-In.                                                                                                                                                                                                                                                                                                                                                 | Global    | No           |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color`                                                   | Specify whether to support collection of vehicle color from the customer during Check-In. </br></br> The available selections for [!UICONTROL Car Color] are configured in the Admin [system settings for the Check-in Experience](check-in-experience-setup.md).                                                                                                                                                                              | Global    | No           |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory`                           | Specify whether vehicle color identification is required for customers during Check-In.</br></br>If enabled, the customer is prompted to specify the color of their vehicle upon arrival. If disabled, the customer can skip this input.                                                                                                                                                                                                       | Global    | No           |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make`                                                    | Specify whether to support collection of vehicle make from the customer during Check-In.</br></br> The available selections for [!UICONTROL Car Make] are configured in the Admin [system settings for the Check-in Experience](check-in-experience-setup.md).                                                                                                                                                                                 | Global    | No           |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory`                             | Specify whether vehicle make identification is required for customers during Check-In.</br></br>If enabled, the customer is prompted to specify the make of their vehicle upon arrival. If disabled, the customer can skip this input.                                                                                                                                                                                                         | Global    | No           |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information`                        | Specify whether to support collection of additional information from the customer during Check-In.                                                                                                                                                                                                                                                                                                                                             | Global    | No           |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Specify whether additional information is required for customers during Check-In. </br></br>If enabled, the customer is prompted to enter additional information upon arrival. If disabled, the customer can skip this input.                                                                                                                                                                                                                  | Global    | No           |
