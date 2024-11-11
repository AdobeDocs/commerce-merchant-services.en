---
title: Tracking your shipments in [!DNL Payment Services]
description: Customize [!DNL Payment Services] shipments and tracking information displayed in the Paypal Merchant Dashboard.
feature: Payments
exl-id: 17aede1f-56ae-441a-b723-3193e865e469
---
# Tracking your shipments in [!DNL Payment Services]

[!DNL Payment Services] enables merchants to see the tracking information for a shipment in their PayPal Merchant Dashboard.

See [shipments](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/shipments){target=_blank} topic for more information on the shipments grid for Adobe Commerce.

## How tracking your shipment works

This functionality is dependent on whether the order has been invoiced, as PayPal must receive a `capture_id` to process the tracking information. If a merchant ships their products before capture, the tracking information is not sent to PayPal.

>[!NOTE]
>
> It is recommended to create one shipment per tracking number, associating the correct items with the shipment.

## Adding the tracking number

The following instructions will walk you through the process to create a shipment in Adobe Commerce with [!DNL Payment Services]:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.

1. In the **[!UICONTROL Action]** column for the selected order, click **[!UICONTROL View]**.

1. Click **[!UICONTROL Ship]**.

1. Scroll down to the **[!UICONTROL Payment & Shipping Method]** block and click **[!UICONTROL Add Tracking Number]** in **[!UICONTROL Shipping Information]**.

1. Set the **[!UICONTROL Carrier]**.

1. To track the shipment, enter the **[!UICONTROL Title]** and **[!UICONTROL Number]** .

1. Click **[!UICONTROL Submit Shipment]**.

>[!NOTE]
>
> Alternatively, you may be using a shipping module to enter the tracking number information. Ensure that the shipping module is saving the tracking number information in the `tracking_number` field.

### Compatibility with third parties

Any third-party extension is compatible with the functionality when a shipment entity is created through [Commerce API](https://developer.adobe.com/commerce/webapi/rest/attributes/#ShipmentRepositoryInterface){target=_blank}.
