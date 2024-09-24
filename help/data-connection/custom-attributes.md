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
>Adobe [!DNL Commerce] supports custom attributes that have a datatype of string or string array.

Adding custom attributes to back office events requires that you:

1. Create a project in your [!DNL Commerce] installation.
1. Update your schema so the new custom attributes can be properly ingested into Experience Platform.
1. Confirm in the Admin that the custom attributes are being captured and sent to Experience Platform.

>[!IMPORTANT]
>
>The directory structure and code samples below are examples for how you can implement custom attributes. The actual directory structure and code you need depends on your store configuration and environment.

## Step 1: Create a custom module to add custom attributes

1. Navigate to the `app/code` directory in your [!DNL Commerce] installation and create a module directory. For example: `Magento/AepCustomAttributes`. This directory will contain the files necessary for your custom attributes.

1. In the module directory, create a subdirectory called `etc`. Inside the `etc` directory, create a `module.xml` file that defines the dependencies and the setup version. For example:

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

1. In the same `etc` subdirectory, create a `query.xml` file to retrieve sales order data. For example:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

1. Inside the `etc` subdirectory, create a `di.xml` file that sets up the dependency injection. For example:

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

1. Inside the `etc` directory, create an `et_schema.xml` configuration file to define the services used for the dependency injection. For example:

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

1. Define the `OrderCustomAttributes` in PHP. For example:

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

1. Define the `OrderItemCustomAttributes` in PHP. For example:

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

1. Define the `ProductContext` class in PHP to handle the product data.

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

1. Create a `registration.php` file inside `app/code/Magento/AepCustomAttributes`. For example:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Step 2: Extend your existing XDM schema

Refer to the following [article](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) to learn how to update your existing XDM schema. The Tenant ID field is dynamically generated, however the field structure should resemble the example provided.

>[!IMPORTANT]
>
>XDM custom attributes must match the attributes sent from [!DNL Commerce].

To `commerce.order`, add a field for Order level:

![Order Level](assets/order-level.png)

To `productListItems`, add a field(s) for Order item level:

![Order Item Level](assets/order-item-level.png)

## Step 3: Confirm data is being captured

You can confirm that custom attribute data is being captured and sent to the Experience Platform using the **Custom Order Attributes** table on the [Data Customization](connect-data.md#data-customization) tab in the Admin.
