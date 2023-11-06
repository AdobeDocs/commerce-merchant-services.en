---
title: Add Field Groups to XDM Schema
description: Learn how to add Adobe Commerce-specific field groups to an XDM schema.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
---
# Add field groups to XDM schema

One of the [onboarding steps](overview.md#onboarding-steps) to using the Data Connection extension is to access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) that is specific to Adobe Commerce. When you create that datastream, you must also select an XDM schema that represents the data you plan to ingest. This topic provides you with the field groups your XDM schema must include to successfully collect the data provided by the Adobe Commerce [events](events.md).

1. If you do not already have an XDM schema, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) one. Otherwise, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) your existing XDM schema in the Adobe Experience Platform UI.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following Commerce-specific field groups:
    
    - Site Search 
    - Visit Web Page
    - User Login Process
    - Reference Keys
    - Personal Contact Details 
    - Commerce Details
    - Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)
    - Identity Map
    
    >[!NOTE]
    >
    > Do not set any Commerce-specific field groups as `Primary identity`. Doing so identifies the field as required and Experience Platform expects that field in every event. If that field is absent, data ingestion fails.
    
    Your XDM schema now contains Commerce-specific field groups so that the data collected from the Commerce [events](events.md) is represented in the XDM.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.
