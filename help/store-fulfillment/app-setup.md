---
title: App Setup
description: Set up the [!DNL Store Assist] app to manage end-to-end store fulfillment workflows and processes for buy online, pick up in store orders.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
---
# App Setup

Store Assist is a fulfillment-as-a-service (FaaS) platform app powered by Walmart Commerce Technologies. The app provides in-store fulfillment capabilities to handle [!DNL buy online], [!DNL pick up in store] (BOPIS) orders.  With Store Assist, store associates can see which items customers ordered, pick the correct items faster, and set up fulfilled orders for in-store or curbside pickup delivery to customers. 

The Store Assist app receives all order and customer information—from order details to pick up times-and makes the data available to store associates online, through mobile devices. The app includes [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], and [!UICONTROL Orders] modules to help Store Associates with fulfillment activities like the following:

- Assign order delivery dates and times.
- Receive notifications from customers when they arrive for order pickup.
- Stage orders for handoff to customers.
- Track order status for all orders in their assigned store locations.

>[!NOTE]
>
>See [Store Assist fulfillment workflows](store-assist-modules.md) to learn more about the Store Assist app.

## Configure the Store Assist App

The Store Assist app requires two types of configuration:

- Adobe Commerce Admin configuration settings to [manage user accounts, user roles, and resource permissions from the Adobe Commerce Admin system settings](user-setup.md).

- Frontend configuration settings to customize the Store Assist app interface and other settings including:

  - **Brand the Store Assist app**—Customize the app user interface with your company logo and colors.

  - **Update the default instructions**—Customize the instructions in the Store Assist interfaces for the Pick, Stage, Handoff, and Order modules to comply with your company policies and procedures, and guide Store Associates through each step of the fulfillment workflow.

  - **Localization**—Select the available language for the app. Choose your date and time format, and select your default measurement units and default currency.

  - **Inactivity time**—Specify the amount of time that the app must be inactive before it logs out.

  - **Cancellation from the store**—Specify whether orders can be cancelled from the store and which roles have cancellation permissions 

  - **Order cleanup window**—Specify how long past the scheduled pickup time that a picked order remains in staging before being restocked—for example, three days. 

  - Customize all in app instructions (picking, staging, hand off).

  - **Picking notifications**–Specify whether to send a push notification to start the picking process after a customer places an order.

  - **Check in notifications**–Specify whether to send a push notification during the check-in process for order pickups- after check-in, after customer wait time exceeds a specified time period. Or, disable notification.

  - **Hand off process**—Enable optional processes when Store Associate delivers order to customer, for example require a customer signature or prompt the associate to check customer ID.

  - **Enable item rejection upon handoff**–Allow customers to return or cancel order items during order handoff.

  Work with the Walmart Commerce Technologies Client Services team to complete frontend configuration for the Store Assist App.

## App download and installation

After the Store Assist app configuration has been completed, Store Associates can download, install, and log in to the Store Assist app from their mobile devices.

- Download the Store Assist app from the [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) or the Google Play store.

- Store Associates require the following information to log in:

  - The company name associated with your Store Assist account

  - Store Assist account credentials—username and password credentials for their account. 

  An Adobe Commerce Administrator can create user account and set permissions for theStore Assist App user accounts for store locations that have [In-Store Pickup](merchant-store-configuration.md#pickup-location-configuration) enabled in the Admin Stores settings.
