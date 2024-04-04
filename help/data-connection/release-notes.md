---
title: Release Notes
description: The latest release information for the [!DNL Data Connection] extension from Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
---
# Release Notes

>[!IMPORTANT]
>
>The Experience Platform connector has been renamed to [!DNL Data Connection].

These release notes contain updates to the [!DNL Data Connection] extension and includes:

![New](../assets/new.svg) - New features
![Fix](../assets/fix.svg) - Fixes and improvements
![Bug](../assets/bug.svg) - Known issues

For feature changes and fixes related to extensions used by the [!DNL Data Connection] extension, see **Supported service updates**.

See [Upcoming Releases](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) to learn about release schedules and support.

See the developer documentation to [learn which Commerce versions support this module](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Supported service updates

These release notes describe feature changes and fixes related to extensions used by the [!DNL Data Connection] extension.

+++Supported service updates

_January 24, 2024_

![New](../assets/new.svg) - Updated the `data-services-b2b` extension to include a new requisition event called [deleteRequisitionList](events.md#deleterequisitionlist) for B2B merchants.

_November 16, 2023_

![Fix](../assets/fix.svg) - Fixed an issue where an error message incorrectly appeared when you placed an order that had multiple shipping addresses.
![Fix](../assets/fix.svg) - Fixed an issue in the [productPageView](events.md#productpageview) event where the `productListItems.priceTotal` event field was not converting the price after switching the currency on the store view.
![Fix](../assets/fix.svg) - Fixed an issue in the `productListItems` event field where the currency code was not updating when the merchant switched the store view.

_October 10, 2023_

![New](../assets/new.svg) - Added new order status events: [Order Invoiced](events-backoffice.md#orderinvoiced), [Order Item Return Initiated](events-backoffice.md#orderitemsreturninitiated), and [Order Item Return Completed](events-backoffice.md#orderitemreturncompleted).
![Fix](../assets/fix.svg) - Fixed an issue where currency configuration changes were not reflected in the events after refreshing the cache.
![Fix](../assets/fix.svg) - Fixed error when order confirmation message does not appear if asynchronous order placement is enabled.
![New](../assets/new.svg) - Added data to [addToRequisitionList](events.md#addtorequisitionlist) event for simple products on the Category view page.
![Fix](../assets/fix.svg) - Fixed an issue in the `selectedOptions` data in the [addToRequisitionList](events.md#addtorequisitionlist) event when products are added from the Order confirmation page.
![New](../assets/new.svg) - Added product data to [addToRequisitionList](events.md#addtorequisitionlist) event when products are added to the requisition list from the Category view page.
![New](../assets/new.svg) - Added [addToRequisitionList](events.md#addtorequisitionlist) event when configurable products are added to the requisition list from the Product view page.
![New](../assets/new.svg) - Added [addToRequisitionList](events.md#addtorequisitionlist) and [removeFromRequisitionList](events.md#removefromrequisitionlist) events when product quantity is increased and/or decreased from a requisition list.

_June 10, 2023_

![Fix](../assets/fix.svg) - Fixed an issue when `orderId` did not pass in the context due to prefixes in the Commerce order identifier.
![Fix](../assets/fix.svg) - Updated Content Security Policy configurations.

_March 30, 2023_

![New](../assets/new.svg) - Added an extension called `data-services-b2b` that includes [requisition list events](events.md#b2b-events) for B2B merchants.
![New](../assets/new.svg) - Added the `uniqueIdentifier` field to [search](events.md#search-events) events. This new field allows merchants to cross-reference search requests and search responses.

_October 12, 2022_

![New](../assets/new.svg) - Added two [storefront events](events.md), `openCart` and `removeFromCart`, to the Adobe Commerce Storefront Events SDK and Collector.
![New](../assets/new.svg) - Added support for an [AEM storefront](overview.md#aem-support).

+++

## 3.1.1

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

_April 9, 2024_

![New](../assets/new.svg) - Added support for PHP 8.3 for all [!DNL Data Connection] extensions.
![New](../assets/new.svg) - Added article about how to [integrate](mobile-sdk-epc.md) the Adobe Experience Platform Mobile SDK with Commerce.

## 3.2.0-beta2

_March 4, 2024_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) - If you are participating in the beta, make sure your `composer.json` file has the following on the root level: ` "minimum-stability": "beta"`.
![New](../assets/new.svg) - Added ability to [add custom attributes](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![New](../assets/new.svg) - Added ability to [collect and send profile records](connect-data.md#send-customer-profile-data) and data to Experience Platform.

## 3.1.0

_November 16, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

![New](../assets/new.svg) - The Experience Platform connector has been renamed to [!DNL Data Connection].
![Fix](../assets/new.svg) - Added ability to log error response if Adobe IMS cannot generate the access token.
![Fix](../assets/new.svg) - Added a notification message if you attempt to sync Historical Orders but have not specified account credentials.

## 3.0.0

_October 10, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 and newer

This is a major version release. [Edit](install.md#update-the-data-connection) your project's root composer.json file.

![New](../assets/new.svg) - General availability to [send historical order](connect-data.md#send-historical-order-data) data and status to the Experience Platform.
![New](../assets/new.svg) - Added support for OAuth 2.0 when you [configure](connect-data.md#connect-commerce-data-to-adobe-experience-platform) the [!DNL Data Connection] extension.
![New](../assets/new.svg) - Ended support for Adobe Commerce 2.4.3.

## 2.3.0

_June 27, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - Added ability to [turn off sending storefront events](connect-data.md#data-collection) to the Experience Platform.
![Fix](../assets/fix.svg) - Updated Content Security Policy configurations.
![Fix](../assets/fix.svg) - Fixed support for back office events on Commerce 2.4.7 version.
![New](../assets/new.svg) - Added a notification message about cache invalidation when you save changes to the [!DNL Data Connection] extension form.


## 3.0.0-beta1 (internal only)

_June 13, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - (Beta) Added ability to [send historical order](connect-data.md#beta-send-historical-order-data) data and status to the Experience Platform.

## 2.2.0

_March 30, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - Bundled the `commerce-data-export` and `saas-export` dependencies with the `experience-platform-connector` extension. Previously, you had to install these dependencies separately. These dependencies, along with merchant configuration, enables server-side processing of [back office events](events-backoffice.md).
![New](../assets/new.svg) - Added new back office event called [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_February 28, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - Added support for PHP 8.2 for all [!DNL Data Connection] extensions.

## 2.1.0

_January 17, 2023_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - Updated the [[!DNL Data Connection] extension Admin](connect-data.md) so you can specify your own AEP Web SDK (alloy).
![Fix](../assets/fix.svg) Changed to using `identityMap` instead of `personID` when setting the primary identity for any data pushed to the edge.

## 2.0.1

_November 10, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![Fix](../assets/fix.svg) - Now the Adobe Experience Platform context is set only after the Storefront Event Collector and Storefront Event SDK are successfully loaded.

## 2.0.0

_October 12, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - Added ability to specify your own AEP Web SDK when [connecting](connect-data.md) your Adobe Commerce instance to the Experience Platform.
![Fix](../assets/fix.svg) - Updated datastream scope requirement so that datastream IDs must be scoped to the website rather than storeview.

## 1.0.0

_August 9, 2022_

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.3 and newer

![New](../assets/new.svg) - General availability release.
