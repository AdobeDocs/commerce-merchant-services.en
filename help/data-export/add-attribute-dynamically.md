---
title: Add product attributes dynamically
description: Learn how to add custom product attributes to data export feed dynamically during the data synchronization process.
role: Admin, Developer
exl-id: fd0e142e-eb39-4c4b-90da-6c9279b7706c
---
# Add product attributes dynamically during data synchronization

You can extend product attributes without registering them in Adobe Commerce by creating a plugin to add the attributes during the data synchronization process.

>[!NOTE]
>
>The best way to extend product attributes is to [add them to Adobe Commerce](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) where you can configure and manage them from the Commerce Admin. Only add them dynamically if you need them solely for Commerce storefront services and do not want to register them in Adobe Commerce. You also have the option to manage custom attributes using [API Mesh with the Catalog Service](../catalog-service/mesh.md) to extend the Catalog Service GraphQL schema.

## Add product attributes

Create a plugin that adds a `customer_attribute` to the `Magento\CatalogDataExporter\Model\Provider\Product\Attributes` class.

1. Update the [dependency injection configuration file](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) to define the plugin.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\Product\Attributes">
     <plugin name="product_customer_attributes" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttribute"/>
   </type>
   ```

1. Create the plugin.

   ```php
    <?php
    declare(strict_types=1);

    namespace Vendor\CatalogDataExporter\Model\Plugin;

    use Magento\CatalogDataExporter\Model\Provider\Product\Attributes;

    class AddAttribute {

         /**
          * @param Attributes $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(Attributes $subject, array $result, $arguments): array
         {
              $productIds = \array_column($arguments, 'productId');

              foreach ($productIds as $productId) {
                    $result[] = [
                         'productId' => $productId,
                         // "storeViewCode" must be specified for products where the customer attribute value should be set
                         'storeViewCode' => 'default',
                         'attributes' => [
                              // specify the customer attribute code
                              'attributeCode' => 'customer_attribute',
                              // provide single or multiple values for the attribute
                              'value' => [
                                    rand(41,43)
                              ]
                         ]
                    ];
              }

              return $result;
         }
    }
   ```

   After you add the plugin, the changes are synchronized to connected storefront services during the next scheduled synchronization. To send the updates immediately, use the following CLI command to start the synchronization process manually.

   ```
   bin/magento saas:resync --feed=products
   ```

## Declare custom product attribute metadata

If you dynamically create a custom product attribute and want to use it for display, search, or filtering in storefront services, add the product attribute metadata to configure the storefront behavior.

1. Update the [dependency injection configuration file](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) to define the plugin for the product attribute metadata.

     ```xml
     <type name="\Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
       <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
     </type>
     ```

1. Create the plugin to the following provider `\Magento\CatalogDataExporter\Model\Provider\ProductMetadata`.

   Check `ProductAttributeMetadata` in `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` for required fields.

     ```php
      <?php
      declare(strict_types=1);

      namespace Vendor\CatalogDataExporter\Model\Plugin;

      use Magento\CatalogDataExporter\Model\Provider\ProductMetadata;

      class AddAttributeMetadata {

           /**
            * @param ProductMetadata $subject
            * @param array $result
            * @param $arguments
            * @return array
            * @throws \Zend_Db_Statement_Exception
            */
           public function afterGet(ProductMetadata $subject, array $result, $arguments): array
           {
                $result[] = [
                  'id' => '123',
                  'storeCode' => 'default',
                  'websiteCode' => 'base',
                  'storeViewCode' => 'default',
                  // specify the customer attribute code - should be the same as used in the products attributes plugin
                  'attributeCode' => 'customer_attribute',
                  // only product attributes are supported
                  'attributeType' => 'catalog_product',
                  // specify the data type
                  'dataType' => 'int',
                  'multi' => false,
                  'label' => 'Customer Attribute',
                  'frontendInput' => 'select',
                  'required' => false,
                  'unique' => false,
                  'global' => true,
                  'visible' => true,
                  'searchable' => true,
                  'filterable' => true,
                  // This value must be set to true to export it to the storefront services
                  'visibleInCompareList' => true,
                  'visibleInListing' => true,
                  'sortable' => true,
                  'visibleInSearch' => true,
                  'filterableInSearch' => true,
                  'searchWeight' => 1.0,
                  'usedForRules' => true,
                  'boolean' => false,
                  'systemAttribute' => false,
                  'numeric' => false,
                  // specify the list of attribute options
                  'attributeOptions' => [
                      'option1',
                      'option2',
                      'option3'
                  ]
               ];

                return $result;
           }
        }
     ```

     After you add the plugin, the changes are synchronized to connected storefront services during the next scheduled synchronization. To send the updates immediately, use the following CLI command to start the synchronization process manually.

     ```
     bin/magento saas:resync --feed=productattributes
     ```
