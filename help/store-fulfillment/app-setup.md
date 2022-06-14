---
title: App Setup
description: "Set up the [!DNL Store Assist] app to manage end-to-end store fulfillment workflows and processes for buy online, pick up in store orders." 
role: User, Admin
level: Intermediate

---
# App Setup

Store Assist is a fulfillment-as-a-service (FaaS) platform app powered by Walmart Commerce Technologies. The app provides in-store fulfillment capabilities to handle [!DNL buy online], [!DNL pick up in store] (BOPIS) orders.  

The app receives all order and customer information—from order details to pick up times-and makes the data available to store associates online, through mobile devices. With Store Assist, store associates can see which items customers ordered, pick the correct items faster, and set up fulfilled orders for in-store or curbside pickup delivery to customers. 

Store Associates use the Store Assist [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], and [!UICONTROL Orders] to complete the following manage the delivery and handoff process:

- Assign order delivery dates and times
- Get notifications from customers when they arrive at the store for order pickup
- Stage orders for handoff to customers
- Track order status for all orders in their assigned store locations

See [Store Assist fulfillment workflows](store-assist-modules.md) to learn more about the Store Assist app.


## Configure the Store Assist App

The Store Assist app requires two types of configuration:

- Adobe Commerce Admin configuration settings to [Manage user accounts, user roles, and resource permissions from the Adobe Commerce Admin system settings](user-setup.md).

- Frontend configuration settings to customize the Store Assist app interface and other settings including:

  - **Brand the Store Assist app**—Customize the app user interface with your company logo and colors

  - **Update the default instructions**—Customize the instructions that display in Store Assist interfaces for the Pick, Stage, Handoff, and Order modules so your associates know exactly what to do during each step of the fulfillment process.

  - **Localization**—Select available language for the app, choose your date and time format, select your default measurement units, select your default currency 

  - **Inactivity time**—Specify the amount of time that the app must be inactive before it logs out 

  - **Cancellation from the store**—Specify whether orders can be cancelled from the store and which roles have cancellation permissions 

  - **Order cleanup window**—Specify how long past the scheduled pickup time that a picked order remains in staging before being restocked—for example, three days. 

  - Customize all in app instructions (picking, staging, hand off) 

  - **Picking notifications**–Setup if you want to have push notifications to start picking once an order was placed 

  - **Check in notifications**–Setup if you want to have push notifications once a customer has checked in / is waiting for X mins / or no notifications at all 

  - **Hand off process**—Enable customer signature, enable a prompt to check customer ID before handing off the order

  - **Enable item rejection upon handoff**

  Work with the Walmart Commerce Technologies Client Services team to complete Frontend configuration for the Store Assist App.

## App download and installation

After the Store Assist app configuration has been completed, Store Associates can download and install the Store Assist app on their mobile devices and log in.

- Download the Store Assist app from the [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) or the Google Play store.

- Store Associates require the following information to log in:

  - The Company name associated with your Store Assist account

  - Store Assist account credentials—username and password credentials for their account. 

  An Adobe Commerce Administrator can create the Store Assist App user accounts for store locations that have [In-Store Pickup](merchant-store-configuration.md#pickup-location-configuration) enabled in the Admin Stores settings.
  
