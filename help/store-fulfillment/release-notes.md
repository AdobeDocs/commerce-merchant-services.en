---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Release Notes'
description: "Review the release notes for information about all [!DNL Store Fulfillment by Walmart Commerce Technologies] releases."
role: Admin, User, Leader, Developer
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
---
# Release Notes

These release notes describe the initial release of [!DNL Store Fulfillment Services by Walmart Commerce Technologies] and include:

![New](../assets/new.svg) New features
![Fixed issue](../assets/fix.svg) Fixes and improvements
![Known issue](../assets/bug.svg) Known issues

## v1.5.0

*August [Add date], 2023*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Compatible with [released versions of Adobe Commerce 2.4.4 - 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/versions.html).

This release contains the following updates:

![New](../assets/fix.svg)  [!DNL Store Fulfillment] is now [compatible with Adobe Commerce 2.4.0 to 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), including the 2.4.6-p1, 2.4.5-p3, and 2.4.4-p4 security patch releases.

![New](../assets/new.svg)<!-- WMTP-918 --> Added support for the [Asynchronous sending](sales-emails.md) configuration option for Sales Emails. Merchants that upgrade to version 1.5.0 have the option to send emails immediately (default) or asynchronously.

![New](../assets/new.svg)<!-- WMTP-916--> Updated the [Sources configuration](merchant-store-configuration.md) to support international phone number formats.

![New](../assets/new.svg) Added logic to prevent refund amounts from exceeding the remaining or invoiced amount.

![New](../assets/new.svg)<!-- WMTP-882 --> Replaced `google.map.LatLng` object with JSON literals to support compatibility with older versions of Google Maps.

![Fixed issue](../assets/fix.svg)<!-- WMTP- --> Updated the script that creates the `[!DNL Available for Store Pickup]` and `[!DNL Available for Home Delivery]` product attributes to prevent attribute category conflict.

![Fixed issue](../assets/fix.svg)<!-- WMTP-915 --> Fixed a compatibility issue that caused an endless loop when loading and saving some entities.

![Fixed issue](../assets/fix.svg)<!-- WMTP-921 --> Fixed an issue that prevented [!DNL Ship to Store] quote validation from triggering when an item is added to the cart from a product detail page (PDP).

![Fixed issue](../assets/fix.svg)<!-- WMTP- 932 --> Fixed a checkout issue that allowed customers to select the home delivery method for items that are not eligible for home delivery.

![Fixed issue](../assets/fix.svg) Installation updates

- <!-- WMTP-880--> Fixed an issue that caused an incorrect website code to be returned when installing the Store Fulfillment extension.

- <!-- WMTP-878--> Fixed an issue for SKU integers that required the data type to be casted to string type during installation.

![Fixed issue](../assets/fix.svg)<!-- WMTP-915--> Fixed a failure caused by a missing Check-in error code.

![Fixed issue](../assets/fix.svg)<!-- WMTP-932 --> Fixed a bug related to partial reject during dispense operations.

![New](../assets/new.svg)<!-- WMTP-953 --> Updated the Cancel API endpoint to consume the status parameter as an optional object.

![New](../assets/new.svg)<!-- WMTP-960 --> Improved logging details for the Dispense API endpoint.

## v1.4.0

*April 13, 2023*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 - 2.4.6

![New](../assets/fix.svg) [!DNL Store Fulfillment] is now [compatible with [!DNL Adobe Commerce] 2.4.4 to 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*February 27, 2023*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 - 2.4.5

This release contains the following update:

![New](../assets/fix.svg)<!-- WMTP-795 --> Added the capability to disable the Store Fulfillment solution for a specific site by changing the default scope for the System Configuration setting from website to global.

## v1.2.0

*September 27, 2022*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 - 2.4.5

This release contains the following update:

![New](../assets/fix.svg) [!DNL Store Fulfillment] is now [compatible with [!DNL Adobe Commerce] 2.4.4 to 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*July 15, 2022*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 - 2.4.4

Stability: General Availability

![New](../assets/new.svg)<!-- WMTP-731 --> Simplified the [Check-in experience configuration](check-in-experience-setup.md) for the Store Assist app by adding default car make and model selections. In the previous version, merchants had to manually configure the car make and model selections.

## v1.0.0

*March 4, 2022*

[!BADGE Compatibility]{type=Informative tooltip="Compatibility"} Adobe Commerce versions 2.4.4 - 2.4.4

Stability: General Availability

## Store Assist app

For information about new releases of the Store Assist app, see the app information in the [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
