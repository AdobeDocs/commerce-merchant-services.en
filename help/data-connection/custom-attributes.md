---
title: Add Custom Order Attributes
description: Learn how to add custom order attributes to your back office data and send those attributes to the Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
---
# Add Custom Order Attributes

In this article, you learn how to add custom attributes to back office events. With custom attributes, you can capture rich data insights to enhance analytics and further create personalized experiences for your shoppers.

Custom attributes are supported at two levels:

- Order level 
- Order item level

>[!NOTE]
>
>Adobe [!DNL Commerce] supports custom attributes that have a datatype of string, Boolean, or date.

Adding custom attributes to back office events requires that you:

1. Create a project in your [!DNL Commerce] installation.
1. Update your schema so that the new custom attributes can be properly ingested into Experience Platform.
1. In the Admin, confirm that the custom attributes are being captured and sent to Experience Platform.

>[!IMPORTANT]
>
>The directory structure and code samples below illustrate how you can implement custom attributes. The actual directory structure and code required depends on your store configuration and environment.

## Step 1: Create the directory structure

1. Navigate to the `app/code` directory in your [!DNL Commerce] installation and create a module directory. For example: `Magento/AepCustomAttributes`. This directory contains the files necessary for your custom attributes.
1. In the module directory, create a subdirectory called `etc`. The `etc` directory contains the `module.xml`, `query.xml`, `di.xml`, and `et_schema.xml` files.

## Step 2: Define the dependencies and the setup version

Create a `module.xml` file that defines the dependencies and the setup version. For example:

  ```xml
  <?xml version="1.0"?>
  <!--
  /**
  * Copyright (c) [year], [name]. All rights reserved.
  */
  -->
  <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
      <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
          <sequence>
              <module name="Magento_Staging"/>
              <module name="Magento_SalesRule"/>
          </sequence>
      </module>
  </config>
  ```

## Step 3: Retrieve sales order data

Create a `query.xml` file that retrieves sales order data. For example:

  ```xml
  <query>
      <source name="sales_order" type="sales">
          <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
          <link source="inventory_source_item" condition_type="by_sku"/>
      </source>
  </query>
  ```

## Step 4: Set up the dependency injection

Create a `di.xml` file that sets up the dependency injection. For example:

  ```xml
  <manifest xmlns:android="http://schemas.android.com/apk/res/android"
            package="com.example.instrumentedtest"
            android:versionCode="1"
            android:versionName="1.0">
      <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
      
      <instrumentation
          android:name=".MyInstrumentationTestRunner"
          android:targetPackage="com.example.instrumentedtest"/>
      
      <!-- More instrumentation elements might be here -->
  </manifest>
  ```

## Step 5: Define the services used for the dependency injection

Create a `et_schema.xml` file that defines the services used for the dependency injection. For example:

  ```xml
  <services>
      <service id="App\Controller\MainController" class="App\Controller\MainController">
          <argument type="service" id="doctrine.orm.default_entity_manager"/>
          <argument type="service" id="form.factory"/>
          <argument type="service" id="security.authorization_checker"/>
      </service>

      <!-- ... -->

      <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
          <argument type="service" id="security.authentication_utils"/>
          <tag name="controller.service_arguments"/>
      </service>

      <!-- ... -->
  </services>
  ```

## Step 6: Create a directory for the PHP files

At the same level as the `etc` directory, create a directory called `Module/Provider`. This directory contains the `OrderCustomAttributes` and `OrderItemCustomAttributes` PHP files.

## Step 7: Define the OrderCustomAttributes

Create a `OrderCustomAttributes.php` file that defines the order custom attributes. For example:

  ```php
  namespace App\Transformers;

  use League\Fractal\TransformerAbstract;
  use Illuminate\Support\Collection;

  class CustomAttributeTransformer extends TransformerAbstract
  {
      protected $availableIncludes = [];
      protected $defaultIncludes = [];

      public function __construct($signsField, $jsonSignsField = null)
      {
          $this->signsField = $signsField;
          $this->jsonSignsField = $jsonSignsField;
      }

      public function transform(Collection $collection)
      {
          // Initialize array for additional information.
          $additionalInformation = [];

          // Source - this comes from values sent to this transformer.
          foreach ($collection->{$this->signsField} ?: [] as $value) {
              if (is_array($value)) {
                  // If value is an array, serialize it.
                  foreach ($value as &$item) {
                      if (isset($item['custom_attr'])) {
                          // Serialize custom attribute data.
                          ...
                      }
                  }
              } else {
                  // Add non-array values directly.
                  ...
              }
          }

          ...

          return [
              'current' => ...,
              'additional_information' => ...,
              'source' => ...,
          ];
      }

      private function flatten(array $values)
      {
        return Arr::flatten($values);
    }
  }
  ```

