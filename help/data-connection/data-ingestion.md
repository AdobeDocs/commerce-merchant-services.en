---
title: Types of Commerce Data
description: Learn the types of data that you can collect and send to the Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
---
# Types of Commerce Data

The [Data Connection extension](overview.md) connects your Commerce data to the Experience Platform. Data intended for use in the Experience Platform is grouped into two behavior types: time series data, which belongs to the **Experience Event** class, and record data, which belongs to the **Individual Profile** class.

Learn more about [data behavior](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) and [classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) in Experience Platform.

## Time series data

Time series data provides a snapshot of the system at the time that an action was taken either directly or indirectly by a record subject. For example, when a shopper browses a product on your site, adds a product to their cart, places an order, and so on. Time series data is ingested into the Experience Platform using a schema that has the class set to **Experience Event**.

### Captured time series data

See [behavioral events](events.md) and [back office events](events-backoffice.md) to learn what data is captured when a time series event is generated.

### Schema needed to ingest time series event data

Learn how to [create a schema](update-xdm.md) that can ingest behavioral and back office time series event data.

## Record data

Record data provides information about the attributes of a subject. A subject could be an organization or an individual. For example, a shopper on your site creates an account and that generates record data. This data is ingested into the Experience Platform using a schema that has the class set to **Individual Profile**. You can send that record data to Adobe's profile management and segmentation service: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### Captured profile record data

See [customer profile record data](events-profilerecord.md) to learn what data is captured when a profile record is generated.

### Schema needed to ingest profile record data

Learn how to [create a schema](profile-data.md) that can ingest profile record data.
