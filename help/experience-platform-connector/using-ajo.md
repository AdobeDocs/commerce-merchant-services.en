---
title: Use Adobe Journey Optimizer to Send an Abandoned Cart Email
description: Learn how to use Adobe Journey Optimizer to send an abandoned cart email.

---
# Use Adobe Journey Optimizer to Send an Abandoned Cart Email

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) helps you personalize the commerce experience for your shoppers. For example, you can use Journey Optimizer to create and deliver scheduled marketing campaigns, such as weekly promotions for a retail store; or, you can generate an abandoned cart email if a customer added a product to a cart but then did not complete the checkout process.

In this tutorial, you will learn how to listen to a `checkout` event generated from your Commerce instance and respond to that event in Journey Optimizer to build an abandoned cart email.

>[!IMPORTANT]
>
>For demonstration purposes, make sure you are using your Commerce sandbox environment as you go through this tutorial. This ensures that the storefront and back office event data you send to Experience Platform does not dilute your production event data.

## Prerequisits

Before you begin working on this tutorial, you must ensure the following:

- You are provisioned to use Adobe Journey Optimizer
- You have [configured](connect-data.md) the Experience Platform Connector
- You have [confirmed](connect-data.md#confirm-that-event-data-is-collected) your Commerce event data is arriving at the Experience Platform edge

### Step 1: Create a user in your Commerce sandbox environment

You need to create a user in your test environment and confirm that user account information appears in Experience Platform. Make sure the email you specified is valid as that is used later in this tutorial to send the abandoned cart email.

1. Sign in or create an account in your test environment.

    With the Experience Platform Connector installed and configured, this account information is sent to the Experience Platform as a profile.

    ![Sign in to your test account](assets/check-event-profile.png)

1. Confirm your user account information in the Profile section of Experience Platform.
1. Confirm the checkout event appears in the Experience Platform unified profile

Go to Profiles in the Adobe Experience Platform. Click on Detail in the profile. You will now see the profile that you created. 


With the Experience Platform Connector configured, storefront and back office event data from your Commerce site are already being sent to the Experience Platform. Go to Profiles in the Adobe Experience Platform. Click on Detail in the profile. You will now see the profile that you created. 

    1. 


### Step 2: Create an abandoned cart email in Journey Optimizer

Before we begin creating an abandoned cart email, you will need to add items to the cart.

1. Open your Commerce test environment.
1. Add a product to the cart.

    This action triggered the `addToCart` event. However, because you did not initiate a checkout, your cart is essentially abandoned.

1. Confirm the events are flowing to Journey Optimizer.

    1. Launch Adobe Journey Optimizer.
    1. Select **Profiles**.
    1. Set [!UICONTROL Identity namespace] to `Email`.
    1. Set [!UICONTROL Identity value] to your email address.

    For example:

    ![Details in Journey Optimizer](assets/check-event-profile.png)

    Under your profile, you can see the list of events with the details by clicking on the **Events** tab.





















Let's focus on the following checkout event:

`commerce.checkout`

## Configure a Checkout Event in Journey  

In this exercise, we will configure journeys so that it can listen to the right checkout events in real-time. 

Log into Adobe Jouney Optimizer 

Click on Configurations under the administration section of the left menu. 

Then click on Manage Events.

You will see the list of already available events that journeys can listen to. We have pre-created some events for you like the order event. But in this exercise, we will create a new event for Checkout 

Click on Create Event 

You can now setup your event through the right rail as following: 

    Name: set the name by prefixing it with your name: firstname_lastname_Checkout_Event 

    Type: Leave to Unitary event (= one per profile) 

    Event ID type: Leave it to Rule based (= filter down events to be listed to thanks to a rule) 

    Schema: Select the schema named CitiSignal - Commerce EE v.1 

Fields: you need to select the fields that are useful for this event.   

    Select all fields under Product List Items except _experience 

    Select all fields under Commerce and eventType 

    Select all fields under Web 

    Click on OK 

Event ID condition: Click on the Edit button next to the condition and create a condition eventType is commerce.checkouts AND personID = XXXX where XXXX = your ECID 

    To do so, you can: 

    drag and drop the eventType from the left rail and set it to commerce.checkout 

    drag and drop the person ID and paste your ECID (see below how to get that).

## Build a simple Checkout Journey  

Go to Journeys from the left menu and click on Create Journey 
Set the name of your journey by prefixing it with your firstname_lastname checkout journey and click ok.  
In the left rail under section EVENTS, Search for the Event you have previously created firstname_lastname_checkout_event and drag and drop it.  

Note: double clicking on the event will automatically add it to the canvas. 

Search for Event CitiSignal_OrderEvent and add it. 

Set the timeout branch to 1 min. This means that a website visitor doing a checkout and not doing an order within 1 minute will land in this timeout branch. In real life this can be set to a longer period like 24hours. 

In the left rail, Go to section ACTIONS and add the "Email action in the timeout branch. 
Your journey should look like this now 

Build a Checkout  abandonment email 

 

You can now click on the Email action 

set a name for the action Checkout abandonment email 

Choose a category Transactional 

Choose an email surface Transactionals that will select the branding settings to be used 

 

 

 

 

Click on Edit content 

 

Set the email subject line:  for example: Are you still interested? 

 

Click on Open Email Designer or Edit Email body  

 

 

 

 

Click on tab Saved templates and select the Checkout Abandonment Template 

 

We have prepared the email template for you. 

 

 

 

You can preview the template before selecting it with Use this template 

 

 

You are now in the email editor and we are going to add personalization to this email content. 

 

 

 

First let's add the first name to the email.  

You can select the following block and click on the personalization icon  

Une image contenant texte, capture d'écran, moniteur, intérieur

Description générée automatiquement 

 

Search for "first name" and click on the + icon to add it and click on Save 

Une image contenant texte

Description générée automatiquement 

 

Your content should look like this now. 

 

 

 

We are now going to set the list of products in the abandoned cart. This section is more advanced. We have pre-created the personalization for you as part of the template you have selected.  

let's select the following block and click on the code icon 

Une image contenant texte

Description générée automatiquement 

 

We can see here the HTML of that block with dynamic personalization that is included. In our case, we need to modify the event ID that is highlighted below. This is because you will be using personalization information coming from your own event created in exercise 5.2. 

 

 

 

 

Note: if you are trying to save the content without changing the event ID, you will get an error 

 

 

 

 

To get your event id, do the following: 

Go to Contextual attributes in the left rail  

Browse through Journey Orchestration > Events > firstname_lastname_checkout event> productListItems 

You will now see the product attributes. Add the Name by clicking on the + icon 

This inserts a personalization token that has the right Event ID 

Now copy and replace that id into the #each. You can now delete the the token added in previous step. 

Une image contenant texte

Description générée automatiquement 


You can click on Save. Your email is now ready 

Note for advanced users: 

This personalization editor allows you to tailor your content and make it very dynamic. 

You have access to all of the checkout event data 

You can use any profile attributes 

You can do conditional content based on a segment or a rule 

You can access Helper functions that allow to do date formatting, string operations, math, loops… 


Exercise 4.3 – Test your journey in real-time 

 

You are now ready to test this journey. Enable test mode.  

Next to it, you can see an icon that will be orange if you have warnings or red if you have errors. In the latter case, test option will be greyed out. You have to fix the error first. You can learn more by clicking on that icon. 

 

 

 

Now let's test this journey in real-time. Open another browser tab and Go to the CitiSignal website . 

 

Add a product to your cart  

 

Une image contenant texte

Description générée automatiquement 

 

Go to the checkout 

 

Une image contenant texte

Description générée automatiquement 

From the checkout page, you can now abandon. This means you can go back to the main page or close your tab. 

Une image contenant table

Description générée automatiquement 

 

The journey will now be triggered. You can check that by going to your browser tab where you have your journey. 

You should see a green arrow showing where your user went through. 

Now check your inbox. You should have received an email. 

 

 