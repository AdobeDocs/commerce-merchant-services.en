---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Release Notes'
description: "Review the release notes for information about all [!DNL Store Fulfillment by Walmart Commerce Technologies] releases."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
---
# Release Notes

These release notes describe the initial release of [!DNL Store Fulfillment Services by Walmart Commerce Technologies] and include:

![New](../assets/new.svg) New features
![Fixed issue](../assets/fix.svg) Fixes and improvements
![Known issue](../assets/bug.svg) Known issues

See [Upcoming Releases](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) to learn about release schedules and support.

See [Product Availability](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) to learn which Adobe Commerce versions support this extension.

## v1.6.0

*December 18, 2023*

This release contains the following updates:

![New](../assets/new.svg)<!-- WMTP-1000 --> Added configuration to modify password parameters.

![New](../assets/new.svg) Added a safeguard to prevents users from picking up and dispensing a quantity greater than the order.

![New](../assets/new.svg) Added configuration for Estimated Ship-to-store Lead Time.

![Fixed issue](../assets/fix.svg) Code quality improvements:

- <!-- WMTP-941--> Fixed an issue that flagged return statements by PHPStan.
- <!-- WMTP-944--> Added proper PHP docs to help with auto-completion.
- <!-- WMTP-943--> Fixed an issue for incorrect return types.
- <!-- WMTP-945--> Fixed an issue to correct classes.
- <!-- WMTP-905--> Fixed an issue to resolve missing or unknown classes.
- <!-- WMTP-939--> Fixed an issue that validated unsused property.
- <!-- WMTP-946--> Fixed an issue that verified if methods exists.
- <!-- WMTP-926--> Fixed an issue to resolve an exception that was thrown in the same function.
- <!-- WMTP-925--> Changed use of function parse_url().
- <!-- WMTP-925--> Removed direct use of $_SERVER Superglobal.
- <!-- WMTP-922--> Use context specific Exceptions.

![Fixed issue](../assets/fix.svg) Improved Security:

- <!-- WMTP-903--> Refactored code that defined some extension attributes on the quote address that was being injected using the resource model and database queries alteration.
- <!-- WMTP-970--> Use binding for select to prevent SQL injection.
- <!-- WMTP-969--> Remove direct database queries.

![Fixed issue](../assets/fix.svg) <!-- WMTP-906--> Improved performance for product view & login.

![Fixed issue](../assets/fix.svg) <!-- WMTP-976--> Modified the cancellation endpoint to process cancellation acknowledgement.

![Fixed issue](../assets/fix.svg) <!-- WMTP-971--> Fixed an issue where the value of the string for QR code for Two-Factor Authentication is twice encoded in base64.

![Fixed issue](../assets/fix.svg) <!-- WMTP-974--> Fixed an issue for creating cancellation in Magento when creating one click cancellation.

![Fixed issue](../assets/fix.svg) <!-- WMTP-975--> Fixed an issue for wrong email format for partial nil-pick.

![Fixed issue](../assets/fix.svg) <!-- WMTP-1004--> Fixed an issue that prevented creating an order from the admin.

![Fixed issue](../assets/fix.svg) <!-- WMTP-994--> Fixed an issue that for order line item extension attributes to be loaded correctly and correct picking process to occur.

![Fixed issue](../assets/fix.svg) <!-- WMTP-972--> Fixed an issue for source configuration screen to react for the global level configuration only.

![Fixed issue](../assets/fix.svg) <!-- WMTP-994--> Resolved MFTF test reports.

![Fixed issue](../assets/fix.svg) <!-- WMTP-999--> Fixed an issue for an error when switching storeviews.

![Fixed issue](../assets/fix.svg) <!-- WMTP-994--> Fixed an issue where order line item extension attributes are not getting loaded.

![Fixed issue](../assets/fix.svg) <!-- WMTP-983--> Fixed an issue that prevented customer to save and select preferred source.

![Fixed issue](../assets/fix.svg) <!-- WMTP-979--> Fixed an issue to set country dialing code as a set field in the source configuration form.

![Fixed issue](../assets/fix.svg) <!-- WMTP-952--> Fixed an issue to show alerts when a Ship-to-store product gets removed in the minicart.

![Fixed issue](../assets/fix.svg) <!-- WMTP-979--> Fixed an issue to correctly log admin connection test failures.

![Fixed issue](../assets/fix.svg) Fixed an issue for the order delayed email getting wrongfully sent out for every instore pickup order.

![Fixed issue](../assets/fix.svg) Fixed an issue that broke admin orders by the quote stock validator.

![Fixed issue](../assets/fix.svg) Fixed an issue where partial dispensation was sometimes wrongfully reporting emails as dispensed in full.

![Fixed issue](../assets/fix.svg) Improved emails for partially cancelled orders to use in-transit and ready-for-pickup order line items.

![Fixed issue](../assets/fix.svg) Displaying quantity in transit and ready for pickup on the customer order details page.

![Fixed issue](../assets/fix.svg) Improved notification history for orders that have been partially cancelled.

