---
title: SaaS Price Indexing
description: Using the SaaS Price Indexing to improve performance
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
---
# SaaS Price Indexing

SaaS price indexing speeds up the time that it takes for price changes to get reflected on [Commerce Services ](../landing/saas.md) after they have been submitted. This allows merchants with large, complex catalogs, or with multiple websites or customer groups, to process price changes more rapidly and continuously.

Additionally, if you have a Headless Storefront or with additional [catalog-adapter](./catalog-adapter.md) extension, customer can disable Adobe Commerce core price indexer.

The biggest bottleneck of the pipeline: computational heavy processes such as indexation and price calculation, have been moved from the PHP core to the Adobe's Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes to websites at much faster speeds.

The Core indexing data flow to SaaS services looks like:

![Default data flow](assets/old_way.png)

With SaaS price indexing, the flow is:

![SaaS price indexing data flow](assets/new_way.png)

All merchants can benefit from these improvements, but those who will see the greatest gains are customers with: 

* Constant price changes: Merchants that require repeated changes to their prices to meet strategic goals such as frequent promotions, seasonal discounts, or inventory markdowns.
* Multiple websites and/or customer groups: Merchants with shared product catalogs across multiple websites (domains/brands) and/or customer groups. 
* Large number of unique prices across websites or customer groups: Merchants with extensive shared product catalogs that contain unique prices across websites or customer groups, such as B2B merchants with pre-negotiated prices, brands with different pricing strategies.

SaaS price indexing is available for free for customers using Adobe Commerce services and supports price calculation for all built-in Adobe Commerce Product Types.

This mini-guide describes how SaaS price indexing works and how to enable it.

## Requirements

* Adobe Commerce 2.4.4+
* At least one of the following Commerce Services with the latest version of Adobe Commerce extension:

    * [Catalog Service](../catalog-service/overview.md) starting from `magento/catalog-service:3.0.0`  
    * [Live Search](../live-search/guide-overview.md) starting from `magento/live-search:3.1.1`
    * [Product Recommendations](../product-recommendations/guide-overview.md) starting from `magento/product-recommendations:5.0.1`

SaaS price indexing is available out of the box with the latest version of mentioned service.
If you have an older version, please refer to the [`Manual Installation`](installation.md) section.


Luma and Adobe Commerce Core GraphQL users can install the [`catalog-adapter`](catalog-adapter.md) extension that provides Luma and Core GraphQl compatibility and disables the Adobe Commerce Product Price indexer.

## Usage

After upgrading Adobe Commerce instance with SaaS price indexing support is highly recommended to sync new available feeds: 

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

Otherwise, the data gets refreshed in the standard sync process which may cause delays. Get more information about the [Catalog Sync](../landing/catalog-sync.md) process.

To gain the maximum benefits of SaaS price indexing please consider disabling Adobe Commerce price with [`Catalog Adapter`](catalog-adapter.md) extension.

## Support Prices for Custom Product Type

Out of the box price calculation is supported for Custom Product Type for standard price features available in the Adobe Commerce core edition, such as base price, special price, group price, catalog rule price, etc.

However, if you have Custom Product Type that uses specific formula to calculate final price , you should extend behaviour of the product price feed.

Below you can find one of possible options how to do it:

1. Create a plugin on the `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` class.

`di.xml` file:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

1. Create a method with the custom formula:

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Override the output $result with your data for the corresponding products (see original method for details) 
        return $result;
    }
}
```
