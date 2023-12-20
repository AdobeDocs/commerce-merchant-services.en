---
title: Guide Overview
description: Learn how to integrate Adobe Commerce data with Adobe Experience Platform using the [!DNL Data Connection] extension.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
---
# [!DNL Data Connection] Introduction

>[!IMPORTANT]
>
>The Experience Platform connector has been renamed to [!DNL Data Connection].

The [!DNL Data Connection] extension connects your Adobe Commerce instance to the Adobe Experience Platform edge.

Your Commerce store contains a wealth of data. Information about how your shoppers browse, view, and ultimately purchase the products on your site can reveal opportunities to create a more personalized shopping experience. While that data can inform native Commerce features such as cart price rules and dynamic blocks, the data remains siloed in your Commerce instance. 

The Adobe Experience Platform provides a suite of technologies, that when hydrated with data from your Commerce store, can distribute that data through the edge network to other Adobe DX products to unlock insights into your shopper's buying behavior. With these deep insights, you can create a more personalized shopping experience across all channels.

The following image shows how your Commerce data flows from your store to other Adobe DX products:

![How data flows to the Experience Platform edge](assets/commerce-edge.png)

In the above image, your storefront and back office data is sent to the Experience Platform edge using an SDK, API, and a source connector. You do not need to fully understand how those pieces work as the extension handles the data sharing complexity for you. When the event data is at the edge, you can pull that data into other Experience Platform applications. For example:

|Application|Purpose|
|---|---|
|Adobe [!DNL Real-Time CDP]| Profile management and segmentation service|
|Customer [!DNL Journey Analytics]|Deep analysis of the full Commerce journey|
|Adobe [!DNL Analytics]|Deep analysis of customer behavior and campaign performance|
|Adobe [!DNL Journey Optimizer]|Campaign orchestration across channels|
|Adobe [!DNL Target]|A/B and Multivariate Testing and experience personalization|

## Pull Experience Platform data back into Commerce

Sending your Commerce data to the Experience Platform using the [!DNL Data Connection] extension is one side of Commerce's data sharing capabilities. The other side, which is an optional extension, is called [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). This extension allows you to build audiences in Real-Time CDP and deploy those audiences to your Commerce store to inform cart price rules and dynamic blocks.

At a high level, the flow of data from your Commerce store to the Experience Platform and back through the Audience Activation extension looks like the following:

![[!DNL Data Connection] flow](assets/data-connection.png)

After you set up the connection between Commerce to Experience Platform and Experience Platform to Commerce, the data continues to flow. You do not need to reconnect, unless required to do so by an upgrade.

## Concepts

Sharing data between these two systems requires that you understand several concepts. This guide ties together those concepts so you can build a robust data sharing system to achieve your personalization goals.

To understand the pieces involved in connecting your Commerce store to the Experience Platform, there are a few concepts to learn.

* **Data** - The data that gets shared with the Experience Platform is data collected from browser events on your storefront, and back office events on the server. Storefront events are captured from shoppers' interactions on the site and include events such as [addToCart](events.md#addtocart), [pageView](events.md#pageview), [createAccount](events.md#createaccount), [editAccount](events.md#editaccount), [startCheckout](events.md#startcheckout), [completeCheckout](events.md#completecheckout), [signIn](events.md#signin), [signOut](events.md#signout), and so on. See [storefront events](events.md#storefront-events) for the full list of storefront events. Server-side, or back office events, include [order status](events.md#back-office-events) information, such as [orderPlaced](events.md#orderplaced), [orderReturned](events.md#orderitemreturncompleted), [orderShipped](events.md#ordershipmentcompleted), [orderCancelled](events.md#ordercancelled), and so on. See [back office events](events.md#back-office-events) for the full list of back office events.

* **Experience Platform and edge network** - The Experience Platform is the data warehouse for most Adobe DX products. Data sent to the Experience Platform is then propagated to the Adobe DX products through the Experience Platform edge network. For example, you can launch Journey Optimizer and retrieve your specific Commerce event data from the edge and build an abandoned cart email in Journey Optimizer. Journey Optimizer can then send that email if there are any abandoned carts in your Commerce store.

