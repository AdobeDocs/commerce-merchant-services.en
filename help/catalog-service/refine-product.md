---
title: refineProduct query
description: 'A reference guide for the `refineProduct` GraphQL query for Adobe Commerce Catalog Service.'
---

# refineProduct query

The `refineProduct` query narrows the results of a `products` query that was run against a complex product. Before you run the `refineProduct` query, you must run the `products` query and construct the response so that it returns a list of `options` within a `ComplexProductView` inline fragment. When a shopper selects a product option (such as size or color) on the storefront, run the `refineProduct` query, specifying the SKU and selected option value IDs as input. Depending on the number of product options the complex product has, you might need to run the `refineProduct` query multiple times, until the shopper has selected a specific variant.

You should construct the response of your query so that it contains both the `ComplexProductView` and `SimpleProductView` inline fragments. If the shopper has not selected all of the required options, the query will return the IDs of unselected options and the minimum and maximum price of the product, based on the selected options and possible remaining options. If the shopper has selected all the required options, the query returns details about a simple product, which includes a set price.

## Syntax

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## Required headers

You must specify the following HTTP headers to run this query.

|Header | Description|
|--- | ---|
|`Magento-Customer-Group` | For storefront clients, this value will be available at the storefront in the `dataservices_customer_group` cookie.|
|`Magento-Environment-Id` | This value is displayed at **System** > **Commerce Services Connector** > **SaaS Identifier** > **Data Space ID** or can be obtained by running the `bin/magento config:show services_connector/services_id/environment_id` command.|
|`Magento-Store-Code`| The code assigned to the store associated with the active store view. For example, `main_website_store`.|
|`Magento-Store-View-Code`| The code assigned to the active store view. For example, `default`.|
|`Magento-Website-Code`| The code assigned to the website associated with the active store view. For example, `base`.|
|`X-Api-Key` |  A unique key that is generated during the onboarding process.|

## Example usage

### Return details about a partially selected complex product

The following query returns details about the color options available for a medium-sized variant of product `MH12`. The value of the `optionIDs` input parameter is taken from the `products` query's [Return details about a complex product](products.md#complex-product-example) example.

