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

See [Upcoming Releases](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) to learn about release schedules and support.

See [Availability](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) to learn about product compatibility.

## Supported service updates

These release notes describe feature changes and fixes related to extensions used by the Experience Platform connector.

+++Supported service updates

_October 12, 2022_

* ![New](../assets/new.svg) - Added two [storefront events](events.md): `openCart` and `removeFromCart` to the Adobe Commerce Storefront Events SDK and Collector
* ![New](../assets/new.svg) - Added support for an [AEM storefront](overview.md#aem-support)

+++

## 2.1.0

_January 17, 2023_

* ![New](../assets/new.svg) - Updated the [Experience Platform connector Admin](connect-data.md) so you can specify your own AEB Web SDK (alloy). Also, added an option for beta merchants to send [back office event data](connect-data.md#data-collection) to the edge. These events contain [order status information](events.md#beta-order-status-events) about an order, such as if an order was placed, cancelled, refunded, or shipped. If you would like to participate in the back office beta program, contact [drios@adobe.com](mailto:drios@adobe.com).
* ![Fix](../assets/fix.svg) Changed to using `identityMap` instead of `personID` when setting the primary identity for any data pushed to the edge

## 2.0.1

_November 10, 2022_

* ![Fixed issue](../assets/fix.svg) - Now the Adobe Experience Platform context is set only after the Storefront Event Collector and Storefront Event SDK are successfully loaded.

## 2.0.0

_October 12, 2022_

* ![New](../assets/new.svg) - Added ability to specify your own AEP Web SDK when [connecting](connect-data.md) your Adobe Commerce instance to the Experience Platform
* ![Fix](../assets/fix.svg) - Updated datastream scope requirement so that datastream IDs must be scoped to the website rather than storeview

## 1.0.0

_August 9, 2022_

* ![New](../assets/new.svg) - General availability release

## Documentation

To learn more:

* [Adobe Commerce Developer Documentation](https://devdocs.magento.com/)
* [Adobe Commerce User Guide](https://docs.magento.com/user-guide/)
