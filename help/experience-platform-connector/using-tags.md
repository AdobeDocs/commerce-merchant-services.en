---
title: Collect Commerce Data using Adobe Experience Platform Tags
description: Learn how to collect Commerce data using Adobe Experience Platform tags.
exl-id: 852fc7d2-5a5f-4b09-8949-e9607a928b44
---
# Collect Commerce Data using Adobe Experience Platform Tags

While you can use the Experience Platform connector to publish and subscribe to storefront events, some merchants might already be using a data collection solution, such as the [Adobe Experience Platform tags](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en). For those merchants, Adobe Commerce provides a publishing only option in the Experience Platform connector that uses the Adobe Commerce Event SDK.

![Experience Platform Connector Data Flow](assets/tags-data-flow.png)
_Experience Platform Connector Data Flow with Tags_

In this topic, you will learn how to map the storefront event values provided by the Experience Platform connector to the Adobe Experience Platform tags solution you are already using.

## Collect event data from Adobe Commerce

To collect Commerce event data:

- Install the [Adobe Commerce Events SDK](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-sdk). For PHP storefronts, see the [install](install.md) topic. For PWA Studio storefronts, see the [PWA Studio guide](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

    >[!NOTE]
    >
    > Do **not** [configure](connect-data.md) the Organization ID and Datastream ID.

## Map Commerce storefront data to Adobe Experience Platform

To map Commerce storefront data to Adobe Experience Platform, configure and install the following from within Adobe Experience Platform tags:

1. [Set up a tag property](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) in Adobe Experience Platform Data Collection.

1. Under **Authoring**, select **Extensions** and install and configure the following extensions:

   - [Adobe Client Data Layer](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [Publish tag](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) to your development environment.

1. Follow the **Event Mapping** steps below to configure data elements and rules for specific events.

### Event mapping

Because data collection using tags is different from using the Adobe Commerce Event SDK, it is important to understand the equivalent terms used in both frameworks.

|Adobe Experience Platform tags term|Adobe Commerce Event SDK term|
|---|---|
|_data elements_|context|
|_rules_|event|
||_rule conditions_ - event listeners (from ACDL)<br><br>_rule actions_ - event handlers (send to Adobe Experience Platform)|

When you update the data elements and rules in Adobe Experience Platform tags with Adobe Commerce-specific event data, there are some common steps you will take.

For example, let's add the Adobe Commerce `signOut` event to Adobe Experience Platform tags. The steps outlined below, except for specific values you set, describe how to add [data elements](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) and [rules](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule), which apply to all Adobe Commerce events you are adding to tags.

1. Create a Data Element:

    ![Create New Data Element](assets/create-new-data-elements.png)
    _Create New Data Element_

1. Set **Name** to `sign out`.

1. Set **Extension** to `Adobe Experience Platform Web SDK`.

1. Set **Data Element Type** to `XDM object`.

1. Select the **Sandbox** and **Schema** that you want to update.

1. Under **userAccount** > **logout**, set the **value** in **Visitor Logout** to `1`.

     ![Update Sign out value](assets/signout-value.png)
    _Update Sign out value_

1. Select **Save**.

1. Create a Rule:

    ![Create New Rule](assets/create-new-rule.png)
    _Create New Rule_

1. Select **Add** under **EVENTS**.

1. Set **Extension** to `Adobe Client Data Layer`.

1. Set **Event Type** to `Data Pushed`.

1. Select **Specific Event** and set the **Event/Key to register for** to `sign-out`.

1. Select **Keep Changes** to save the new rule.

1. Add an action.

1. Set **Extension** to `Adobe Experience Platform Web SDK`.

1. Set **Action Type** to `Send Event`.

1. Set **Instance** to `Alloy`.

1. Set **Type** to `userAccount.logout`.

1. Set **XDM data** to `%sign out%`.

1. Click **Save**.

    You created a data element in your schema for the `signOut` event from Adobe Commerce. Also, you created a rule with a specific action that should occur when that event is fired from the Adobe Commerce storefront.

Repeat the above steps in tags for each of the Adobe Commerce events described below.

### Available events

For each of the following events, map the Adobe Commerce events to your XDM by following the above steps.

- [`signOut`](#signout)
- [`signIn`](#signin)
- [`createAccount`](#createaccount)
- [`editAccount`](#editaccount)
- [`pageView`](#pageview)
- [`productView`](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [`viewCart`](#viewcart)
- [`removeFromCart`](#removefromcart)
- [`initiateCheckout`](#initiatecheckout)
- [`placeOrder`](#placeorder)

### signOut {#signout}

#### Data Elements

Create the following data element:

1. Sign out:

    - **Name**: `Sign out`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `userAccount` > `logout`
    - **Visitor Logout**: **Value** = `1`

#### Rules 

- **Name**: `Sign out`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `sign-out`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `userAccount.logout`
- **XDM data**: `%sign-out%`

### signIn {#signin}

#### Data Elements

Create the following data elements:

1. Account email:

    - **Name**: `account email`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.emailAddress`

1. Account type:

    - **Name**: `account type`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.accountType`

1. Account ID:

    - **Name**: `account id`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path***: `accountContext.accountId`

1. Sign in:

    - **Name**: `sign in`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `person` > `accountID`
    - **Account ID**: **Value** = `%account id%`
    - **Field Group**: `person` > `accountType`
    - **Account Type**: **Value** = `%account type%`
    - **Field Group**: `person` > `personalEmailID`
    - **Personal Email Address**: **Value** = `%account email%`
    - **Field Group**: `personalEmail` > `address`
    - **Address**: **Value** = `%account email%`
    - **Field Group**: `userAccount` > `login`
    - **Visitor Login**: **Value** = `1`

#### Rules 

- **Name**: `sign in`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `sign-in`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `userAccount.login`
- **XDM data**: `%sign in%`

### createAccount {#createaccount}

#### Data Elements

Create the following data elements:

1. Account email:

    - **Name**: `account email`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.emailAddress`

1. Account type:

    - **Name**: `account type`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.accountType`

1. Account ID:

    - **Name**: `account id`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.accountId`

1.  Create account:

    - **Name**: `Create account`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `person` > `accountID`
    - **Account ID**: **Value** = `%account id%`
    - **Field Group**: `person` > `accountType`
    - **Account Type**: **Value** = `%account type%`
    - **Field Group**: `person` > `personalEmailID`
    - **Personal Email Address**: **Value** = `%account email%`
    - **Field Group**: `personalEmail` > `address`
    - **Address**: **Value** = `%account email%`
    - **Field Group**: `userAccount` > `createProfile`
    - **Account Profile Create**: **Value** = `1`

#### Rules 

- **Name**: `Create account`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `create-account`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `userAccount.createProfile`
- **XDM data**: `%create account%`

### editAccount {#editaccount}

#### Data Elements

Create the following data elements:

1. Account email:

    - **Name**: `account email`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.emailAddress`

1. Account type:

    - **Name**: `account type`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.accountType`

1. Account ID:

    - **Name**: `account id`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `accountContext.accountId`

1. Edit account:

    - **Name**: `Edit account`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `person` > `accountID`
    - **Account ID**: **Value** = `%account id%`
    - **Field Group**: `person` > `accountType`
    - **Account Type**: **Value** = `%account type%`
    - **Field Group**: `person` > `personalEmailID`
    - **Personal Email Address**: **Value** = `%account email%`
    - **Field Group**: `personalEmail` > `address`
    - **Address**: **Value** = `%account email%`
    - **Field Group**: `userAccount` > `updateProfile`
    - **Account Profile Create**: **Value** = `1`

#### Rules

- **Name**: `Edit account`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `edit-account`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `userAccount.updateProfile`
- **XDM data**: `%edit account%`

### pageView {#pageview}

#### Data Elements

Create the following data elements:

1. Page name:

    - **Name**: `page name`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `pageContext.pageName`

#### Rules 

- **Name**: `page view`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `page-view`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `web.webPageDetails.pageViews`
- **XDM data**: `%page view%`

### productView {#productview}

#### Data Elements

Create the following data elements:
  
1. Product name:

    - **Name**: `product name`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.name`

1. Product SKU:

    - **Name**: `product sku`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.sku`

1. Product currency:

    - **Name**: `product currency`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.currencyCode`

1. Currency code:

    - **Name**: `currency code`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('product currency') || _satellite.getVar('storefront').storeViewCurrencyCode
    ```

1. Special price:

    - **Name**: `special price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.specialPrice`

1. Regular price:

    - **Name**: `regular price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.regularPrice`

1. Product price:

    - **Name**: `product price`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('product regular price') || _satellite.getVar('product special price')
    ```

1. Product view:

    - **Name**: `product view`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. Select **Provide individual items** and click the **Add item** button. Because this view is for a PDP, you can populate with a single item.
    - **Field Group**: `productListItems` > `name`
    - **Name**: **Value** = `%product name%`
    - **Field Group**: `productListItems` > `SKU`
    - **SKU**: **Value** = `%product sku%`
    - **Field Group**: `productListItems` > `priceTotal`
    - **Price total**: **Value** = `%product price%`
    - **Field Group**: `productListItems` > `currencyCode`
    - **Currency code**: **Value** = `%currency code%`
    - **Field Group**: `commerce` > `productViews` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `product view`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `product-page-view`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.productViews`
- **XDM data**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### Data Elements

Create the following data elements:

1. Search input

    - **Name**: `search input`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `searchInputContext.units[0]`

1. Search input phrase

    - **Name**: `search input phrase`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('search input').phrase;
    ```

1. Search input sort

    - **Name**: `search input sort`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    const searchInput = _satellite.getVar('search input');
    const sortFromInput = searchInput ? searchInput.sort : [];
    const sort = sortFromInput.map((searchSort) => {
        return {
            attribute: searchSort.attribute,
            order: searchSort.direction,
        };
    });
    return sort;
    ```

1. Search input filters

    - **Name**: `search input filters`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash

    const searchInput = _satellite.getVar('search input');
    const filtersFromInput = searchInput ? searchInput.filter : [];
    const filters = filtersFromInput.map(
        (searchFilter) => {
            let value = [];
            let isRange = false;
            if (searchFilter.eq) {
                value.push(searchFilter.eq);
            } else if (searchFilter.in) {
                value = searchFilter.in;
            } else if (searchFilter.range) {
                isRange = true;
                value.push(String(searchFilter.range.from));
                value.push(String(searchFilter.range.to));
            }
            return {
                attribute: searchFilter.attribute,
                value,
                isRange,
            };
        }
    );
    
    return filters;
    ```

1. Search request:   

    - **Name**: `search request`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `siteSearch` > `phrase`
    - **value**: Not yet available
    - **Field Group**: `siteSearch` > `sort`. Select **Provide entire object**.
    - **Field Group**: `siteSearch` > `filter`. Select **Provide entire object**.
    - **Field Group**: `searchRequest` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `search request sent`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `search-request-sent`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `searchRequest`
- **XDM data**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### Data Elements

Create the following data elements:

1. Search results:

    - **Name**: `search results`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `searchResultsContext.units[0]`

1. Search result number of products:

    - **Name**: `search result number of products`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    return _satellite.getVar('search result').products.length;
    ```

1. Search result products:

    - **Name**: `search result products`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const searchResult = _satellite.getVar('search result');
    const productsFromResult = searchResult.products ? searchResult.products : [];
    const products = productsFromResult.map(
        (product) => {
            return { SKU: product.sku, name: product.name };
        }
    );
    return products;
    ```

1. Search result suggestions:

    - **Name**: `search result products`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const searchResult = _satellite.getVar('search result');
    const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
    const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
    return suggestions;
    ```

1. Search response:

    - **Name**: `search response`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `siteSearch` > `suggestions`. Select **Provide entire object**.
    - **Data element**: `%search result suggestions%`
    - **Field Group**: `siteSearch` > `numberOfResults`
    - **value**: `%search result number of products%`
    - **Field Group**: `productListItems`. Select **Provide entire object**.
    - **Data element**: `%search result products%`
    - **Field Group**: `searchResponse` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `search response received`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `search-response-received`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `searchResponse`
- **XDM data**: `%search response%`

### addToCart {#addtocart}

#### Data Elements

Create the following data elements:

1. Product name:

    - **Name**: `product name`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.name`

1. Product sku:

    - **Name**: `product sku`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.sku`

1. Currency code:

    - **Name**: `currency code`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.currencyCode`

1. Product special price:

    - **Name**: `product special price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.specialPrice`

1. Product regular price:

    - **Name**: `product regular price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.regularPrice`

1. Product  price:

    - **Name**: `product price`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
    ```

1. Cart:

    - **Name**: `cart`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `shoppingCartContext`

1. Cart id:

    - **Name**: `cart id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('cart').id
    ```

1. Add to cart:

    - **Name**: `add to cart`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. Select **Provide individual items** and click the **Add item** button. Because this view is for a PDP, you can populate with a single item.
    - **Field Group**: `productListItems` > `name`
    - **Name**: **Value** = `%product name%`
    - **Field Group**: `productListItems` > `SKU`
    - **SKU**: **Value** = `%product sku%`
    - **Field Group**: `productListItems` > `priceTotal`
    - **Price total**: **Value** = `%product price%`
    - **Field Group**: `productListItems` > `currencyCode`
    - **Currency code**: **Value** = `%currency code%`
    - **Field Group**: `commerce` > `cart` > `cartID`
    - **Cart ID**: **Value** = `%cart id%`
    - **Field Group**: `commerce` > `productListAdds` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `add to cart`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `add-to-cart`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.productListAdds`
- **XDM data**: `%add to cart%`

### viewCart {#viewcart}

#### Data Elements

Create the following data elements:

1. Storefront:

    - **Name**: `storefront`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `storefrontInstanceContext`

1. Cart:

    - **Name**: `cart`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `shoppingCartContext`

1. Cart id:

    - **Name**: `cart id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    return _satellite.getVar('cart').id
    ```

1. Product list items:

    - **Name**: `product list items:`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const storefrontContext = _satellite.getVar('storefront');
    const cart = _satellite.getVar('cart');
    
    const returnList = [];
    cart.items.forEach(item => {
        const selectedOptions = [];
        item.configurableOptions?.forEach(option => {
            selectedOptions.push({
                attribute: option.optionLabel,
                value: option.valueLabel,
            });
        });
    
        const productListItem = {
            SKU: item.product.sku,
            name: item.product.name,
            quantity: item.quantity,
            priceTotal: item.prices.price.value * item.quantity,
            currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
            selectedOptions: selectedOptions,
        };
    
        returnList.push(productListItem);
    });
    return returnList;
    ```

1. View cart:

    - **Name**: `view cart`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. For `productListItems`, there can be multiple items that are precomputed. Select **productListItems** > **Populate entire array**.
    - **Data element**: `%product list items%`
    - **Field Group**: `commerce` > `cart` > `cartID`
    - **Cart ID**: **Value** = `%cart id%`
    - **Field Group**: `commerce` > `productListViews` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `view cart`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `shopping-cart-view`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.productListViews`
- **XDM data**: `%view cart%`

### removeFromCart {#removefromcart}

#### Data Elements

Create the following data elements:

1. Product name:

    - **Name**: `product name`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.name`

1. Product sku:

    - **Name**: `product sku`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.sku`

1. Currency code:

    - **Name**: `currency code`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.currencyCode`

1. Product special price:

    - **Name**: `product special price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.specialPrice`

1. Product regular price:

    - **Name**: `product regular price`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `productContext.pricing.regularPrice`

1. Product  price:

    - **Name**: `product price`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
    ```

1. Cart:

    - **Name**: `cart`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `shoppingCartContext`

1. Cart id:

    - **Name**: `cart id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('cart').id
    ```

1. Remove from cart:

    - **Name**: `remove from cart`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. Select **Provide individual items** and click the **Add item** button. Because this view is for a PDP, you can populate with a single item.
    - **Field Group**: `productListItems` > `name`
    - **Name**: **Value** = `%product name%`
    - **Field Group**: `productListItems` > `SKU`
    - **SKU**: **Value** = `%product sku%`
    - **Field Group**: `productListItems` > `priceTotal`
    - **Price total**: **Value** = `%product price%`
    - **Field Group**: `productListItems` > `currencyCode`
    - **Currency code**: **Value** = `%currency code%`
    - **Field Group**: `commerce` > `cart` > `cartID`
    - **Cart ID**: **Value** = `%cart id%`
    - **Field Group**: `commerce` > `productListRemovals` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `remove from cart`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `remove-from-cart`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.productListRemovals`
- **XDM data**: `%remove from cart%`

### initiateCheckout {#initiatecheckout}

#### Data Elements

Create the following data elements:

1. Storefront:

    - **Name**: `storefront`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `storefrontInstanceContext`

1. Cart:

    - **Name**: `cart`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `shoppingCartContext`

1. Cart id:

    - **Name**: `cart id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    return _satellite.getVar('cart').id
    ```

1. Product list items:

    - **Name**: `product list items`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const storefrontContext = _satellite.getVar('storefront');
    const cart = _satellite.getVar('cart');
    
    const returnList = [];
    cart.items.forEach(item => {
        const selectedOptions = [];
        item.configurableOptions?.forEach(option => {
            selectedOptions.push({
                attribute: option.optionLabel,
                value: option.valueLabel,
            });
        });
    
        const productListItem = {
            SKU: item.product.sku,
            name: item.product.name,
            quantity: item.quantity,
            priceTotal: item.prices.price.value * item.quantity,
            currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
            selectedOptions: selectedOptions,
        };
    
        returnList.push(productListItem);
    });
    return returnList;
    ```

1. Initiate checkout:

    - **Name**: `initiate checkout`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. For `productListItems`, there can be multiple items that are precomputed. Select **productListItems** > **Populate entire array**.
    - **Data element**: `%product list items%`
    - **Field Group**: `commerce` > `cart` > `cartID`
    - **Cart ID**: **Value** = `%cart id%`
    - **Field Group**: `commerce` > `checkouts` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `initiate checkout`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `initiate-checkout`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.checkouts`
- **XDM data**: `%initiate checkout%`

### placeOrder {#placeorder}

#### Data Elements

Create the following data elements:

1. Storefront:

    - **Name**: `storefront`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `storefrontInstanceContext`

1. Cart:

    - **Name**: `cart`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `shoppingCartContext`

1. Cart id:

    - **Name**: `cart id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    return _satellite.getVar('cart').id
    ```

1. Order:

    - **Name**: `order`
    - **Extension**: `Adobe Client Data Layer`
    - **Data Element Type**: `Data Layer Computed State`
    - **[Optional] path**: `orderContext`

1. Commerce order:

    - **Name**: `commerce order`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:
    
    ```bash
    const order = _satellite.getVar('order');
    const storefront = _satellite.getVar('storefront');
    
    if (order.payments && order.payments.length) {
        payments = order.payments.map(payment => {
            return {
                paymentAmount: payment.total,
                paymentType: payment.paymentMethodCode,
                transactionID: order.orderId.toString(),
            };
        });
    } else {
        payments = [
            {
                paymentAmount: order.grandTotal,
                paymentType: order.paymentMethodCode,
                transactionID: order.orderId.toString(),
            },
        ];
    }
    
    return {
        purchaseID: order.orderId.toString(),
        currencyCode: storefront.storeViewCurrencyCode,
        payments,
    };
    ```

1. Order shipping:

    - **Name**: `order shipping`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const order = _satellite.getVar('order');
    return {
        shippingMethod: order.shipping.shippingMethod,
        shippingAmount: order.shipping.shippingAmount || 0,
    }
    ```

1. Promotion id:

    - **Name**: `promotion id`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    return _satellite.getVar('order').appliedCouponCode
    ```

1. Product list items:

    - **Name**: `product list items`
    - **Extension**: `Core`
    - **Data Element Type**: `Custom Code`
    - **Open Editor**:

    ```bash
    const storefrontContext = _satellite.getVar('storefront');
    const cart = _satellite.getVar('cart');
    
    const returnList = [];
    cart.items.forEach(item => {
        const selectedOptions = [];
        item.configurableOptions?.forEach(option => {
            selectedOptions.push({
                attribute: option.optionLabel,
                value: option.valueLabel,
            });
        });
    
        const productListItem = {
            SKU: item.product.sku,
            name: item.product.name,
            quantity: item.quantity,
            priceTotal: item.prices.price.value * item.quantity,
            currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
            selectedOptions: selectedOptions,
        };
    
        returnList.push(productListItem);
    });
    return returnList;
    ```

1. Place order:

    - **Name**: `place order`
    - **Extension**: `Adobe Experience Platform Web SDK`
    - **Data Element Type**: `XDM object`
    - **Field Group**: `productListItems`. For `productListItems`, there can be multiple items that are precomputed. Select **productListItems** > **Populate entire array**.
    - **Data element**: `%product list items%`
    - **Field Group**: `commerce` > `order`
    - **Unique Identifier**: **Value** = `%commerce order%`
    - **Field Group**: `commerce` > `shipping`
    - **Unique Identifier**: **Value** = `%order shipping%`
    - **Field Group**: `commerce` > `promotionID`
    - **Promotion ID**: **Value** = `%promotion id%`
    - **Field Group**: `commerce` > `purchases` > `value`
    - **value**: **Value** = `1`

#### Rules 

- **Name**: `place order`
- **Extension**: `Adobe Client Data Layer`
- **Event Type**: `Data Pushed`
- **Specific event**: `place-order`

##### Actions

- **Extension**: `Adobe Experience Platform Web SDK`
- **Action Type**: `Send event`
- **Type**: `commerce.order`
- **XDM data**: `%place order%`

## Setting identity

Experience Platform connector profiles are joined and generated based on the `personID` and the `personalEmail` identity fields in XDM Experience events. 

If you have a previous setup that relies on different fields, you can continue to use those. To set Experience Platform connector profile identity fields, you must set the following fields:

- `personalEmail` - Account events only - follow the steps outlined above for account events
- `personID` - All other events:
    
  - If you are already capturing `ECID` in tags, you can set `personID` in all of your Adobe Experience Platform Web SDK rules to `%ECID%`.
  - To capture `ECID` in tags, you must add a **Custom Code** action to your send event rules following the [Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html). See the example below.

### Example

The following images show how to configure a `pageView` event with `personID` in Experience Platform connector:

1. Configure data element with custom code for ECID:

    ![Configure data element with custom code](assets/set-custom-code-ecid.png)
    _Configure data element with custom code_

1. Add ECID custom code:

    ![Code to set ECID in data element](assets/code-to-set-ecid.png)
    _Code to set ECID in data element_

1. Update XDM schema with personID set as ECID:

    ![Set personID as ECID](assets/set-personid-as-ecid.png)
    _Set personID as ECID_

1. Define rule actions that retrieve ECID:

    ![Retrieve ECID](assets/rule-retrieve-ecid.png)
    _Retrieve ECID_

## Setting consent

Adobe Commerce and Experience Platform connector data collection consent is enabled by default. Opt-out is managed through the [`mg_dnt` cookie](https://docs.magento.com/user-guide/stores/cookie-reference.html). You can follow the steps outlined here if you choose to use `mg_dnt` to manage consent. The [Adobe Experience Platform Web SDK documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) has several additional options for managing consent.

1. Create a **Core Custom Code** data element (`%do not track cookie%`) for the `mg_dnt` cookie:

    ![Create do not track data element](assets/element-dnt-cookie.png)
    _Create do not track data element_

1. Create a **Core Custom Code** data element (`%consent%`) that returns `out` if cookie is set and `in` otherwise:

    ![Create consent data element](assets/element-consent-dnt-cookie.png)
    _Create consent data element_

1. Configure Adobe Experience Platform Web SDK Extension with `%consent%` data element:

    ![Update SDK with consent](assets/config-sdk-consent.png)
    _Update SDK with consent_

## Warnings

- Not following steps to turn off Experience Platform collection results in events being double-counted
- Not setting up mappings/events as described in this topic can affect Adobe Analytics boards
- You cannot set up Target through the Experience Platform connector if data collection is disabled