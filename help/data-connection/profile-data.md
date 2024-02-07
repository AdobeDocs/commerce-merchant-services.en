---
title: Customer Profile Record Data
description: Learn how to collect and send Commerce profile record data to the Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
---
# Customer profile data (Beta)

>[!NOTE]
>
>This feature is in beta. If you would like to join the beta, send an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 

The [Data Connection extension](overview.md) connects your Commerce data to the Experience Platform. Data intended for use in Experience Platform is grouped into two behavior types:

- **Record data**: Provides information about the attributes of a subject. A subject could be an organization or an individual. For example, record data is generated when a shopper creates an account on your site. This data is ingested into the Experience Platform using a schema that has the class set to **Individual Profile**. You can send that record data to Adobe's profile management and segmentation service: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html). See [send record data to Real-Time CDP](#send-record-data-to-real-time-cdp) to learn more.
- **Time series data**: Provides a snapshot of the system at the time that an action was taken either directly or indirectly by a record subject. For example, when a shopper browses a product on your site, adds a product to their cart, updates their profile, and so on. Time series data is ingested into the Experience Platform using a schema that has the class set to **Experience Event**. See [update schema for Commerce data ingestion](update-xdm.md) to learn how you can update your Commerce schema to handle behavioral, back office, and profile time series data.

## Send record data to Real-Time CDP

When your shoppers create a profile in your Commerce site, a profile record is created and data is captured. You must create a schema and dataset specific to that profile record before you can stream that profile data into Real-Time CDP.

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

With the schema and dataset configured for customer profile record data, you can [configure](connect-data.md#data-collection) your Commerce instance to collect and send that data to Experience Platform.
