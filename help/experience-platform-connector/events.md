---
title: Events
description: Learn what data each event captures.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
---
# Experience Platform Connector Events

The following lists the Commerce events available when you install the Experience Platform connector extension. The data these events collect is sent to the Adobe Experience Platform edge. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

In addition to the data the following events collect, you also get [other data](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) provided by the Adobe Experience Platform Web SDK.

## Storefront events

The storefront events collect anonymized behavioral data from your shoppers as they browse your site. You can use the data these events collect to create promotions and campaigns targeted to a specific set of shoppers. Storefront event data includes simple and configurable products only.

>[!NOTE]
>
>All storefront events include the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which includes the shopper's email address, when available, and ECID. By including this profile data in each event, you do not need a separate user account import from Adobe Commerce.

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer's cart|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer's cart|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer's cart|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer's cart|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

### pageView

|Description| XDM event name|
|---|---|
|Triggered when any page loads.|`web.webpagedetails.pageViews`|

#### Data collected from pageView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`pageViews`|Indicates if a page was loaded. A `value` of `1` indicates that the page was loaded.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`cartID`|The unique ID that identifies the customer's cart|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
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
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

## Profile events

Profile events include account information, such as `signIn`, `signOut`, `createAccount`, and `editAccount`. This data is used to help populate key customer details that are needed to better define segments or execute marketing campaigns, such as if you want to target shoppers who live in New York.

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
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Captures contact details - an e-mail and associated information|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`login`|Indicates if a visitor attempted to log in|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`logout`|Indicates if a visitor attempted to log out|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Captures contact details - an e-mail and associated information|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`createProfile`|Indicates if a user has created an account profile|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`person`|An individual actor, contact, or owner|
|`accountID`|Captures the user account ID|
|`accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable|
|`personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`personalEmail`|Captures contact details - an e-mail and associated information|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences|
|`updateProfile`|Indicates if a user has updated their account profile|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

## Search events

The search events provide data relevant to the shopper's intent. Insight into a shopper's intent helps merchants see how shoppers are searching for items, what they click on, and ultimately purchase or abandon. An example of how you might use this data is if you want to target existing shoppers who search for your top product, but never purchase the product.

Use the `uniqueIdentifier` field found in both the `searchRequestSent` and `searchResponseReceived` events to cross reference a search request to the corresponding search response.

### searchRequestSent

