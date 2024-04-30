---
title: SaaS Price Indexing
description: Using the SaaS Price Indexing to improve performance
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
---
# SaaS Price Indexing

SaaS price indexing speeds up the time that it takes for price changes to get reflected on [Commerce Services ](../landing/saas.md) after they have been submitted. This allows merchants with large, complex catalogs, or with multiple websites or customer groups, to continually process price changes.
If you have a headless storefront or use the [catalog-adapter](./catalog-adapter.md) extension, customers can disable the Adobe Commerce core price indexer.

Computational heavy processes such as indexation and price calculation have been moved from the Commerce core to Adobe's Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes faster.

The Core indexing data flow to SaaS services looks like:

![Default data flow](assets/old_way.png)

With SaaS price indexing, the flow is:

![SaaS price indexing data flow](assets/new_way.png)

All merchants can benefit from these improvements, but those who will see the greatest gains are customers with: 

* Constant price changes: Merchants that require repeated changes to their prices to meet strategic goals such as frequent promotions, seasonal discounts, or inventory markdowns.
* Multiple websites and/or customer groups: Merchants with shared product catalogs across multiple websites (domains/brands) and/or customer groups. 
* Large number of unique prices across websites or customer groups: merchants with extensive shared product catalogs that contain unique prices across websites or customer groups, such as B2B merchants with pre-negotiated prices, brands with different pricing strategies.

SaaS price indexing is available for free for customers using Adobe Commerce services and supports price calculation for all built-in Adobe Commerce product types.

This guide describes how SaaS price indexing works and how to enable it.

## Requirements

* Adobe Commerce 2.4.4+
* At least one of the following Commerce Services with the latest version of Adobe Commerce extension:

    * [Catalog Service](../catalog-service/overview.md) 
    * [Live Search](../live-search/overview.md)
    * [Product Recommendations](../product-recommendations/guide-overview.md)

Luma and Adobe Commerce Core GraphQL users can install the [`catalog-adapter`](catalog-adapter.md) extension that provides Luma and Core GraphQl compatibility and disables the Adobe Commerce Product Price indexer.

## Usage

After upgrading your Adobe Commerce instance with SaaS price indexing support, sync the new feeds: 

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Prices for custom product types

Price calculations are supported for custom product types such as base price, special price, group price, catalog rule price, etc.

If you have a custom product type that uses a specific formula to calculate final price, you can extend the behavior of the product price feed.

1. Create a plugin on the `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` class.

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