## Step 8: Define the OrderItemCustomAttributes

Create a `OrderItemCustomAttributes.php` file that defines the order item custom attributes. For example:

  ```php
  namespace Magento\AepCustomAttributes\Model\Provider;

  use Magento\Framework\Serialize\Serializer\Json;

  class OrderItemCustomAttribute
  {
      private Json $jsonSerializer;
      private string $usingField;

      public function __construct(Json $jsonSerializer, string $usingField)
      {
          $this->jsonSerializer = $jsonSerializer;
          $this->usingField = $usingField;
      }

      public function get(array $values): array
      {
          $output = [];
          $values = $this->flatten($values);

          foreach ($values as $row) {
              $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
              $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

              $attrLabel = implode(',', ['label1', 'label2']);
              $unserializedData['custom_attr1'] = $attrLabel;

              $additionalInformation = [];
              foreach ($unserializedData as $name => $value) {
                  $additionalInformation[] = [
                      'name' => $name,
                      'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                  ];
              }

              foreach ($additionalInformation as $information) {
                  $output[] = [
                      'additionalInformation' => $information,
                      $this->usingField => $row[$this->usingField],
                  ];
              }
          }

          return $output;
      }

      private function flatten(array $values): array
      {
          return array_merge([], ...array_values($values));
      }
  }
  ```

## Step 9: Create a directory for the productContext file

At the same level as the `etc` directory, create a directory called `Plugin/Module`. This directory contains the `ProductContext.php` file.

## Step 10: Define the ProductContext class

Create a file called `ProductContext.php`that defines the `ProductContext` class. For example:

  ```php
  namespace Magento\Catalog\Model\Product;

  use Magento\Framework\App\ResourceConnection;
  use Magento\Quote\Api\Data\CartInterface;

  class ProductContext
  {
      private $brandCache = [];
      private $resourceConnection;

      public function __construct(
          ResourceConnection $resourceConnection
      ) {
          $this->resourceConnection = $resourceConnection;
      }

      public function afterGetProductData($subject, array $result)
      {
          if (isset($result['brand_id'])) {
              if (!isset($this->brandCache[$result['brand_id']])) {
                  // @todo load brand label by brand id.
                  $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
              }
              $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
          }

          return $result;
      }
  }
  ```

## Step 11: Register the module
 
 At the same level as the `etc` directory, create a `registration.php` file that registers the module. For example:

  ```php
  use \Magento\Framework\Component\ComponentRegistrar;

  ComponentRegistrar::register(
      ComponentRegistrar::MODULE,
      'Dfe_Stripe',
      __DIR__
  );
  ```

## Step 12: Extend your existing XDM schema

To ensure that the new custom order attributes can be ingested by your [!DNL Commerce] schema in Experience Platform, you need to extend the schema to include these custom fields.

To learn how to extend an existing XDM schema to include these custom fields, see the [Create and edit schemas in the UI](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) article in the Experience Platform documentation. The Tenant ID field is dynamically generated; however, the field structure should resemble the example provided in the Experience Platform documentation.

>[!IMPORTANT]
>
>XDM custom attributes must match the attributes sent from [!DNL Commerce].

To `commerce.order`, add a field for Order level:

![Order Level](assets/order-level.png)

To `productListItems`, add fields for Order item level:

![Order Item Level](assets/order-item-level.png)

## Step 12: Confirm that data is being captured

View the [Data Customization](connect-data.md#data-customization) tab in the Admin to confirm that custom attribute data is being captured and sent to the Experience Platform.

### Troubleshooting

If you see the message `No custom order attributes found.` on the **[!UICONTROL Data Customization]** tab, confirm the following:

1. You have completed the prerequisites to enable the [Data Connector extension](overview.md#prerequisites).
1. You have configured [custom order attributes](#add-custom-order-attributes).
1. At least one order event has been generated.
