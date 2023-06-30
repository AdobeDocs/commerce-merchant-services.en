---
title: Release Notes
description: The latest release information for Adobe Experience Platform connector from Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
---
# Release Notes

These release notes contain updates to the Experience Platform connector and includes:

* ![New](../assets/new.svg) - New features
* ![Fix](../assets/fix.svg) - Fixes and improvements
* ![Bug](../assets/bug.svg) - Known issues

For feature changes and fixes related to extensions used by the Experience Platform connector, see **Supported service updates**.

See [Upcoming Releases](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) to learn about release schedules and support.

See the developer documentation to [learn about product compatibility](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Supported service updates

These release notes describe feature changes and fixes related to extensions used by the Experience Platform connector.

+++Supported service updates

_June 10, 2023_

* ![Fix](../assets/fix.svg) - Fixed an issue when `orderId` was not passing in the context due to prefixes in the Commerce order identifier.
* ![Fix](../assets/fix.svg) - Updated Content Security Policy configurations.

_March 30, 2023_

* ![New](../assets/new.svg) - Added a new extension called `data-services-b2b` that includes [requisition list events](events.md#b2b-events) for B2B merchants.
* ![New](../assets/new.svg) - Added the `uniqueIdentifier` field to [search](events.md#search-events) events. This new field allows merchants to cross reference which search requests correspond to which search responses.

_October 12, 2022_

* ![New](../assets/new.svg) - Added two [storefront events](events.md): `openCart` and `removeFromCart` to the Adobe Commerce Storefront Events SDK and Collector.
* ![New](../assets/new.svg) - Added support for an [AEM storefront](overview.md#aem-support).

+++

## 2.3.0

_June 27, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - Added ability to [turn off sending storefront events](connect-data.md#data-collection) to the Experience Platform.
* ![Fix](../assets/fix.svg) - Updated Content Security Policy configurations.
* ![Fix](../assets/fix.svg) - Fixed support for back office events on Commerce 2.4.7 version.
* ![New](../assets/new.svg) - Added a notification message about cache invalidation when you save changes to the Experience Platform Connector form.


## 3.0.0-beta1 (internal only)

_June 13, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - (Beta) Added ability to [send historical order](connect-data.md#beta-send-historical-order-data) data and status to the Experience Platform. This feature is available for beta users only. You can join the beta by sending an email to the following address: [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

## 2.2.0

_March 30, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - Bundled the `commerce-data-export` and `saas-export` dependencies with the `experience-platform-connector` extension. Previously, you had to install these dependencies separately. These dependencies, along with merchant configuration, enables server side processing of [back office events](events.md#back-office-events).
* ![New](../assets/new.svg) - Added new back office event called [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_February 28, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - Added support for PHP 8.2 for all Experience Platform connector extensions.

## 2.1.0

_January 17, 2023_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - Updated the [Experience Platform connector Admin](connect-data.md) so you can specify your own AEP Web SDK (alloy).
* ![Fix](../assets/fix.svg) Changed to using `identityMap` instead of `personID` when setting the primary identity for any data pushed to the edge.

## 2.0.1

_November 10, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![Fixed issue](../assets/fix.svg) - Now the Adobe Experience Platform context is set only after the Storefront Event Collector and Storefront Event SDK are successfully loaded.

## 2.0.0

_October 12, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - Added ability to specify your own AEP Web SDK when [connecting](connect-data.md) your Adobe Commerce instance to the Experience Platform.
* ![Fix](../assets/fix.svg) - Updated datastream scope requirement so that datastream IDs must be scoped to the website rather than storeview.

## 1.0.0

_August 9, 2022_

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.3 and newer

* ![New](../assets/new.svg) - General availability release.