* **Schema** - The schema is what describes the structure of the data that is being sent. Before Experience Platform can ingest your Commerce data, you must compose a schema to describe the data's structure and provide constraints to the type of data that can be contained within each field. Schemas consist of a base class and zero or more schema field groups. The schema uses the XDM structure, which all Adobe DX products can read. So when you send your data to the Experience Platform you can be sure that your data is understood across all DX products. Learn more about [schemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Dataset** - A dataset is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store. All data that is successfully ingested into Adobe Experience Platform is contained within datasets. Learn more about [datasets](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - A datastream represents the server-side configuration when implementing the Adobe Experience Platform Web and Mobile SDKs. While the configure command in the SDK controls things that must be handled on the client (such as the edgeDomain), datastreams handle all other configurations for the SDK. When a request is sent to the Adobe Experience Platform Edge Network, the edgeConfigId is used to reference the datastream. This allows you to update the server-side configuration without having to make code changes on your website. Learn more about [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

* **Supported architecture** - The [!DNL Data Connection] extension is available on the following storefronts:

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## Prerequisites

To use the [!DNL Data Connection] extension, you must have the following:

* Adobe Commerce 2.4.4 or higher.
* Adobe ID and Organization ID.
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). The ACDL is required to collect storefront event data.
* Entitlements to other Adobe DX products.

<!-->
What about B2B
Data Connection provides the following event data:
- Create Requisition
- Quote Accepted
- And so on...



I think some options would be to link or define certain terms that the user might need to understand like:  Adobe Experience Platform edge as well as a link to the marketplace where the connector is.

So I think the thing that I always struggle with is that for someone that is new to the concept, it doesn't always connect the dots.   What I like to get to with the documentation is

What does Commerce have
where is it
how do I get it out
where does it go
what happens to it there
how do I use it

In this sense, commerce has valuable data, I presume it's in specific parts of commerce, or specific tables

I need to do a simple implementation of the data connector (how to), is adobe is going to maintain this for me, do I need to keep it up to date

It extracts commerce data and sends it to Edge network, where it can just pass automatically to other Adobe products (?), or it needs to be transformed (?), or it's already in "this schema" that is used between all products, so no effort necessary, other products can then just grab that data and ingest it and it will live at the edge(?), or in that new product(?) and a sample use case might be X.

Also, we say no PII, but what's the point then, I thought there was some aspect of Jim is interested in this category of products, he's clicked on these 19 items in the past 30 days, he bought X, we should segment him as a Car Junkie and include him in the 'Grand Prix' campaign (edited) 

I imagine you have specific parameters on how/what you write - but to me breaking it down to layman's terms and being more comprehensive would help the non-technical audience (who are our buyers and influencers).   Some of the stuff I mentioned I think could be links so if I need to understand it, I can open that, and if I don't I just keep reading.
-->


## Onboarding steps

At a high level, enabling the [!DNL Data Connection] extension involves the following steps: 

1. [Install](install.md) the [!DNL Data Connection] extension.
1. [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account and [view to confirm](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) your organization ID. The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) `@AdobeOrg`.
1. [Create or update](update-xdm.md) your XDM schema with Commerce-specific field groups.
1. [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated. This dataset contains the Commerce data that you send.
1. [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups.
1. [Connect to Commerce Services](../landing/saas.md).
1. [Connect to Adobe Experience Platform](connect-data.md).

The remainder of this guide walks you through all of these steps in more detail so you can get to up to speed and begin using the power of Adobe DX products in your Commerce store.

## Audience

This guide is designed for the Adobe Commerce merchant who wants to enrich and personalize their Commerce store so enhance the shopping experience for their customers.

## Support

If you need information or have questions that are not covered in this guide, use the following resources:

* [Help center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [Support tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}---Submit a ticket to receive additional help.
