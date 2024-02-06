---
title: Prepare Schema for Data Ingestion
description: Learn how to add Adobe Commerce-specific field groups to a schema.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
---
# Prepare Schema for Data Ingestion

One of the [onboarding steps](overview.md#onboarding-steps) for using the [!DNL Data Connection] extension is to access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) that is specific to Adobe Commerce. When you create that datastream, you must also select a schema that describes the data you plan to ingest. That schema must contain commerce-specific field groups.

This article provides you with the field groups your schema must include to successfully collect the following time series event data provided by the Adobe Commerce [events](events.md):

- [Behavioral](events.md#behavioral-events)
- [Back office](events.md#back-office-events)

Learn more about the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Update schema with time series behavioral and back office event data

In this section, you learn how to update your existing schema or create a new schema to include behavioral and back office event data. See [time series profile event data](#time-series-profile-event-data-beta) to learn how to add profile-specific fields.

1. If you do not already have a schema, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) one with the class set to **Experience Event**. If you already have a schema, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) your schema in the Adobe Experience Platform UI.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following Commerce-specific field groups:
    
    - Site Search 
    - Visit Web Page
    - User Login Process
    - Reference Keys
    - Personal Contact Details 
    - Commerce Details
    - Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)

    >[!NOTE]
    >
    > Do not set any Commerce-specific field groups as `Primary identity`. Doing so identifies the field as required and Experience Platform expects that field in every event. If that field is absent, data ingestion fails.
    
    Your schema now contains Commerce-specific field groups so that the time series data collected from the Commerce [events](events.md) is represented in the schema.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.

1. **Beta** (Optional) You can use custom attributes if you must pass custom back office event data from your Commerce instance to the Experience Platform. This feature is in beta. If you would like to join the beta, send an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com). In your request, include the following:

    - Your [Adobe Org ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). For example `organization_id@AdobeOrg`.
    - List of Order level custom attributes.
    - List of Order item level attributes.

    The Adobe Commerce team will contact you with more information and next steps.

To include your shopper's profile information, see the next section.

## Time series profile event data (Beta)

>[!NOTE]
>
>This feature is in beta. If you would like to join the beta, send an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 

Profile event data comes from the following events:

- [`accountCreated`](events.md#accountcreated)
- [`accountUpdated`](events.md#accountupdated)
- [`accountDeleted`](events.md#accountdeleted)

If you want to ingest your customer's profile event data, you can update your existing Commerce schema and use the same datastream already configured, or you can create a new profile-specific datastream and schema. That decision is based on your company's data governance.

### Send time series profile event data to Experience Platform using your existing datastream

If you want to add time series [server-side profile event data](events.md#profile-events-server-side) to your existing Commerce datastream, add the `Demographic Details` field group to your schema. Your schema now contains the following Commerce-specific field groups:

- Site Search 
- Visit Web Page
- User Login Process
- Reference Keys
- Personal Contact Details 
- Commerce Details
- Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)
- New: **Demographic Details**

With the addition of the `Demographic Details` field group in your existing Commerce schema, the dataset and datastream already associated with your Commerce schema is used for this time series profile data.

### Send time series profile event data to Experience Platform in a separate datastream

If you want to add [server-side profile event data](events.md#profile-events-server-side) to a new profile-specific datastream and schema, complete the following steps.

1. [Create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) a schema and set the class to **Individual Profile**.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following profile-specific field groups:
    
    - Demographic Details
    - Personal Contact Details
    - Commerce Details

1. [Enable](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) the schema for Profile.

    When a schema is enabled for Profile, any datasets created from this schema participate in Real-Time CDP, which merges data from disparate sources to construct a complete view of each customer.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.

With the schemas, datasets, and datastreams configured for customer profile data, you can [configure](./connect-data.md#customer-profiles-beta) your Commerce instance to send that data to Experience Platform.