|Description| XDM event name|
|---|---|
|Triggered by the following events in the "search as you type" popover:<br><br>Press Enter, Click _View All_<br><br>Triggered by the following events on search results pages:<br><br>Select a filter, Change the sort order (_Sort By_), Change the sort direction (ascending or descending), Change the number of results per page (_Show # per page_), Navigate to the next page, Navigate to the previous page, Navigate to a different page|`searchRequest`|

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B extension installed.

#### Data collected from searchRequestSent

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchRequest`|Indicates if a search request was sent|
|`id`| The unique ID for this particular search request|
|`filter`|Indicates if any filters were applied to limit search results|
|`attribute` (filter)|The facet of an item used to determine whether to include it in search results|
|`value`|Attribute values used to determine which items are included in search results|
|`isRange`|When true, values indicate endpoints of an acceptable range of values|
|`sort`|Indicates how search results should be sorted|
|`attribute` (sort)|An attribute used to sort items in search results|
|`order`|The order in which to return search results|
|`query`|The terms searched for|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

### searchResponseReceived

|Description| XDM event name|
|---|---|
|Triggered when Live Search returns results for the "search as you type" popover or search results page.|`searchResponse`|

>[!NOTE]
>
>Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B extension installed.

#### Data collected from searchResponseReceived

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`searchResponse`|Indicates if a search response has been received|
|`id`| The unique ID for this particular search response|
|`suggestions`|An array of strings that include the names of products and categories that exist in the catalog that are similar to the search query|
|`numberOfResults`|The number of products returned|
|`productListItems`|An array of products in the shopping cart.|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`name`|The display name or human-readable name of the product|
|`productImageUrl`|Main image URL of the product|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

## B2B events

![B2B for Adobe Commerce](../assets/b2b.svg) For B2B merchants, you must [install](install.md#install-the-b2b-extension) the `experience-platform-connector-b2b` extension to enable these events.

The B2B events contain [requisition list](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) information, such as if a requisition list was created, added to, or deleted from. By tracking events specific to requisition lists, you can see which products your customers purchase frequently and create campaigns based on that data.

### createRequisitionList

|Description| XDM event name|
|---|---|
|Triggered when a shopper creates a new requisition list.|`commerce.requisitionListOpens`|

#### Data collected from createRequisitionList

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`requisitionList`|The properties of requisition list created by customer|
|`ID`|Unique identifier of the requisition list|
|`name`|Name of the requisition list specified by the customer|
|`description`|Description of the requisition list specified by the customer|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

### addToRequisitionList

|Description| XDM event name|
|---|---|
|Triggered when a shopper adds a product to an existing requistion list or while creating a new list.|`commerce.requisitionListAdds`|

>[!NOTE]
>
>`addToRequisitionList` is not supported on category view pages or for configurable products. It is supported on product view pages and for simple products.

#### Data collected from addToRequisitionList

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`requisitionList`|The properties of requisition list created by customer|
|`ID`|Unique identifier of the requisition list|
|`name`|Name of the requisition list specified by the customer|
|`description`|Description of the requisition list specified by the customer|
|`productListItems`|An array of products that were added to the requisition list|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units added|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

### removeFromRequisitionList

|Description| XDM event name|
|---|---|
|Triggered when a shopper removes a product from a requisition list.|`commerce.requisitionListRemovals`|

#### Data collected from removeFromRequisitionList

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`requisitionList`|The properties of requisition list created by customer|
|`ID`|Unique identifier of the requisition list|
|`name`|Name of the requisition list specified by the customer|
|`description`|Description of the requisition list specified by the customer|
|`productListItems`|An array of products that were added to the requisition list|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units added|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|

## Back office events

The back office events contain information about the status of an order, such as if an order was placed, cancelled, refunded, shipped, or completed. The data that these server-side events collect shows a 360 view of the shopper order. This view helps merchants better target or analyze the entire order status when developing marketing campaigns. For example, you can spot trends in certain product categories that perform well at different times of the year. Such as, winter clothes that sell better during colder months or certain product colors that shoppers are interested in over the years. In addition, order status data can help you calculate lifetime customer value by understanding a shopper's propensity to convert based on previous orders.

>[!NOTE]
>
>All back office events include the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which provides the shopper's email address. By including this profile data in each event, you do not need a separate user account import from Adobe Commerce.

### orderPlaced

|Description| XDM event name|
|---|---|
|Triggered when a shopper places an order.|`commerce.backofficeOrderPlaced`|

#### Data collected from orderPlaced

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the order|
|`id`|The line item identifier for this product entry. The product itself is identified through the `product` field.|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units in the cart|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied to the item|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|
|`order`|Contains information about the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique|
|`priceTotal`|The total price of this order after all discounts and taxes have been applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract|
|`payments`|The list of payments for this order|
|`paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`paymentAmount`|The value of the payment|
|`taxAmount`|The tax amount paid by the buyer as part of the final payment|
|`discountAmount`|Indicates the discount amount applied to the whole order|
|`createdDate`|The time and date when a new order is created in the commerce system. For example, `2022-10-15T20:20:39+00:00`|
|`shipping`|Shipping details for one or more products|
|`shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on|
|`shippingAmount`|The amount the customer had to pay for shipping.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`address`|Physical shipping address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`billingAddress`|Billing postal address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address|
|`address`|The technical address, for example, 'name@domain.com' as commonly defined in RFC2822 and subsequent standards|

### orderItemsShipped

|Description| XDM event name|
|---|---|
|Triggered when an order is shipped.|`commerce.backofficeOrderItemsShipped`|

#### Data collected from orderItemsShipped

The following table describes the data collected for this event.
|Field|Description|
|---|---|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the order|
|`id`|The line item identifier for this product entry. The product itself is identified through the `product` field.|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units in the cart|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|
|`order`|Contains information about the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique|
|`priceTotal`|The total price of this order after all discounts and taxes have been applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract|
|`payments`|The list of payments for this order|
|`paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`paymentAmount`|The value of the payment|
|`lastUpdatedDate`|The time when a particular order record is last updated in the commerce system|
|`shipping`|Shipping details for one or more products|
|`shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`trackingNumber`|The tracking number provided by the shipping carrier for an order item shipment|
|`trackingURL`|The URL to track the shipping status of an order item|
|`shipDate`|The date when one or more items from an order is shipped|
|`address`|Physical shipping address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`shippingAmount`|The amount the customer had to pay for shipping.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`billingAddress`|Billing postal address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address|
|`address`|The technical address, for example, 'name@domain.com' as commonly defined in RFC2822 and subsequent standards|

### orderCancelled

|Description| XDM event name|
|---|---|
|Triggered when a shopper cancels an order.|`commerce.backofficeOrderCancelled`|

#### Data collected from orderCancelled

The following table describes the data collected for this event.
|Field|Description|
|---|---|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the order|
|`id`|The line item identifier for this product entry. The product itself is identified through the `product` field.|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units in the cart|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`storeCode`|The unique store code. You can have many stores per website.|
|`storeViewCode`|The unique store view code. You can have many store views per store.|
|`websiteCode`|The unique website code. You can have many websites in an environment.|
|`order`|Contains information about the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique|
|`purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract|
|`cancelDate`|The date and time when a shopper cancels an order|
|`lastUpdatedDate`|The time when a particular order record is last updated in the commerce system|
|`personalEmail`|A personal email address|
|`address`|The technical address, for example, 'name@domain.com' as commonly defined in RFC2822 and subsequent standards|

### creditMemoIssued

|Description| XDM event name|
|---|---|
|Triggered when a shopper returns an item in an order.|`commerce.backofficeCreditMemoIssued`|

#### Data collected from creditMemoIssued

The following table describes the data collected for this event.
|Field|Description|
|---|---|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the order|
|`id`|The line item identifier for this product entry. The product itself is identified through the `product` field.|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units in the cart|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`order`|Contains information about the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique|
|`purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract|
|`lastUpdatedDate`|The time when a particular order record is last updated in the commerce system|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`taxAmount`|The tax amount paid by the buyer as part of the final payment.|
|`refunds`|The list of refunds for this order|
|`refundPaymentType`|The method of payment for this order. Enumerated, custom values allowed.|
|`refundAmount`|The value of the refund.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`personalEmail`|A personal email address|
|`address`|The technical address, for example, 'name@domain.com' as commonly defined in RFC2822 and subsequent standards|

### orderShipmentCompleted

|Description| XDM event name|
|---|---|
|Triggered when a shopper returns an item in an order.|`commerce.backofficeOrderShipmentCompleted`|

#### Data collected from orderShipmentCompleted

The following table describes the data collected for this event.
|Field|Description|
|---|---|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`productListItems`|An array of products in the order|
|`id`|The line item identifier for this product entry. The product itself is identified through the `product` field.|
|`name`|The display name or human-readable name of the product|
|`SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`quantity`|The number of product units in the cart|
|`priceTotal`|The total price for the product line item|
|`discountAmount`|Indicates the discount amount applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`productImageUrl`|Main image URL of the product|
|`selectedOptions`|Field used for a configurable product.|
|`attribute`|Identifies an attribute of the configurable product, such as `size` or `color`|
|`value`|Identifies the value of the attribute such as `small` or `black`.|
|`order`|Contains information about the order|
|`purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique|
|`priceTotal`|The total price of this order after all discounts and taxes have been applied|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for the order totals|
|`purchaseOrderNumber`|Unique identifier assigned by the purchaser for this purchase or contract|
|`taxAmount`|The tax amount paid by the buyer as part of the final payment.|
|`createdDate`|The time and date when a new order is created in the commerce system. For example, `2022-10-15T20:20:39+00:00`|
|`payments`|The list of payments for this order|
|`paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`paymentAmount`|The value of the payment|
|`shipping`|Shipping details for one or more products|
|`shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on|
|`address`|Physical shipping address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this will only contain part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`shippingAmount`|The amount the customer had to pay for shipping.|
|`currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used for this shipping cost|
|`address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards|
|`billingAddress`|Billing postal address|
|`street1`|Primary street level information, apartment number, street number, and street name|
|`street2`|Additional field for street level information|
|`city`|The name of the city|
|`state`|The name of the state. This is a free-form field.|
|`postalCode`|The postal code of the location. Postal codes are not available for all countries. In some countries, this data contains only part of the postal code.|
|`country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`personalEmail`|A personal email address|
|`address`|The technical address, for example, 'name@domain.com' as commonly defined in RFC2822 and subsequent standards|
