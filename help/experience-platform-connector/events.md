---
title: Events
description: Learn what data each event captures.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
---
# Experience Platform Connector Events

The following lists the Commerce events available when you install the Experience Platform connector extension. The data these events collect is sent to the Adobe Experience Platform edge. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

In addition to the data the following events collect, you also get [other data](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) provided by the Adobe Experience Platform Web SDK.

## Storefront events

+++ The storefront events collect anonymized behavioral data from your shoppers as they browse your site. The data these events collect can be used to create promotions and campaigns targeted to a specific set of shoppers.

>[!NOTE]
>
>All storefront events include the `personID` field, which is a unique identifier of the person.

### addToCart

|Description| XDM event name|
|---|---|
|Triggered when a product is added to the cart or when the quantity of a product in the cart is incremented.|`commerce.productListAdds`|

#### Data collected from addToCart

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`productListAdds`|Indicates if a product was added to a shopping cart. A value of `1` indicates that a product was added.|
|`productListItems`|An array of products added to the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units added to the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

### openCart

|Description| XDM event name|
|---|---|
|Triggered when a new cart is created, which is when a product is added to an empty cart.|`commerce.productListOpens`|

#### Data collected from openCart

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`productListOpens`|Indicates if a cart was created. A value of `1` indicates that a cart was created.|
|`productListItems`|An array of products added to the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units added to the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

### removeFromCart

|Description| XDM event name|
|---|---|
|Triggered every time a product is removed or every time the quantity of a product in the cart is decremented.|`commerce.productListRemovals`|

#### Data collected from removeFromCart

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`productListRemovals`|Indicates if a product was removed from the cart. A value of `1` indicates that a product was removed from the cart.|
|`productListItems`|An array of products removed from the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units removed from the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

### shoppingCartView

|Description| XDM event name|
|---|---|
|Triggered when any cart page loads.|`commerce.productListViews`|

#### Data collected from shoppingCartView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`productListViews`|Indicates if a product list was viewed|
|`productListItems`|An array of products in the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units in the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

### pageView

|Description| XDM event name|
|---|---|
|Triggered when any page loads.|`web.webpagedetails.pageViews`|

#### Data collected from pageView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`pageViews`|Indicates if a page was loaded. A `value` of `1` indicates that the page was loaded.|

### productPageView

|Description| XDM event name|
|---|---|
|Triggered when any product page loads.|`commerce.productViews`|

#### Data collected from productPageView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`productViews`|Indicates if the product was viewed|
|`productListItems`|An array of products in the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|

### startCheckout

|Description| XDM event name|
|---|---|
|Triggered when the shopper clicks a checkout button.|`commerce.checkouts`|

#### Data collected from startCheckout

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`checkouts`|Indicates if an action occurred during the checkout process|
|`productListItems`|An array of products in the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units in the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

### completeCheckout

|Description| XDM event name|
|---|---|
|Triggered when the shopper places an order.|`commerce.order`|

#### Data collected from completeCheckout

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`purchases`|Indicates if an order has been accepted|
|`order`|Contains information about the placed order for one or more products|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`orderType`|Indicates the type of order that was placed, such as Checkout or Instant Purchase|
|`payments`|The list of payments for this order|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this payment item. For example, `USD` or `EUR`.|
|`paymentAmount`|The value of the payment|
|`paymentType`|The method of payment for this order. Options are: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`|
|`transactionID`|The unique transaction identifier for this payment item|
|`shipping`|Shipping details for one or more products.|
|`shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on|
|`shippingAmount`|The total shipping cost for the items in the cart|
|`promotionID`|Unique identifier of the promotion, if any|
|`personalEmail`|Specifies the personal email address|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units in the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals.|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
+++

## Profile events

+++ Profile events include account information, such as `signIn`, `signOut`, `createAccount`, and `editAccount`. The data these events collect can be used to...

### signIn

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to sign in.|`userAccount.login`|

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful.

#### Data collected from signIn

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `userAccount.login`|
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`personalEmailID`|Specifies the unique identifier for the personal email|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`login`|Indicates if a visitor attempted to log in|

### signOut

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to sign out.|`userAccount.logout`|

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful.

#### Data collected from signOut

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `userAccount.logout`|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`logout`|Indicates if a visitor attempted to log out|

### createAccount

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to create an account.|`userAccount.createProfile`|

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful.

#### Data collected from createAccount

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `account.createProfile`|
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable|
|`personalEmailID`|Specifies the unique identifier for the personal email|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`createProfile`|Indicates if a user has created an account profile|

### editAccount

|Description| XDM event name|
|---|---|
|Triggered when a shopper attempts to edit an account.|`userAccount.updateProfile`|

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful.

#### Data collected from editAccount

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `account.updateProfile`|
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable|
|`personalEmailID`|Specifies the unique identifier for the personal email|
|`personalEmail`|Specifies the personal email address|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`updateProfile`|Indicates if a user has updated their account profile|
+++

## Search events

+++ The search events collected...

### searchRequestSent

|Description| XDM event name|
|---|---|
|Triggered by the following events in the “search as you type” popover:<br>Press Enter, Click _View All_<br>Triggered by the following events on search results pages:<br>Select a filter, Change the sort order (_Sort By_), Change the sort direction (ascending or descending), Change the number of results per page (_Show # per page_), Navigate to the next page, Navigate to the previous page, Navigate to a different page|`searchRequest`|

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B module installed.

#### Data collected from searchRequestSent

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchRequest`|Indicates if a search request was sent|
|`filter`|Indicates if any filters were applied to limit search results|
|`attribute` (filter)|The facet of an item used to determine whether to include it in search results|
|`value`|Attribute values used to determine which items are included in search results|
|`isRange`|When true, values indicate endpoints of an acceptable range of values|
|`sort`|Indicates how search results should be sorted|
|`attribute` (sort)|An attribute used to sort items in search results|
|`order`|The order in which to return search results|
|`query`|The terms searched for|

### searchResponseReceived

|Description| XDM event name|
|---|---|
|Triggered when Live Search returns results for the “search as you type” popover or search results page.|`searchResponse`|

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B module installed.

#### Data collected from searchResponseReceived

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchResponse`|Indicates if a search response has been received|
|`suggestions`|An array of strings that include the names of products and categories that exist in the catalog that are similar to the search query|
|`numberOfResults`|The number of products returned|
|`productListItems`|An array of products in the shopping cart.|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`productImageUrl`|Main image URL of the product|

+++

## (Beta) Order status events

+++ The order status events contain information about an order, such as if an order was placed, cancelled, refunded, or shipped.

### orderPlaced

|Description| XDM event name|
|---|---|
|Triggered when a shopper places an order.||

#### Data collected from orderPlaced

The following table describes the data collected for this event.
|Field|Description|
|---|---|

### orderCancelled

|Description| XDM event name|
|---|---|
|Triggered when ||

#### Data collected from orderCancelled

The following table describes the data collected for this event.
|Field|Description|
|---|---|

### orderRefunded

|Description| XDM event name|
|---|---|
|Triggered when ||

#### Data collected from orderRefunded

The following table describes the data collected for this event.
|Field|Description|
|---|---|

### orderShipped

|Description| XDM event name|
|---|---|
|Triggered when ||

#### Data collected from orderShipped

The following table describes the data collected for this event.
|Field|Description|
|---|---|
+++
