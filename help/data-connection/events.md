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
|`commerce.productListAdds`|Indicates if a product was added to a shopping cart. A value of `1` indicates that a product was added.|
|`commerce.cart.cartID`|The unique ID that identifies the customer's cart.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### openCart

|Description| XDM event name|
|---|---|
|Triggered when a new cart is created, which is when a product is added to an empty cart.|`commerce.productListOpens`|

#### Data collected from openCart

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.productListOpens`|Indicates if a cart was created. A value of `1` indicates that a cart was created.|
|`commerce.cart.cartID`|The unique ID that identifies the customer's cart.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### removeFromCart

|Description| XDM event name|
|---|---|
|Triggered every time a product is removed or every time the quantity of a product in the cart is decremented.|`commerce.productListRemovals`|

#### Data collected from removeFromCart

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.productListRemovals`|Indicates if a product was removed from the cart. A value of `1` indicates that a product was removed from the cart.|
|`commerce.cart.cartID`|The unique ID that identifies the customer's cart.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### shoppingCartView

|Description| XDM event name|
|---|---|
|Triggered when any cart page loads.|`commerce.productListViews`|

#### Data collected from shoppingCartView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.productListViews`|Indicates if a product list was viewed.|
|`commerce.cart.cartID`|The unique ID that identifies the customer's cart.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### pageView

|Description| XDM event name|
|---|---|
|Triggered when any page loads.|`web.webpagedetails.pageViews`|

#### Data collected from pageView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`web.webPageDetails.pageViews`|Indicates if a page was loaded. A `value` of `1` indicates that the page was loaded.|
|`web.webPageDetails.URL`|The normative or usual URL of the web page. This can be the actual URL used to reach the page, which would be recorded using `Web Link`.|
|`web.webPageDetails.name`|The normative name of the web page. This name is not necessarily the page title or directly associate with page content, but is used to organize a site's pages for classification purposes.|
|`web.webReferrer.URL`|The URL of the webpage a shopper visited before clicking a link to your site.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

### productPageView

|Description| XDM event name|
|---|---|
|Triggered when any product page loads.|`commerce.productViews`|

#### Data collected from productPageView

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.productViews`|Indicates if the product was viewed.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### startCheckout

|Description| XDM event name|
|---|---|
|Triggered when the shopper clicks a checkout button.|`commerce.checkouts`|

#### Data collected from startCheckout

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.checkouts`|Indicates if an action occurred during the checkout process.|
|`commerce.cart.cartID`|The unique ID that identifies the customer's cart.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### completeCheckout

|Description| XDM event name|
|---|---|
|Triggered when the shopper places an order.|`commerce.order`|

#### Data collected from completeCheckout

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.purchases`|Indicates if an order has been accepted.|
|`commerce.order`|Contains information about the placed order for one or more products.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.paymentTransactionID`|Unique identifier for this payment transaction.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Options are: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`.|
|`commerce.order.payments.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.order.taxAmount`|The tax amount paid by the buyer as part of the final payment.|
|`commerce.order.discountAmount`|Indicates the discount amount applied to the whole order.|
|`commerce.order.createdDate`|The time and date when a new order is created in the commerce system. For example, `2022-10-15T20:20:39+00:00`.|
|`commerce.shipping`|Shipping details for one or more products.|
|`commerce.shipping.shippingMethod`|The method of shipping chosen by the customer, such as standard delivery, expedited delivery, pick up in store, and so on.|
|`commerce.shipping.shippingAmount`|The amount the customer had to pay for shipping.||`shipping`|Shipping details for one or more products.|
|`commerce.shipping.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

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
|`person`|An individual actor, contact, or owner.|
|`person.accountID`|Captures the user account ID.|
|`person.accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable.|
|`person.personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`personalEmail`|Captures contact details - an e-mail and associated information.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.login`|Indicates if a visitor attempted to log in.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.logout`|Indicates if a visitor attempted to log out.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`person`|An individual actor, contact, or owner.|
|`person.accountID`|Captures the user account ID.|
|`person.accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable.|
|`person.personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`personalEmail`|Captures contact details - an e-mail and associated information.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.updateProfile`|Indicates if a user has updated their account profile.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`person`|An individual actor, contact, or owner.|
|`person.accountID`|Captures the user account ID.|
|`person.accountType`|Captures the user account type, such as `Personal` or `Company`, if applicable.|
|`person.personalEmailID`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`personalEmail`|Captures contact details - an e-mail and associated information.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`userAccount`|Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.updateProfile`|Indicates if a user has updated their account profile.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

## Search events

The search events provide data relevant to the shopper's intent. Insight into a shopper's intent helps merchants see how shoppers are searching for items, what they click on, and ultimately purchase or abandon. An example of how you might use this data is if you want to target existing shoppers who search for your top product, but never purchase the product.