![Fixed issue](../assets/fix.svg) <!-- WMTP-1007--> Fixed an issue where multiple picking could result in incorrect quantities for order items.

- A credit memo refunding the customer will be automatically issued, with limitations:
-   Only for logged in users.
-   Store credit needs to be enabled with auto-credit turned on.
-   Only works for Adobe Commerce, no Magento Open Source support.
-   Otherwise, a warning will be issed in the admin and the order will put placed in Payment Review state, requiring manual intervention for refunding.

![Fixed issue](../assets/fix.svg) <!-- WMTP-1006--> Fixed an issue where extension is disabled, out of stock products can still be purchased.

![Fixed issue](../assets/fix.svg) Fixed an issue where nil-picked order items are still considered in transit and an Order Canceled email is not sent.

![Fixed issue](../assets/fix.svg) Fixed an issue where an order is canceled, that status at dispense is not changing but shows as “Ready for Pickup” in admin.

![Fixed issue](../assets/fix.svg) Fixed an issue where order sync failure was caused by a failed quantity check for child items.

![Fixed issue](../assets/fix.svg) <!-- WMTP-1012--> Fixed an issue to show alternate pick up person details.


## v1.5.0

*August 3, 2023*

[!BADGE Supported]{type=Informative tooltip="Supported"} [Adobe Commerce 2.4.4 to 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), including the 2.4.6-p1, 2.4.5-p3, and 2.4.4-p4 security patch releases

This release contains the following updates:

![New](../assets/fix.svg) Updated the extension to support [Adobe Commerce security patch releases](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3, and 2.4.4-p4.

![New](../assets/new.svg)<!-- WMTP-918 --> Added support for the [Asynchronous sending](sales-emails.md) configuration option for Sales Emails. Merchants that upgrade to version 1.5.0 have the option to send emails immediately (default) or asynchronously.

![New](../assets/new.svg)<!-- WMTP-916--> Updated the [Sources configuration](merchant-store-configuration.md) to support international phone number formats.

![New](../assets/new.svg) Added logic to prevent refund amounts from exceeding the remaining or invoiced amount.

![New](../assets/new.svg)<!-- WMTP-882 --> Replaced `google.map.LatLng` object with JSON literals to support compatibility with older versions of [!DNL Google Maps].

![Fixed issue](../assets/fix.svg)<!-- WMTP- --> Updated the script that creates the `[!DNL Available for Store Pickup]` and `[!DNL Available for Home Delivery]` product attributes to prevent attribute category conflict.

![Fixed issue](../assets/fix.svg)<!-- WMTP-915 --> Fixed a compatibility issue that caused an endless loop when loading and saving some entities.

![Fixed issue](../assets/fix.svg)<!-- WMTP-921 --> Fixed an issue that prevented [!DNL Ship to Store] quote validation from triggering when an item is added to the cart from a product detail page (PDP).

![Fixed issue](../assets/fix.svg)<!-- WMTP- 932 --> Fixed a checkout issue that allowed customers to select the home delivery method for items that are not eligible for home delivery.

![Fixed issue](../assets/fix.svg) Installation updates:

- <!-- WMTP-880--> Fixed an issue that caused an incorrect website code to be returned when installing the [!DNL Store Fulfillment] extension.

- <!-- WMTP-878--> Fixed an issue for SKU integers that required the data type to be casted to string type during installation.

![Fixed issue](../assets/fix.svg)<!-- WMTP-915--> Fixed a failure caused by a missing Check-in error code.

![Fixed issue](../assets/fix.svg)<!-- WMTP-932 --> Fixed a bug related to partial reject during dispense operations.

![New](../assets/new.svg)<!-- WMTP-953 --> Updated the Cancel API endpoint to consume the status parameter as an optional object.

![New](../assets/new.svg)<!-- WMTP-960 --> Improved logging details for the Dispense API endpoint.

## v1.4.0

*April 13, 2023*

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 - 2.4.6

![New](../assets/fix.svg) [!DNL Store Fulfillment] is now [compatible with [!DNL Adobe Commerce] 2.4.4 to 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*February 27, 2023*

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 - 2.4.5

This release contains the following update:

![New](../assets/fix.svg)<!-- WMTP-795 --> Added the capability to disable the Store Fulfillment solution for a specific site by changing the default scope for the System Configuration setting from website to global.

## v1.2.0

*September 27, 2022*

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 - 2.4.5

This release contains the following update:

![New](../assets/fix.svg) [!DNL Store Fulfillment] is now [compatible with [!DNL Adobe Commerce] 2.4.4 to 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*July 15, 2022*

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 - 2.4.4

Stability: General Availability

![New](../assets/fix.svg)<!-- WMTP-731 --> Simplified the [Check-in experience configuration](check-in-experience-setup.md) for the Store Assist app by adding default car make and model selections. In the previous version, merchants had to manually configure the car make and model selections.

## v1.0.0

*March 4, 2022*

[!BADGE Supported]{type=Informative tooltip="Supported"} Adobe Commerce versions 2.4.4 - 2.4.4

Stability: General Availability

## Store Assist app

For information about new releases of the Store Assist app, see the app information in the [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
