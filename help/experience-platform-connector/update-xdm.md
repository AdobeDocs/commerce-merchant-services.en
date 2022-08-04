---
title: Add field groups to XDM schema
description: Learn how to add Adobe Commerce-specific field groups to an XDM schema.
---
# Add field groups to XDM schema

One of the [prerequisites](overview.md#prereqs) to using the Experience Platform connector is to access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) that is specific to Adobe Commerce. When you create that datastream, you must also select an XDM schema that represents the data you plan to ingest. This topic provides you with the field groups your XDM schema must include to successfully collect the data provided by the Adobe Commerce storefront [events](events.md).

1. If you do not already have an XDM schema, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) one. Otherwise, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) your existing XDM schema in the Adobe Experience Platform UI.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) the following Commerce-specific field groups:
    
    - Commerce
    - Site Search 
    - Visit Web Page
    - User Login Process
    - Reference Keys
    - Personal Contact Details 
    - Commerce Details
    - Adobe Analytics Experience event Commerce (if you want to send data to Adobe Analytics)
    - Person Identifier
    
    >[!NOTE]
    >
    > Do not set any Commerce-specific field groups as `Primary identity`. Doing so identifies the field as required and Experience Platform expects that field in every event. If that field is absent, data ingestion fails.
    
    Your XDM schema now contains Commerce-specific field groups so that the data collected from the Commerce storefront [events](events.md) is represented in the XDM.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups.
