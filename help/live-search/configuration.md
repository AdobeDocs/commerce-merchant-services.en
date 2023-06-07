---
title: 'Commerce Configurations Settings and [!DNL Live Search] '
description: Describes the Adobe Commerce configuration settings that [!DNL Live Search] can read.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
---
# [!DNL Live Search] and Adobe Commerce Configuration Settings

There are Commerce configuration settings that [!DNL Live Search] supports. This topic lists these configurations values.

## Supported configuration values

|Commerce Configuration Setting|Supported by Popover|Supported by Adapter|
|---|---|---|
|Stores -> Configuration -> Catalog -> Catalog -> Catalog Search -> Minimal Query Length|Yes|Yes|
|Stores -> Configuration -> Catalog -> Inventory -> Display Out of Stock Products|Yes w/ v2.0.4+|Yes w/ v2.0.4+|
|Stores -> Configuration -> General -> Currency Setup -> Currency Options -> Base Currency|Yes|Yes|

## Unsupported configuration values

[!DNL Live Search] cannot read all configuration values. This table lists values that may be of higher interest to developers.

|Magento Configuration Setting|Notes|
|---|---|
|Stores -> Configuration -> Catalog -> Storefront -> List Mode|Renders correctly but events are not sent for some page interactions|
|Stores -> Configuration -> Catalog -> Storefront -> Allow All Products per Page|Not implemented; submits request to search service with no page size and [!DNL Live Search] returns a default page size of 20|
|Stores -> Configuration -> Catalog -> Catalog -> Catalog Search -> Maximum Query Length|Not implemented; Search Services accepts up to 255 characters|
|Stores -> Configuration -> General -> Currency Setup -> Currency Options -> Default Display Currency|Not implemented; [!DNL Live Search] only has access to the base currency|
|Configuration -> Sales -> Tax -> Price Display Settings -> Display Product Prices In Catalog||
