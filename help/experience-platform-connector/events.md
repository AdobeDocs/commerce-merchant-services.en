---
title: Events
description: Learn which events capture data and see the full schema definition.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
---
# Experience Platform Connector Events

The following lists the [!DNL Commerce] events available when you install the Experience Platform connector extension. The data these events collect is sent to the Adobe Experience Platform edge. You can also create [custom events](custom-events.md) to collect additional data not provided out of the box.

Click the event name to see the full schema definition.

|Event|Type|
|---|---|
|[Add to Cart](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts)|Storefront|
|[View Shopping Cart](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts)|Storefront|
|[View Page](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts)|Storefront|
|[View Product](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts)|Storefront|
|[Start Checkout](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts)|Storefront|
|[Complete Checkout](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts)|Storefront|
|[Sign In](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts)|Profile|
|[Sign Out](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts)|Profile|
|[Create Account](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts)|Profile|
|[Edit Account](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts)|Profile|
|[Search Request Sent](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts)|Search|
|[Search Response Received](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)|Search|

>[!NOTE]
>
> The `Sign In`, `Sign Out`, `Create Account`, and `Update Account` events are triggered when the specific action is attempted. It does not indicate that the action was successful.
