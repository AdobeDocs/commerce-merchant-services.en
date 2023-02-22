---
title: "Commerce Configurations Settings and [!DNL Live Search] "
description: "Describes the Adobe Commerce configuration settings that [!DNL Live Search] can read."
---
# [!DNL Live Search] and Adobe Commerce Configuration Settings

There are Commerce configuration settings that [!DNL Live Search] supports. This topic lists these configurations values.
The list of settings that [!DNL Live Search] cannot read is by no means complete but lists configurations that may be of interest.
We make the distinction between support of the extension itself and support in the popover.

## Supported configuration values

|Commerce Configuration Setting|Supported by Popover|Supported by Adapter|
|---|---|---|
|Stores -> Configuration -> Catalog -> Catalog -> Catalog Search -> Minimal Query Length|Yes|Yes|
|Stores -> Configuration -> Catalog -> Inventory -> Display Out of Stock Products|Yes w/ v2.0.4+|Yes w/ v2.0.4+|
|Stores -> Configuration -> General -> Currency Setup -> Currency Options -> Base Currency|Yes|Yes|

## Unsupported configuration values

|Magento Configuration Setting|Notes|
|---|---|
|Stores -> Configuration -> Catalog -> Storefront -> List Mode|Renders correctly but events are not emitted for some of the page interactions|
|Stores -> Configuration -> Catalog -> Storefront -> Allow All Products per Page|Not implemented; submits request to search service with no page size and we return default page size of 20|
|Stores -> Configuration -> Catalog -> Catalog -> Catalog Search -> Maximum Query Length|Not implemented; Search Services accepts up to 255 chars|
|Stores -> Configuration -> General -> Currency Setup -> Currency Options -> Default Display Currency|Not implemented; [!DNL Live Search] only has access to the base currency|
|Configuration -> Sales -> Tax -> Price Display Settings -> Display Product Prices In Catalog||
