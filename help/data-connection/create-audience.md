---
title: Create an audience in Real-Time CDP using [!DNL Commerce] event data
description: Learn how to use [!DNL Commerce] event data to create an audience in Real-Time CDP
role: Admin, Developer
feature: Personalization, Integration
---
# Create Audiences in Real-Time CDP using [!DNL Commerce] Event Data

You can use event data captured from your [!DNL Commerce] store to create audiences in Real-Time CDP. The data captured is based on browsing behavior, past purchases, profile attributes, propensities to convert or to churn, loyalty status, high and low customer value, and more.

In this article, you learn:

- The specific [!DNL Commerce] events used
- How to create an audience in Real-Time CDP based on the data the events collect
- How to activate that audience to your [!DNL Commerce] store
- How to use the audience in [!DNL Commerce] to inform a cart price rule

>[!IMPORTANT]
>
>As you go through the steps outlined in this article, make sure that you are using your [!DNL Commerce] sandbox environment. This ensures that the storefront and back office event data you send to Experience Platform does not dilute your production event data.

## What is an audience?

An audience is a set of customers that share similar behavior or characteristics. In this exercise, you will create an audience that qualifies people that are interested in a particular product from your store.

## Solutions

This solution uses the following applications:

- Adobe [!DNL Commerce]
- Real-Time CDP

### What have other customers achieved?

Adobe [!DNL Commerce] customers have achieved significant business impacts from activating audiences built in Real-Time and deploying them to their [!DNL Commerce] instance.

A global, multi-brand apparel retailer achieved:

- 1 source of truth, 10s of millions of unified customer profiles
- 40+ unique audiences of "high intent customers" to engage across channels

A global beverage company achieved:

- 98 million customer profiles from over 100 countries

## Prerequisites

Before you begin, ensure:

- You are provisioned to use Real-Time CDP. If you are not sure, check with your systems integrator or development team that manages projects and environments.
- You [installed](install.md) and [configured](connect-data.md) the [!DNL Data Connection] extension in [!DNL Commerce].
- You [confirmed](connect-data.md#confirm-that-event-data-is-collected) that your [!DNL Commerce] event data is arriving at the Experience Platform edge.

## Data types

When creating audiences in Real-Time CDP using data from your [!DNL Commerce] store, you typically use data from the following events:

|Event Type|Events Captured by Adobe Commerce|
|---|---|
|**Time-Series Event Data** - Includes data related to user interactions and behaviors on your website or mobile app.|[productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart)<br>[placeOrder](events.md#completecheckout)<br>[orderplaced](events-backoffice.md#orderplaced)<br>[orderLineItemRefunded](events-backoffice.md#orderlineitemrefunded)<br>[order Canceled](events-backoffice.md#ordercancelled)<br>[order history](connect-data.md#send-historical-order-data)|
|**Profile Data** - Refers to the attributes and characteristics of individuals. This can include information such as first name, last name, email address, age, gender, location, preferences, and any other relevant demographic or behavioral data that can help define and segment your audience.|[createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[Profile Record](events-profilerecord.md)|

Capturing and sending this data is handled for you when you [install](install.md) and [configure](connect-data.md) the [!DNL Data Connection] extension, so no additional steps are needed from you.

In the next section, you will use the data from the [productPageView](events.md#productpageview) event to build an audience in Real-Time CDP.

## 1. Create an audience

To simplify this exercise, you will only use event data from the [productPageView](events.md#productpageview) event. This event captures details about the product that was viewed, such as product name, SKU, price, and so on.

​You will use this event data to specify that the audience includes individuals who have at least one "Product Views" event where the SKU (product identifier) equals a specific product on your site and the event occurs within the last 1 day. ​

1. Open Experience Platform and select **[!UICONTROL Audiences]** from the left rail.

    ![Audience Dashboard](assets/audience-left-rail.png)

1. Click **[!UICONTROL Create Audience]**.

    ![Create Audience](assets/browse-create-audience.png)

    The **Segment Builder** workspace displays.

1. In the **Segment Builder** workspace, select the **Build rule** creation method.

    ![Build Rule](assets/build-rule.png)

    The **Segment Builder** workspace is where you define the rules and conditions for your audience.​ These rules and conditions are based on the event and profile data from your Commerce store and define the criteria that determine whether a user qualifies for the audience. For example, you might create a rule that includes users who have viewed a specific product or have made a purchase within a certain time frame. Learn more about [Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) and rules and conditions.
    
1. Select the [Events](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) tab.

    ![Events Tab](assets/audience-events-tab.png)

1. Search for the "Product Views" event type. Drag and drop it to the **Segment Builder** workspace.

1. Return to the **Events** tab and search for "SKU". Drag and drop it to the **Segment Builder** workspace on top of the **Product View** event. The **Event Rules** section appears where you can specify the specific product you want to build your audience off of.

    ![Select SKU](assets/audience-addsku.png)

1. Set the time internal to 1 day by clicking on **Any Time** and selecting *In last* with a value of *1*.

    When building an audience, you can specify a time interval to capture recent activity. Setting a time interval allows you to target users based on their recent interactions or behaviors within a specific timeframe.

1. In the right rail, set the audience properties by providing a name, description, and evaluation method for the audience.

1. To save the audience, click **[!UICONTROL Save and Close]**.

    The details of your audience appears.

## 2. Activate the audience to the [!DNL Commerce] destination

To make the audience available in [!DNL Commerce], you need to activate it to the [!DNL Commerce] destination.

>[!IMPORTANT]
>
>If you have not already set [!DNL Commerce] as an available destination to receive data, see the [Adobe [!DNL Commerce] Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) article.

1. In the **Details** tab of your audience, click **Activate to destination**.

1. Select your [!DNL Commerce] destination.

1. Click **Next**

1. Click **[!UICONTROL Finish]** to complete the activation process. 

## 3. View the audience in the Audiences Dashboard

In [!DNL Commerce], you can view all [active](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html) audiences that are available to personalize within your [!DNL Commerce] instance using the **Real-Time CDP Audiences** dashboard.

To access the **Real-Time CDP Audiences** dashboard, go to the _Admin_ sidebar, then go to **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

In the dashboard, look for the audience you created. Notice it is not being used in a cart price rule or dynamic block.

![Real-Time CDP Audiences Dashboard](assets/real-time-cdp-dashboard.png)

## 4. Create a cart price rule based on the audience

In this section, you create a cart price rule based on your new audience.

1. Confirm your new audience appears in the **Real-Time CDP Audiences** dashboard.
1. [Create a cart price rule](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Set the condition](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) of the cart price rule using your new audience.
1. [Set what action](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) you want to occur when the product is added to the cart.
1. Continue to configure your cart price rule.
1. Go to the customer view of your sandbox instance.
1. Add the product you based the audience off of to the cart. Notice the cart price rule is enabled.

## Wrap up

In this exercise, you created an audience in Real-Time CDP and activated it to the [!DNL Commerce] destination. You then created a cart price rule based on that audience and enabled the rule on your sandbox storefront when you added the product to your cart.
