---
title: Extend and customize SaaS data export feed data
description: Learn how to extend and customize the [!DNL SaaS Data Export] feed data.
role: Admin, Developer
recommendations: noCatalog
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
---
# Extend and customize SaaS data export feed data

The [!DNL Commerce Data Export] extension provides a way to export data from the [!DNL Commerce] application to Commerce Services like Live Search, Catalog Service, and Product Recommendations. If needed, you can extend and customize the feed data to include additional data or modify the collected data by updating the `Magento\CatalogDataExporter` module.

>[!NOTE]
>
>Adding new data to the feed or modifying existing data can affect the feed collection performance and cause issues in processing logic on the Adobe Commerce side. Be sure to test the customized code before merging to a production environment.

## Extend attributes data in the products feed

The products feed includes default attributes which are required for product processing or commonly used by consumers. You can include additional system attributes in the products feed by adding them to the feed. 

To complete this task, update the `magento/catalog-data-exporter` module to add the additional system attributes to the [dependency injection configuration file](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`). Add the attributes to the  Product Attribute query (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`). 

**Example**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
