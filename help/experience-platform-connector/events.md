---
title: Events
description: Learn what data each event captures.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
---
# Experience Platform Connector Events

The following lists the Commerce events available when you install the Experience Platform connector extension. The data these events collect is sent to the Adobe Experience Platform edge. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

In addition to the data the following events collect, you also get [other data](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) provided by the Adobe Experience Platform Web SDK.

>[!NOTE]
>
>All storefront events include the `personID` field, which is a unique identifier of the person.

## addToCart

Triggered when a product is added to the cart or when the quantity of a product in the cart is incremented.

### XDM event name

`commerce.productListAdds`

### Type

Storefront

### Data collected

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

## openCart

Triggered when a new cart is created, which is when a product is added to an empty cart.

### XDM event name

`commerce.productListOpens`

### Type

Storefront

### Data collected

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

## removeFromCart

Triggered every time a product is removed or every time the quantity of a product in the cart is decremented.

### XDM event name

`commerce.productListRemovals`

### Type

Storefront

### Data collected

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

## shoppingCartView

Triggered when any cart page loads.

### XDM event name

`commerce.productListViews`

### Type

Storefront

### Data collected

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

## pageView

Triggered when any page loads.

### XDM event name

`web.webpagedetails.pageViews`

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`pageViews`|Indicates if a page was loaded. A `value` of `1` indicates that the page was loaded.|

## productPageView

Triggered when any product page loads.

### XDM event name

`commerce.productViews`

### Type

Storefront

### Data collected

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

## startCheckout

Triggered when the shopper clicks a checkout button.

### XDM event name

`commerce.checkouts`

### Type

Storefront

### Data collected

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

## completeCheckout

Triggered when the shopper places an order.

### XDM event name

`commerce.order`

### Type

Storefront

### Data collected

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
|`productListItems`|An array of products in the shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`priceTotal`|The total price for the product line item|
|`quantity`|The number of product units in the cart|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals.|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|

## signIn

Triggered when a shopper attempts to sign in.

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### XDM event name

`userAccount.login`

### Type

Profile

### Data collected

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

## signOut

Triggered when a shopper attempts to sign out.

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### XDM event name

`userAccount.logout`

### Type

Profile

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `userAccount.logout`|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`logout`|Indicates if a visitor attempted to log out|

## createAccount

Triggered when a shopper attempts to create an account.

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### XDM event name

`userAccount.createProfile`

### Type

Profile

### Data collected

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

## editAccount

Triggered when a shopper attempts to edit an account.

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### XDM event name

`userAccount.updateProfile`

### Type

Profile

### Data collected

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

## searchRequestSent

Triggered by the following events in the “search as you type” popover:

- Press Enter
- Click _View All_

Triggered by the following events on search results pages:

- Select a filter
- Change the sort order (_Sort By_)
- Change the sort direction (ascending or descending)
- Change the number of results per page (_Show # per page_)
- Navigate to the next page
- Navigate to the previous page
- Navigate to a different page

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B module installed.

### XDM event name

`searchRequest`

### Type

Search

### Data collected

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

## searchResponseReceived

Triggered when Live Search returns results for the “search as you type” popover or search results page.

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B module installed.

### XDM event name

`searchResponse`

### Type

Search

### Data collected

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
