---
title: Extend and customize SaaS data export feed data
description: Learn how to extend and customize the [!DNL SaaS Data Export] feed data.
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
---
# Extend and customize SaaS data export feed data

The [!DNL Commerce Data Export] extension provides a way to export data from the [!DNL Commerce] application to Commerce Services like Live Search, Catalog Service, and Product Recommendations. If needed, you can extend and customize the feed data to include additional attribute data or modify the collected data.

After adding attribute data, it is accessible from the [attributes field](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type) in the GraphQL schema for storefront service.

>[!NOTE]
>
>Adding or modifying feed data can impact performance and processing logic on the Commerce backend. Test customized code before merging to production. Instead of adding data to the backend, use API Mesh to extend the Catalog Service GraphQL schema. For configuration details, see [Catalog Service and API Mesh](../catalog-service/mesh.md).

## Extend system attributes data in the products feed

The products feed includes default system attributes which are required for product processing or commonly used by consumers. You can include additional system attributes in the products feed by adding them to the feed.

To complete this task, update the `magento/catalog-data-exporter` module to add the additional system attributes to the [dependency injection configuration file](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`).

Add the attributes to the Product Attribute query(`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

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

## Add product attributes to Adobe Commerce

Developers can add product attributes that are accessible from the [product attributes field](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#output-fields) by using one of the following methods:

- Add the attribute to Adobe Commerce for inclusion in the `products` feed data exported to Commerce storefront services.
- Add the attribute dynamically during the feed synchronization process using a plugin.

### Add the attribute to Adobe Commerce

You can add a product attribute from the Commerce Admin, or programmatically using a custom PHP module to define the attribute and update Adobe Commerce. This is the simplest method for adding a product attribute because you can add the attribute and all required metadata. The new attribute and its metadata properties are exported to the SaaS services automatically during the next scheduled synchronization.

#### Create the product attribute from the Admin

1. From the Commerce Admin, create the attribute from the product attribute configuration page ([!UICONTROL Stores] > *[!UICONTROL Attributes]* > [!UICONTROL Product]).

1. Add the attribute to an attribute set as needed.

See [Create product attributes](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create) in the *Adobe Commerce Admin Guide*.

#### Create the product attribute programmatically

Add a product attribute programmatically by creating a data patch that implements the `DataPatchInterface`, and instantiate a copy of the `EavSetup Factory` class within the constructor to configure the attribute options.

When you define the attribute options, all attribute parameters except `type`, `label`, and `input` are optional. Define the following additional options and any other options that differ from the default settings.

- Ensure that the property is exported to storefront services during data synchronization by setting `user_defined` = `1`
- To ensure that the attribute is accessible within the product listing database query, set `used_in_product_listing` = `1`.

For information about creating data patches, see [Develop data and schema patches](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) in the *PHP Developer Guide*.

### Add the product attribute dynamically

For details about creating product attributes dynamically without introducing new Eav Attributes, see [Add attribute dynamically](add-attribute-dynamically.md).
