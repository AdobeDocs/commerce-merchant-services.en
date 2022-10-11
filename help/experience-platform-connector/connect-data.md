---
title: Connect Commerce Data to Adobe Experience Platform
description: Learn how to connect your Commerce data to the Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
---
# Connect Commerce data to Adobe Experience Platform {#connectaep}

To connect your Adobe Commerce instance to the Adobe Experience Platform, you must provide an organization ID and a datastream ID.

![Experience Platform connector configuration](assets/epc-config.png)

1. Sign in to your Adobe account in the [Commerce Services Connector](../landing/saas.md#organizationid) and select your organization ID.

1. In the Admin, go to **System** > Services > **Experience Platform Connector**.

1. In the **Scope** drop-down, set the context to **Website**.

1. In the **Organization ID** field, you see the ID associated with your Adobe Experience Platform account, as configured in the [Commerce Services Connector](../landing/saas.md#organizationid). The organization ID is global. Only one organization ID can be associated per Adobe Commerce instance.

1. In the **Datastream ID** field, paste the ID of the datastream you [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) in the Adobe Experience Platform.

    >[!NOTE]
    >
    >The scope of the datastream ID must be set at the website level or higher. At that level, the same datastream ID is used for each website in the hierarchy. You cannot set the datastream ID scope at the storeview level.

1. (Optional) If you do not have an AEP Web SDK deployed to your site, leave this field blank and the Experience Platform connector deploys one for you. Otherwise, add the name of the AEP Web SDK.

## Field descriptions

| Field | Description |
|--- |--- |
| Scope | Specific website where you want the configuration settings to apply. |
| Organization ID (Global)| ID that belongs to the organization that purchased the Adobe DX product. This ID links your Adobe Commerce instance to Adobe Experience Platform. |
| Datastream ID (Website) | ID that allows data to flow from Adobe Experience Platform to other Adobe DX products. This ID must be associated to a specific website within your specific Adobe Commerce instance. |
|AEP Web SDK Name (Global)| If you do not have an AEP Web SDK deployed to your site, leave this field blank and the Experience Platform connector deploys one for you. If you already have an AEP Web SDK deployed to your site, specify the name of that SDK in this field. This allows the Storefront Event Collector and Storefront Event SDK to use your AEP Web SDK rather than the version deployed by the Experience Platform connector.|

With the Experience Platform connector extension installed, the link between Adobe Commerce and Adobe Experience Platform created, and the Datastream ID specified, Commerce data begins to flow to the Adobe Experience Platform edge and to other Adobe DX products. 

>[!NOTE]
>
> The amount of time it takes for data to flow from the edge to other Adobe DX products can vary.

## Commerce data at the edge

When Commerce data is sent to the Adobe Experience Platform edge, you can build reports like the following:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
