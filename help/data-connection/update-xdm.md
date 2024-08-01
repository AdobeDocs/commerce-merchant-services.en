---
title: Update Time Series Event Schemas for Commerce Data Ingestion
description: Learn how to create a schema, dataset, and datastream to collect and send time series event data for Commerce data ingestion.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
---
# Update Time Series Event Schemas for Commerce Data Ingestion

One of the [onboarding steps](overview.md#onboarding-steps) for using the [!DNL Data Connection] extension is to access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) that is specific to Adobe Commerce. When you create that datastream, you must also select a schema that describes the data you plan to ingest. That schema must include commerce-specific field groups.

This article provides you with the field groups your schema must include to successfully collect the following time series data provided by the Adobe Commerce events:

- [Behavioral](events.md) - Includes storefront, profile, search, and B2B events.
- [Back office](events-backoffice.md) - Includes order status and profile events.

Learn more about [time series data](data-ingestion.md).

Learn more about the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Update schema with time series behavioral and back office event data

In this section, you learn how to update your existing schema or create a schema to include behavioral and back office event data.

>[!NOTE]
>
>See [time series profile event data](#time-series-profile-event-data) to learn how to add profile-specific fields.

1. If you do not already have a schema, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) one with the class set to **Experience Event**. 

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following Commerce-specific field groups (or edit your existing schema and add these field groups):
    
    - Site Search 
    - Visit Web Page
    - User Login Process
    - Reference Keys
    - Personal Contact Details 
    - Channel Details
    - Commerce Details
    - Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)

    >[!NOTE]
    >
    > Do not set any Commerce-specific field groups as `Primary identity`. Doing so identifies the field as required and Experience Platform expects that field in every event. If that field is absent, data ingestion fails.
    
    Your schema now contains Commerce-specific field groups so that the time series data collected from the Commerce [behavioral](events.md) and [back office](events-backoffice.md) events is represented in the schema.

1. [Enable](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) the schema for Profile.

    When a schema is enabled for Profile, any datasets created from this schema participate in Real-Time CDP, which merges data from disparate sources to construct a complete view of each customer.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.

With the schemas, datasets, and datastreams configured for behavioral and back office data, you can [configure](connect-data.md#data-collection) your Commerce instance to collect and send that data to the Experience Platform.

To include your shopper's profile information, see [time series profile event data](#time-series-profile-event-data).

### Add custom attributes

You can use custom attributes if you want to pass custom back office event data from your Commerce instance to the Experience Platform.

Custom attributes are supported at two levels:

- Order level 
- Order item level

>[!NOTE]
>
>Adobe Commerce supports custom attributes that have a datatype of string or string array.

1. Add and enable an additional module in your [!DNL Commerce] application. See the following [example](https://github.com/shiftedreality/beacon-backoffice-custom-events/blob/main/BeaconDemo/Plugin/ModifyOrder.php).

    You need to modify the example code to expose additional custom attributes. The implementation varies based on where these attributes are stored and the logic required to extract them. 

1. Extend your existing XDM schema. Refer to the following [guide](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) to create custom attributes for Order and Order item levels. The Tenant ID field is dynamically generated, however the field structure should resemble the example provided.

    >[!IMPORTANT]
    >
    >XDM custom attributes must match the attributes sent from [!DNL Commerce].

1. Make sure that the datastream associated with your XDM schema is the same datastream specified on the [Data Collection](connect-data.md#data-collection) tab.

1. Click **[!UICONTROL Save]** on the **Data Collection** tab to retrieve any custom attributes you have specified.

## Time series profile event data

Time series profile event data is generated from the following events:

- [`accountCreated`](events-backoffice.md#accountcreated)
- [`accountUpdated`](events-backoffice.md#accountupdated)
- [`accountDeleted`](events-backoffice.md#accountdeleted)

If you want to ingest your customer's profile event data into the Experience Platform, you can update your existing Commerce schema and use the same datastream already configured, or you can create a profile-specific datastream and schema. That decision is based on your company's data governance. The next two sections walk you through either case.

### Send time series profile event data to Experience Platform using your existing datastream

If you want to add time series [server-side profile event data](events-backoffice.md#customer-profile-events-server-side) to your existing Commerce datastream, add the `Demographic Details` field group to your schema. Your schema now contains the following Commerce-specific field groups:

- Site Search 
- Visit Web Page
- User Login Process
- Reference Keys
- Personal Contact Details
- Channel Details
- Commerce Details
- Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)
- New: **Demographic Details**

With the addition of the `Demographic Details` field group in your existing Commerce schema, the dataset and datastream already associated with your Commerce schema is used for this time series profile data.

### Send time series profile event data to Experience Platform in a separate datastream

If you want to add [server-side profile event data](events-backoffice.md#customer-profile-events-server-side) to a new profile-specific datastream and schema, complete the following steps.

1. [Create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) a schema and set the class to **Experience Event**.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following profile-specific field groups:
    
    - Demographic Details
    - Personal Contact Details
    - Channel Details
    - Commerce Details

1. [Enable](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) the schema for Profile.

    When a schema is enabled for Profile, any datasets created from this schema participate in Real-Time CDP, which merges data from disparate sources to construct a complete view of each customer.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema that you created.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.

With the schemas, datasets, and datastreams configured for customer profile data, you can [configure](connect-data.md#data-collection) your Commerce instance to collect and send that data to Experience Platform.

To create a schema, dataset, and datastream for profile record data, see [send profile record data to the Experience Platform](profile-data.md).