Use the `searchRequest.id` and `searchResponse.id` fields found in both the `searchRequestSent` and `searchResponseReceived` events to cross reference a search request to the corresponding search response.

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
|`searchRequest`|Indicates if a search request was sent.|
|`searchRequest.id`|The unique ID for this particular search request.|
|`searchRequest.value`|The quantifiable value of the request.|
|`siteSearch`|Contains information about the search.|
|`siteSearch.filter`|Indicates if any filters were applied to limit search results.|
|`siteSearch.filter.attribute` (filter)|The facet of an item used to determine whether to include it in search results.|
|`siteSearch.filter.isRange`|When true, values indicate endpoints of an acceptable range of values.|
|`siteSearch.filter.value`|Attribute value used to determine which items are included in search results.|
|`siteSearch.sort`|Indicates how search results should be sorted.|
|`siteSearch.sort.attribute` (sort)|An attribute used to sort items in search results.|
|`siteSearch.sort.order`|The order in which to return search results.|
|`siteSearch.query`|The terms searched for.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`searchResponse`|Indicates if a search response has been received.|
|`searchResponse.id`|The unique ID for this particular search response.|
|`searchResponse.value`|The quantifiable value of the response.|
|`siteSearch.numberOfResults`|The number of products returned.|
|`siteSearch.suggestions`|An array of strings that include the names of products and categories that exist in the catalog that are similar to the search query.|
|`productListItems`|An array of products that were added to the shopping cart.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.productImageUrl`|Main image URL of the product.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

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
|`commerce.requisitionListOpens`|Indicates initialization of a new requisition list.|
|`commerce.requisitionList`|The properties of requisition list created by customer.|
|`commerce.requisitionList.ID`|Unique identifier of the requisition list.|
|`commerce.requisitionList.name`|Name of the requisition list specified by the customer.|
|`commerce.requisitionList.description`|Description of the requisition list specified by the customer.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|

### addToRequisitionList

|Description| XDM event name|
|---|---|
|Triggered when a shopper adds a product to an existing requistion list or while creating a new list.|`commerce.requisitionListAdds`|

#### Data collected from addToRequisitionList

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.requisitionListAdds`|Indicates addition of one or more products to a requisition list.|
|`commerce.requisitionList`|The properties of requisition list created by customer.|
|`commerce.requisitionList.ID`|Unique identifier of the requisition list.|
|`commerce.requisitionList.name`|Name of the requisition list specified by the customer.|
|`commerce.requisitionList.description`|Description of the requisition list specified by the customer.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the requisition list.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

### removeFromRequisitionList

|Description| XDM event name|
|---|---|
|Triggered when a shopper removes a product from a requisition list.|`commerce.requisitionListRemovals`|

#### Data collected from removeFromRequisitionList

The following table describes the data collected for this event.

|Field|Description|
|---|---|
|`commerce.requsitionListRemovals`|Indicates removal of one or more products from a requisition list.|
|`commerce.requisitionList`|The properties of requisition list created by customer.|
|`commerce.requisitionList.ID`|Unique identifier of the requisition list.|
|`commerce.requisitionList.name`|Name of the requisition list specified by the customer.|
|`commerce.requisitionList.description`|Description of the requisition list specified by the customer.|
|`commerce.commerceScope`|Indicates where an event occurred (store view, store, website, and so on).|
|`commerce.commerceScope.environmentID`|The environment ID. A 32-digit alphanumeric ID separated by hyphens.|
|`commerce.commerceScope.storeCode`|The unique store code. You can have many stores per website.|
|`commerce.commerceScope.storeViewCode`|The unique store view code. You can have many store views per store.|
|`commerce.commerceScope.websiteCode`|The unique website code. You can have many websites in an environment.|
|`productListItems`|An array of products that were added to the requisition list.|
|`productListItems.SKU`|Stock Keeping Unit. The unique identifier for the product.|
|`productListItems.name`|The display name or human-readable name of the product.|
|`productListItems.priceTotal`|The total price for the product line item.|
|`productListItems.quantity`|The number of product units in the cart.|
|`productListItems.discountAmount`|Indicates the discount amount applied.|
|`productListItems.currencyCode`|The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency code used, such as `USD` or `EUR`.|
|`productListItems.selectedOptions`|Field used for a configurable product.|
|`productListItems.selectedOptions.attribute`|Identifies an attribute of the configurable product, such as `size` or `color`.|
|`productListItems.selectedOptions.value`|Identifies the value of the attribute such as `small` or `black`.|

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
|`commerce.order`|Contains information about the order.|
|`commerce.order.purchaseID`|Unique identifier assigned by the seller for this purchase or contract. There is no guarantee that the ID is unique.|
|`commerce.order.payments`|The list of payments for this order.|
|`commerce.order.payments.paymentTransactionID`|Unique identifier for this payment transaction.|
|`commerce.order.payments.paymentAmount`|The value of the payment.|
|`commerce.order.payments.paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
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
|`commerce.order.payments.paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
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
|`commerce.order.payments.paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
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
|`commerce.refunds.refundPaymentType`|The method of payment for this order. Enumerated, custom values allowed.|
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
|`commerce.order.returns.returnStatus`|The current status of the RMA (Return Merchandise Authorization), such as Pending, Closed, and so on.|
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
|`commerce.order.returns.returnStatus`|The current status of the RMA (Return Merchandise Authorization), such as Pending, Closed, and so on.|
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
|`commerce.order.payments.paymentType`|The method of payment for this order. Enumerated, custom values allowed.|
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
