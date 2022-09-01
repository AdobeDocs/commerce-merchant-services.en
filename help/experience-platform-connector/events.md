---
title: Events
description: Learn which events capture data and see the full schema definition.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
---
# Experience Platform Connector Events

The following lists the Commerce events available when you install the Experience Platform connector extension. The data these events collect is sent to the Adobe Experience Platform edge. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

In addition to the data the following events collect, you also get [additional data](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) provided by the Adobe Experience Platform Web SDK.

## Add to Cart

Triggered when a product is added to the cart or when the quantity of a product in the cart is incremented. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce`|Identifies the type of content for this event|
|`productListAdds`|Indicates if a product was added to a shopping cart. A value of `1` indicates that a product was added.|
|`productListItems`|An array products added to a shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product.|
|`priceTotal`|The total for this order after all discounts and taxes have been applied.|
|`quantity`|The number of units the customer has indicated they require of the product.|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product.|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

## View Shopping Cart

Triggered when any cart page loads. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce`|Identifies the type of content for this event|
|`productListViews`|Indicates if a product list was viewed|
|`productListItems`|An array products added to a shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product.|
|`priceTotal`|The total for this order after all discounts and taxes have been applied.|
|`quantity`|The number of units the customer has indicated they require of the product.|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product.|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

## View Page

Triggered when any page loads. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`pageViews`|Indicates if a page was loaded. A `value` of `1` indicates that the page was loaded.|

## View Product

Triggered when any product page loads. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce`|Identifies the type of content for this event|
|`productViews`|Indicates if the product was viewed|
|`productListItems`|An array products added to a shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product.|
|`priceTotal`|The total for this order after all discounts and taxes have been applied.|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product.|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|

## Start Checkout

Triggered when the shopper clicks a checkout button. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce`|Identifies the type of content for this event|
|`checkouts`|Indicates if an action occurred during the checkout process|
|`productListItems`|An array products added to a shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product.|
|`priceTotal`|The total for this order after all discounts and taxes have been applied.|
|`quantity`|The number of units the customer has indicated they require of the product.|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product.|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer’s cart|

## Complete Checkout

Triggered when the shopper places an order. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts).

### Type

Storefront

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce`|Identifies the type of content for this event|
|`purchases`|Indicates if an order has been accepted|
|`order`|The unique identifier that identifies the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`orderType`|Indicates the type of order that was placed, such as checkout or instant purchase|
|`paymentTransactionID`|The unique transaction identifier for this payment item|
|`paymentAmount`|The value of the payment|
|`paymentType`|The method of payment for this order. Options are: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`|
|`paymentCurrencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this payment item. For example, `USD` or `EUR`.|
|`shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on|
|`shippingAmount`|The total shipping cost for the items in the cart|
|`promotionID`|Unique identifier of the promotion, if any|
|`productListItems`|An array products added to a shopping cart|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product.|
|`priceTotal`|The total for this order after all discounts and taxes have been applied.|
|`quantity`|The number of units the customer has indicated they require of the product.|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency for the product. For example, `USD` or `EUR`.|
|`selectedOptions`|Field used for a configurable product. `attribute` identifies an attribute of the configurable product, such as `size` or `color` and `value` identifies the value of the attribute such as `small` or `black`.|

## Sign In

Triggered when a shopper attempts to sign in. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts).

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### Type

Profile

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `userAccount.login`|
|`person`|Contains information about the person|
|`accountID`|???|
|`accountType`|???|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Specifies the personal email address|
|`address`|???|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`login`|Indicates if a visitor attempted to login.|
|`personID`|Unique identifier of the person|

## Sign Out

Triggered when a shopper attempts to sign out. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts).

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### Type

Profile

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `userAccount.logout`|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`logout`|Indicates if a visitor attempted to logout|
|`personID`|Unique identifier of the person|

## Create Account

Triggered when a shopper attempts to create an account. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts).

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### Type

Profile

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `account.createProfile`|
|`person`|???|
|`accountID`|???|
|`accountType`|???|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Specifies the personal email address|
|`address`|???|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`createProfile`|Indicates if a user has created an account profile|
|`personID`|Unique identifier of the person|

## Edit Account

Triggered when a shopper attempts to edit an account. [Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts).

>[!NOTE]
>
> This event is triggered when the specific action is attempted. It does not indicate that the action was successful. 

### Type

Profile

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`eventType`|The primary event type for this time-series record, such as: `account.updateProfile`|
|`person`|???|
|`accountID`|???|
|`accountType`|???|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Specifies the personal email address|
|`address`|???|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`updateProfile`|Indicates if a user has updated their account profile|
|`personID`|Unique identifier of the person|

## Search Request Sent

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

[Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts).


"Also for docs we need to note that this will not work OOTB for any nonAdobe Commerce extension"


### Type

Search

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchRequest`|Indicates if a search request was sent|
|`siteSearch`|Contains site search related information such as search query, filtering, and ordering.|
|`filter`|Indicates if any filters were applied to limit search results|
|`attribute`|The facet of an item used to determine whether to include it in search results|
|`value`|Attribute values used to determine which items will be included in search results|
|`isRange`|When true, values indicate endpoints of an acceptable range of values|
|`sort`|Indicates how search results should be sorted|
|`attribute`|An attribute used to sort items in search results|
|`order`|The order in which to return search results|
|`query`|The terms searched for|

## Search Response Received

Triggered when Live Search returns results for the “search as you type” popover or search results page.

[Full schema](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)

### Type

Search

### Data collected

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchResponse`|Indicates if a search response has been received|
> |`siteSearch`|Contains site search related information such as search query, filtering, and ordering.|
|`suggestions`|An array of strings that include the names of products and categories that exist in the catalog that are similar to the search query.|
|`numberOfResults`|The number of products returned.|
|`productListItems`|An array of products added to a shopping cart. Includes the `SKU`(Stock Keeping Unit) and `name` of the product (display name or human-readable name.)|
