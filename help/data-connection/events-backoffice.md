---
title: Back Office Events
description: Learn what data each back office event captures.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: a5a4f04b-89ac-4020-95ce-984f9f2d8385
---
# [!DNL Data Connection] Back Office Events

The following lists the Commerce back office events available when you install the [!DNL Data Connection] extension. The data these events collect is sent to the Adobe Experience Platform. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

In addition to the data the following events collect, you also get [other data](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) provided by the Adobe Experience Platform Web SDK.

Back office events contain server-side data. This data comprises [order status](#order-status) information such as if an order was placed, canceled, refunded, shipped, or completed. Server-side data also includes [customer profile events](#customer-profile-events) information, such as if an account was created, updated, or deleted.

>[!NOTE]
>
>All back office events include the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which includes the shopper's email address, when available, and ECID.

## Order status

Order status data shows a 360 view of the shopper order. This view helps merchants better target or analyze the entire order status when developing marketing campaigns. For example, you can spot trends in certain product categories that perform well at different times of the year. Such as, winter clothes that sell better during colder months or certain product colors that shoppers are interested in over the years. In addition, order status data can help you calculate lifetime customer value by understanding a shopper's propensity to convert based on previous orders.

### orderPlaced

|Description| XDM event name|
|---|---|
|Triggered when a shopper places an order.|`commerce.backofficeOrderPlaced`|

#### Data collected from orderPlaced

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.paymentTransactionID`|Unique identifier for this payment transaction.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Counted, custom values allowed.|
|`commerce.order.payments.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.taxAmount`|The tax amount paid by the buyer as part of the final payment.|
|`commerce.order.discountAmount`|Indicates the discount amount applied to the whole order.|
|`commerce.order.createdDate`|The time and date when a new order is created in the commerce system. For example, `2022-10-15T20:20:39+00:00`.|
|`commerce.order.currencyCode`|The ISO 4217 currency code used for the order totals.|
|`commerce.shipping`|Shipping details for one or more products.|
|`commerce.shipping.shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on.|
|`commerce.shipping.shippingAmount`|The amount the customer had to pay for shipping.|
|`commerce.shipping.currencyCode`|The ISO 4217 currency code used for the shipping total.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`commerce.billing.address`|Billing postal address.|
|`commerce.billing.address.street1`|Primary street level information, apartment number, street number, and street name|
|`commerce.billing.address.street2`|Additional field for street level information.|
|`commerce.billing.address.city`|The name of the city.|
|`commerce.billing.address.state`|The name of the state. This is a free-form field.|
|`commerce.billing.address.postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`commerce.billing.address.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.id`|The line item identifier for this product entry.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|
|`productListItems.productImageUrl`|Main image URL of the product.|

### orderInvoiced

|Description| XDM event name|
|---|---|
|Triggered when a merchant submits an invoice to request payment.|`commerce.backofficeOrderInvoiced`|

#### Data collected from orderInvoiced

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.priceTotal`|The total price of this order after all discounts and taxes have been applied.|
|`commerce.order.currencyCode`|The ISO 4217 currency code used for the order totals.|
|`commerce.order.purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Counted, custom values allowed.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.shipping`|Shipping details for one or more products.|
|`commerce.shipping.shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on.|
|`commerce.shipping.shippingAmount`|The amount the customer had to pay for shipping.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.id`|The line item identifier for this product entry.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|

### orderItemsShipped

|Description| XDM event name|
|---|---|
|Triggered when an order is shipped.|`commerce.backofficeOrderItemsShipped`|

#### Data collected from orderItemsShipped

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.paymentTransactionID`|Unique identifier for this payment transaction.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Counted, custom values allowed.|
|`commerce.order.payments.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.priceTotal`|The total price of this order after all discounts and taxes have been applied.|
|`commerce.order.purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract.|
|`commerce.order.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.lastUpdatedDate`|The time when a particular order record is last updated in the commerce system.|
|`commerce.shipping`|Shipping details for one or more products.|
|`commerce.shipping.shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on.|
|`commerce.shipping.shippingAmount`|The amount the customer had to pay for shipping.|
|`commerce.shipping.address`|The physical shipping address.|
|`commerce.shipping.address.street1`|Primary street level information, apartment number, street number, and street name.|
|`commerce.shipping.address.street2`|Optional street information second line.|
|`commerce.shipping.address.city`|The name of the city.|
|`commerce.shipping.address.state`|The name of the State. This is a free-form field.|
|`commerce.shipping.address.postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`commerce.shipping.address.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`commerce.shipping.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.shipping.trackingNumber`|The tracking number provided by the shipping carrier for an order item shipment.|
|`commerce.shipping.trackingURL`|The URL to track the shipping status of an order item.|
|`commerce.shipping.shipDate`|The date when one or more items from an order is shipped.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`commerce.billing.address`|Billing postal address.|
|`commerce.billing.address.street1`|Primary street level information, apartment number, street number, and street name|
|`commerce.billing.address.street2`|Additional field for street level information.|
|`commerce.billing.address.city`|The name of the city.|
|`commerce.billing.address.state`|The name of the state. This is a free-form field.|
|`commerce.billing.address.postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`commerce.billing.address.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|

### orderCancelled

|Description| XDM event name|
|---|---|
|Triggered when a shopper cancels an order.|`commerce.backofficeOrderCancelled`|

#### Data collected from orderCancelled

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract.|
|`commerce.order.cancelDate`|The date and time when a shopper cancels an order.|
|`commerce.order.lastUpdatedDate`|The time when a particular order record is last updated in the commerce system.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|

### orderLineItemRefunded

|Description| XDM event name|
|---|---|
|Triggered when a shopper is refunded for a returned item.|`commerce.backofficeCreditMemoIssued`|

#### Data collected from orderLineItemRefunded

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.lastUpdatedDate`|The time when a particular order record is last updated in the commerce system.|
|`commerce.order.purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract.|
|`commerce.refunds`|The list of refunds for this order.|
|`commerce.refunds.transactionID`|Unique identifier for this refund.|
|`commerce.refunds.refundAmount`|The value of the refund.|
|`commerce.refunds.refundPaymentType`|The method of payment for this order. Counted, custom values allowed.|
|`commerce.refunds.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|

### orderItemsReturnInitiated

|Description| XDM event name|
|---|---|
|Triggered when a shopper requests to return an item.|`commerce.backofficeOrderItemsReturnInitiated`|

#### Data collected from orderItemsReturnInitiated

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.returns`|The RMA (Return Merchandise Authorization) information for this order.|
|`commerce.order.returns.returnID`|The unique identifier for this RMA (Return Merchandise Authorization).|
|`commerce.order.returns.returnStatus`|The status of the RMA (Return Merchandise Authorization), such as Pending, Closed, and so on.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|
|`productListItems.returnItem`|The RMA (Return Merchandise Authorization) information for this item.|
|`productListItems.returnItem.returnStatus`|The status of the returned item, such as Pending, Approved, and so on.|
|`productListItems.returnItem.returnReason`|The reason why a return is requested for this item.|
|`productListItems.returnItem.returnItemCondition`|The condition of the item that the return is requested for.|
|`productListItems.returnItem.returnResolution`|The requested resolution of the item being returned, such as Refund, Exchange, and so on.|
|`productListItems.returnItem.returnQuantityRequested`|The number of this item that the shopper requested to return.|
|`productListItems.returnItem.returnQuantityAuthorized`|The number of this item that is authorized to be returned.|
|`productListItems.returnItem.eturnQuantityReceived`|The number of returned items received.|
|`productListItems.returnItem.returnQuantityApproved`|The number of this item with return fully complete and approved.|

### orderItemReturnCompleted

|Description| XDM event name|
|---|---|
|Triggered when an item a shopper requested to return is completed.|`commerce.backofficeOrderItemsReturnCompleted`|

#### Data collected from orderItemReturnCompleted

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.returns`|The RMA (Return Merchandise Authorization) information for this order.|
|`commerce.order.returns.returnID`|The unique identifier for this RMA (Return Merchandise Authorization).|
|`commerce.order.returns.returnStatus`|The status of the RMA (Return Merchandise Authorization), such as Pending, Closed, and so on.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|
|`productListItems.returnItem`|The RMA (Return Merchandise Authorization) information for this item.|
|`productListItems.returnItem.returnStatus`|The status of the returned item, such as Pending, Approved, and so on.|
|`productListItems.returnItem.returnReason`|The reason why a return is requested for this item.|
|`productListItems.returnItem.returnItemCondition`|The condition of the item that the return is requested for.|
|`productListItems.returnItem.returnResolution`|The requested resolution of the item being returned, such as Refund, Exchange, and so on.|
|`productListItems.returnItem.returnQuantityRequested`|The number of this item that the shopper requested to return.|
|`productListItems.returnItem.returnQuantityAuthorized`|The number of this item that is authorized to be returned.|
|`productListItems.returnItem.eturnQuantityReceived`|The number of returned items received.|
|`productListItems.returnItem.returnQuantityApproved`|The number of this item with return fully complete and approved.|

### orderShipmentCompleted

|Description| XDM event name|
|---|---|
|Triggered when a shipment is completed.|`commerce.backofficeOrderShipmentCompleted`|

#### Data collected from orderShipmentCompleted

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.paymentTransactionID`|Unique identifier for this payment transaction.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Counted, custom values allowed.|
|`commerce.order.payments.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.taxAmount`|The tax amount paid by the buyer as part of the final payment.|
|`commerce.order.createdDate`|The time and date when a new order is created in the commerce system. For example, `2022-10-15T20:20:39+00:00`.|
|`commerce.shipping`|Shipping details for one or more products.|
|`commerce.shipping.shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on.|
|`commerce.shipping.shippingAmount`|The amount the customer had to pay for shipping.|
|`commerce.shipping.shipDate`|The date when one or more items from an order is shipped.|
|`commerce.shipping.address`|The physical shipping address.|
|`commerce.shipping.address.street1`|Primary street level information, apartment number, street number, and street name.|
|`commerce.shipping.address.street2`|Optional street information second line.|
|`commerce.shipping.address.city`|The name of the city.|
|`commerce.shipping.address.state`|The name of the State. This is a free-form field.|
|`commerce.shipping.address.postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`commerce.shipping.address.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`commerce.billing.address`|Billing postal address.|
|`commerce.billing.address.street1`|Primary street level information, apartment number, street number, and street name|
|`commerce.billing.address.street2`|Additional field for street level information.|
|`commerce.billing.address.city`|The name of the city.|
|`commerce.billing.address.state`|The name of the state. This is a free-form field.|
|`commerce.billing.address.postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`commerce.billing.address.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products in the order.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|
|`productListItems.categories`|Contains information about the category of a product.|
|`productListItems.categories.id`|The unique identifier of the category.|
|`productListItems.categories.name`|The name of the category.|
|`productListItems.categories.path`|The path to the category.|

## Customer profile events

Profile events captured from the server-side include account information, such as `accountCreated`, `accountUpdated`, and `accountDeleted`. This data is used to help populate key customer details that are needed to better define segments or execute marketing campaigns, such as sending sign-up discount offers, account change confirmations, and so on. There are similar profile events captured from the [storefront](events.md#customer-profile-events).

>[!NOTE]
>
>Each customer profile event also includes the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which includes the system generated Commerce Customer ID as the primary identifier for the profile and an email ID that is used as a secondary identifier.

### accountCreated

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to create an account.|`userAccount.backofficeCreateProfile`|

#### Data collected from accountCreated

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`person`|Contains information about the customer.|
|`person.name`|Contains information about the name of the customer.|
|`person.name.firstName`|Contains the first name of the customer.|
|`person.name.lastName`|Contains the last name of the customer.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

### accountUpdated

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to edit an account.|`userAccount.backofficeUpdateProfile`|

#### Data collected from accountUpdated

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`person`|Contains information about the customer.|
|`person.name`|Contains information about the name of the customer.|
|`person.name.firstName`|Contains the first name of the customer.|
|`person.name.lastName`|Contains the last name of the customer.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

### accountDeleted

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to delete an account.|`userAccount.backofficeDeleteProfile`|

#### Data collected from accountDeleted

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`person`|Contains information about the customer.|
|`person.name`|Contains information about the name of the customer.|
|`person.name.firstName`|Contains the first name of the customer.|
|`person.name.lastName`|Contains the last name of the customer.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
