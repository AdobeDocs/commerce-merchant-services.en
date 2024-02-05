---
title: Add Field Groups to XDM Schema
description: Learn how to add Adobe Commerce-specific field groups to an XDM schema.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
---
# Add field groups to XDM schema

One of the [onboarding steps](overview.md#onboarding-steps) for using the [!DNL Data Connection] extension is to access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) that is specific to Adobe Commerce. When you create that datastream, you must also select an XDM schema that represents the data you plan to ingest. This topic provides you with the field groups your XDM schema must include to successfully collect the data provided by the Adobe Commerce [events](events.md).

1. If you do not already have an XDM schema, [create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) one with the class set to **Experience Event**. Otherwise, [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) your existing **Experience Event** XDM schema in the Adobe Experience Platform UI.

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
    
    Your XDM schema now contains Commerce-specific field groups so that the data collected from the Commerce [events](events.md) is represented in the XDM. If you want to include your shopper's profile data, see [profile records and profile-related data](#profile-records-and-profile-related-data).

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups and the corresponding dataset.

    The datastream forwards the collected data to the dataset. The data is represented in the dataset based on the selected schema.

1. **Beta** (Optional) You can use custom attributes if you must pass custom back office event data from your Commerce instance to the Experience Platform. This feature is in beta. If you would like to join the beta, send an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com). In your request, include the following:

    - Your [Adobe Org ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). For example `organization_id@AdobeOrg`.
    - List of Order level custom attributes.
    - List of Order item level attributes.

    The Adobe Commerce team will contact you with more information and next steps.

## Customer profile data (Beta)

>[!NOTE]
>
>This feature is in beta. If you would like to join the beta, send an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 

The [Data Connection extension](overview.md) connects your Commerce data to the Experience Platform. Part of that data can comprise your shopper's profile information, such as if they create, edit, or delete an account on your site. When that profile data is sent to the Experience Platform, it is forwarded to Adobe's profile management and segmentation service: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

Data intended for use in Experience Platform is grouped into two behavior types:

- **Record data**: Provides information about the attributes of a subject. A subject could be an organization or an individual.
- **Time series data**: Provides a snapshot of the system at the time that an action was taken either directly or indirectly by a record subject.

All XDM schemas describe data that can be categorized as record or time series. The data behavior of a schema is defined by the schema's class, which is assigned to a schema when it is first created. Learn [more](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) about classes in schemas.

This section guides you through the process of collecting and sending record data and time series data from your Commerce site to Real-Time CDP.

### Send record data to Real-Time CDP

When your shoppers create a profile in your Commerce instance, a profile record is created and data is captured. You must create a schema and dataset specific to that profile record before you can stream that profile data into Real-Time CDP.

1. [Create](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) a schema and set the class to **Individual Profile**.

1. [Add](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) the following profile-specific field groups:
    
    - identityMap
    - Demographic Details
    - Personal Contact Details
    - User Account Details

1. [Enable](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) the schema for Profile.

    When a schema is enabled for Profile, any datasets created from this schema participate in Real-Time CDP, which merges data from disparate sources to construct a complete view of each customer.

1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated.

    A dataset is a storage and management construct for a collection of data, typically a table that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

>[!IMPORTANT]
>
>It can take about 10 minutes for a profile record to be available in Real-Time CDP.

The profile record is now available in Real-Time CDP. In the next two sections, you learn how to stream time series data, which in this case is server-side profile event data, to the Experience Platform. Those events are the following:

- [`accountCreated`](./events.md#accountcreated)
- [`accountUpdated`](./events.md#accountupdated)
- [`accountDeleted`](./events.md#accountdeleted)

This data these events collect is linked to the profile record that now exists in Real-Time CDP.

The schema you use for the time series profile event data depends on if you want to use your existing Commerce schema or if you want all profile data to reside in a profile-specific schema. That decision is based on your company's data governance.

### Send time series profile event data to Experience Platform using your existing Commerce schema

If you want to add time series [server-side profile event data](events.md#profile-events-server-side) to your existing Commerce schema, add the following field group: `Demographic Details`. Your existing Commerce schema now contains the following field groups:

- Site Search 
- Visit Web Page
- User Login Process
- Reference Keys
- Personal Contact Details 
- Commerce Details
- Adobe Analytics ExperienceEvent Commerce (if you want to send data to Adobe Analytics)
- New: **Demographic Details**

With the addition of the `Demographic Details` field group in your existing Commerce schema, the dataset and datastream already associated with your Commerce schema is used for this time series profile data.

### Send time series profile event data to Experience Platform in a separate schema

If you want to add [server-side profile event data](events.md#profile-events-server-side) to a new profile-specific schema, complete the following steps.

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

With the schemas, datasets, and datastreams configured for customer profile data, you can [configure](./connect-data.md#customer-profiles-beta) your storefront to send that data to Experience Platform.