**Request:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
            }
        }
    }
}
```

**Response:**

```json
{
  "data": {
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
          "values": [
            {
              "id": "Y29uZmlndXJhYmxlLzkzLzU5",
              "title": "Blue"
            },
            {
              "id": "Y29uZmlndXJhYmxlLzkzLzY3",
              "title": "Red"
            },
            {
              "id": "Y29uZmlndXJhYmxlLzkzLzYy",
              "title": "Green"
            }
          ]
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Return details about a fully selected complex product

In the following query, the shopper has selected options for both size and color. The response contains details about the corresponding simple product.

**Request:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
            }
        }
    }
}
```

**Response:**

```json
{
  "data": {
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Input fields

You must specify a SKU value and at least one option ID as input.

|Field | Data type | Description|
|--- | --- | ---|
|`optionIds` | [String!]! | A list of IDs assigned to the product options the shopper has selected, such specific colors and sizes.|
|`sku` | String! |  The SKU of a complex product.|

## Output fields

The `ProductView` return object is an interface that can contain the following fields. It is implemented by the [`SimpleProductView`](#SimpleProductView-type) and [`ComplexProductView`](#ComplexProductView-type) types.

|Field | Data Type | Description|
|--- | --- | ---|
|`attributes(roles: [String])` | [ProductViewAttribute] | A list of merchant-defined attributes designated for the storefront.|
|`description` | String | The detailed description of the product.|
|`id` | ID! | The product ID, generated as a composite key, unique per locale.|
|`images(roles: [String])` | [ProductViewImage] | A list of images defined for the product.|
|`metaDescription` | String | A brief overview of the product for search results listings.|
|`metaKeyword` | String | A comma-separated list of keywords that are visible only to search engines.|
|`metaTitle` | String | A string that is displayed in the title bar and tab of the browser and in search results lists.|
|`name` | String | Product name.|
|`shortDescription` | String | A summary of the product.|
|`sku` | String | Product SKU.|
|`url` | String | Canonical URL of the product.|

### ComplexProductView type {#ComplexProductView-type}

The `ComplexProductView` type represents bundle, configurable, and group products. Complex product prices are returned as a price range, because price values can vary based on selected options. The type implements `ProductView`.

|Field | Data Type | Description|
|`attributes(roles: [String])` | [ProductViewAttribute] | A list of merchant-defined attributes designated for the storefront.|
|`description` | String | The detailed description of the product.|
|`id` | ID! | The product ID, generated as a composite key, unique per locale.|
|`images(roles: [String])` | [ProductViewImage] | A list of images defined for the product.|
|`metaDescription` | String | A brief overview of the product for search results listings.|
|`metaKeyword` | String | A comma-separated list of keywords that are visible only to search engines.|
|`metaTitle` | String | A string that is displayed in the title bar and tab of the browser and in search results lists.|
|`name` | String | Product name.|
|`options` | [ProductViewOption] | A list of selectable options.|
|`priceRange` | ProductViewPriceRange | A range of possible prices for a complex product.|
|`shortDescription` | String | A summary of the product.|

### Price type

The `Price type` defines the price of a simple product or a part of a price range for a complex product. It can include a list of price adjustments.

|`amount` | ProductViewMoney | Contains the monetary value and currency code of a product. |

### PriceAdjustment type

The `PriceAdjustment` type specifies the amount and type of a price adjustment. An example code value is `weee`.

|Field | Data Type | Description|
|--- | --- | ---|
|`amount` | Float | The amount of the price adjustment.|
|`code` | String | Identifies the type of price adjustment.|

### ProductViewAttribute type

The `ProductViewAttribute` type is a container for customer-defined attributes that are displayed the storefront.

|Field | Data Type | Description|
|--- | --- | ---|
|`label` | String | Label of the attribute.|
|`name` | String! | Name of an attribute code.|
|`roles` | [String] | Roles designated for an attribute on the storefront, such as "Show on PLP", "Show in PDP", or "Show in Search".|
|`value` | JSON | Attribute value, arbitrary of type.|

### ProductViewImage type

The `ProductViewImage` type contains details about a product image.

|Field | Data Type | Description|
|--- | --- | ---|
|`label` | String | The display label of the product image.|
|`roles` | [String] | A list that describes how the image is used. Can be `image`, `small_image`, or `thumbnail`.|
|`url` | String! | The URL to the product image.|

### ProductViewMoney type

The `ProductViewMoney` type defines a monetary value, including a numeric value and a currency code.

|Field | Data Type | Description|
|--- | --- | ---|
|`currency` | ProductViewCurrency | A three-letter currency code, such as USD or EUR.|
|`value` | Float | A number expressing a monetary value.|

### ProductViewOption type

Product options provide a way to configure products by making selections of particular option values. Selecting one or many options will point to a specific simple product.

|Field | Data Type | Description|
|--- | --- | ---|
|`id` | ID | The ID of the option.|
|`multi` | Boolean | Indicates whether the option allows multiple choices.|
|`required` | Boolean | Indicates whether the option must be selected.|
|`title` | String | The display name of the option.|
|`values` | [ProductViewOptionValue!] | List of available option values.|

### ProductViewOptionValue interface

The `ProductViewOptionValue` interface defines the product fields available to the `ProductViewOptionValueProduct` and `ProductViewOptionValueConfiguration` types.

|Field | Data Type | Description|
|--- | --- | ---|
|`id` | ID | The ID of an option value.|
|`title` | String | The display name of the option value.|

### ProductViewOptionValueConfiguration type

The `ProductViewOptionValueConfiguration` type is an implementation of `ProductViewOptionValue` for configuration values.

|Field | Data Type | Description|
|--- | --- | ---|
|`id` | ID | The ID of an option value.|
|`title` | String | The display name of the option value.|

### ProductViewOptionValueProduct type

The `ProductViewOptionValueProduct` type is an implementation of `ProductViewOptionValue` that adds details about a simple product.

|Field | Data Type | Description|
|--- | --- | ---|
|`id` | ID | The ID of an option value.|
|`title` | String | The display name of the option value.|
|`product` | SimpleProductView | Details about a simple product.|

### ProductViewPrice type

The `ProductViewPrice` type provides the base product price view, inherent for simple products.

|Field | Data Type | Description|
|--- | --- | ---|
|`final` | Price | Price value after discounts, excluding personalized promotions.|
|`regular` | Price | Base product price specified by the merchant.|
|`roles` | [String] | Determines if the price should be visible or hidden.|

### ProductViewPriceRange type

The `ProductViewPriceRange` type lists the minimum and maximum price of a complex product.

|Field | Data Type | Description|
|--- | --- | ---|
|`maximum` | ProductViewPrice | Maximum price.|
|`minimum` | ProductViewPrice | Minimum price.|

### SimpleProductView type {#SimpleProductView-type}

The `SimpleProductView` type represents all product types, except bundle, configurable, and group. Simple product prices do not contain price ranges. `SimpleProductView` implements `ProductView`.

|Field | Data Type | Description|
|--- | --- | ---|
|`attributes(roles: [String])` | [ProductViewAttribute] | A list of merchant-defined attributes designated for the storefront.|
|`description` | String | The detailed description of the product.|
|`id` | ID! | The product ID, generated as a composite key, unique per locale.|
|`images(roles: [String])` | [ProductViewImage] | A list of images defined for the product.|
|`metaDescription` | String | A brief overview of the product for search results listings.|
|`metaKeyword` | String | A comma-separated list of keywords that are visible only to search engines.|
|`metaTitle` | String | A string that is displayed in the title bar and tab of the browser and in search results lists.|
|`name` | String | Product name.|
|`price` | ProductViewPrice | Base product price view.|
|`shortDescription` | String | A summary of the product.|
|`sku` | String | Product SKU.|
|`url` | String | Canonical URL of the product.|
