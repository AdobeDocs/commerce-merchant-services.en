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
|Stores > Configuration > Catalog > Catalog > Catalog Search > Allow All Products per Paage Length|Yes. Max 500 products|Yes. Max 500 products|
|Stores > Configuration > Catalog > Catalog > Catalog Search > Minimal Query Length|Yes|Yes|
|Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Allowed Values|Yes|Yes|
|Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Default Value|Yes|Yes|
|Stores > Configuration > Catalog > Inventory > Display Out of Stock Products|Yes w/ v2.0.4+|Yes w/ v2.0.4+|
|Stores > Configuration > Currency > Default Display Currency|Yes w/3.1.0+|Yes w/3/1/0+|
|Stores > Configuration > General > Currency Setup > Currency Options > Base Currency|Yes|Yes|

Prices in the Widget Product Listing Page and Popover are now converted to the Default Display Currency using the configured Currency Rates

## Unsupported configuration values

[!DNL Live Search] cannot read all configuration values. This table lists values that may be of higher interest to developers.

|Commerce Configuration Setting|Notes|
|---|---|
|Stores > Configuration > Catalog > Storefront > List Mode|Renders correctly but events are not sent for some page interactions|
|Stores > Configuration > Catalog > Catalog > Catalog Search > Maximum Query Length|Not implemented; Search Services accepts up to 255 characters|
|Configuration > Sales > Tax > Price Display Settings > Display Product Prices In Catalog||
