---
title: Store Location and Mapping System Configuration
description: Configure a distance provider to support store location mapping in the storefront UI. The Store Fulfillment solutions requires a distance provider to enable retail store search and other mapping and scheduling capabilities for the end-to-end fulfillment workflow.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
---
# Store Location and Mapping Setup

Enable the store location and mapping capabilities for Store Fulfillment by configuring a [distance provider](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) to search for retail store locations.

**Requirements**

During the configuration process, you provide a Google API key for the Google Maps platform. If you do not have one, [generate one from the Google Maps platform](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

To configure the distance provider:

1. From the **[!UICONTROL Stores > General]** configuration in the Admin, add the Google Maps integration for the Map content type.

   - Go to **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Add your Google API Key to **[!UICONTROL Google Maps API Key]** field.

1. From the **[!UICONTROL Stores > Inventory]** configuration in the Admin, select the distance provider for Store Fulfillment.

   - Go to **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expand the **[!UICONTROL Distance Provider for Distance Based SSA]** section.

   - Set the **Provider** to **Google Map**.

1. Configure settings for the **[!UICONTROL Google Distance Provider]**.

   - Add your **Google API key**.

   - Set **[!UICONTROL Computation Mode]** to `Driving` and **[!UICONTROL Value]** to `Distance`
