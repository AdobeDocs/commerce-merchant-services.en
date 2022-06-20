---
title: Connect Commerce Data to Adobe Experience Platform
description: Learn how to connect your Commerce data to the Adobe Experience Platform.
---
# Connect Commerce data to Adobe Experience Platform {#connectaep}

Before you connect your Adobe Commerce data to the Adobe Experience Platform, you need to sign in to your Adobe account in the [Commerce Services Connector](../landing/saas.md#organizationid). After you sign in and select your organization ID, you can then specify the scope and datastream ID on the **Experience Platform Connector** page in the Admin.

1. In the Admin, go to **System** > Services > **Experience Platform Connector**.

1. In the **Scope** drop-down, select the context, or “scope” of the store view.

   The Organization Id is global. Only one Organization Id can be associated per Adobe Commerce instance.

1. In the **IMS Organization** field, you will see the ID associated with your Adobe Experience Platform account, as configured in the [Commerce Services Connector](../landing/saas.md#organizationid).

1. In the **Datastream ID** field, paste the ID of the data stream you [created](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) in Adobe Experience Platform.

## Relationship of Datastream ID and your Commerce Instance Storeview

The Datastream ID enables event-forwarding from Adobe Experience Platform to other Adobe DX products and can be associated to a specific storeview within your specific Adobe Commerce instance. You also can associate multiple storeviews to the same Datastream ID. It depends on what makes the most sense for your business.

## Field descriptions

| Field | Description |
|--- |--- |
| Scope | Specific storeview where you want the configuration settings to apply |
| IMS Org (Global)| ID that belongs to the organization that purchased the Adobe DX product. This ID links your Adobe Commerce instance to Adobe Experience Platform. |
| Datastream ID (Storeview) | ID that allows data to flow from Adobe Experience Platform to other Adobe DX products. This ID can be associated to a specific storeView within your specific Adobe Commerce instance. |

With the Experience Platform connector extension installed, the link between Adobe Commerce and Adobe Experience Platform created, and the Datastream ID specified, [!DNL Commerce] data will begin flowing to the Adobe Experience Platform edge and to other Adobe DX products.

## Commerce data at the edge

When Commerce data is sent to the Adobe Experience Platform edge, you can build reports like the following:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
