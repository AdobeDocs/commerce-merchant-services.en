---
title: Tag Data for Adobe Experience Platform
description: Learn how to connect your Commerce data to the Adobe Experience Platform.
hidefromtoc: yes
---
# Tag data

If you are using Adobe Experience Platform Web SDK (alloy.js) or tags in Adobe Experience Platform, then your storefront data is already tagged and is being sent to the Adobe Experience Platform Edge. However, to include additional [!DNL Commerce] data provided in the Experience Platform connector extension, you need to add the fields in the Experience Platform connector schema to your existing XDM schema. [Learn how to edit an existing schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit). When you update your XDM schema to support the fields in the Experience Platform connector schema, no further steps are needed to forward your [!DNL Commerce] data to the Adobe Experience Platform Edge.

>[!CAUTION]
>
> If you have already deployed a site tagging solution, it is possible you are already capturing the same events or a superset of those events provided in the Experience Platform connector extension. See the list of events Experience Platform connector captures [here](events.md). If that is the case, installing the Experience Platform connector extension might not make sense. Migrating or mapping to a different solution can be challenging and time-consuming. It is important that you weigh the benefits of migrating versus the time and effort required to make the switch. While Adobe encourages all merchants to install the extension, it is up to you to decide if it makes sense for your business.

If you are not using Adobe Experience Platform Web SDK (alloy.js) or tags in Adobe Experience Platform, then there are a couple of options to tag your storefront data:

* For Luma, Venia, or Adobe Experience Manager storefronts, install and configure the Experience Platform connector extension, which tags and forwards your data to the Adobe Experience Platform Edge. [Luma and Adobe Experience Manger](#method-1), [Venia](#method-2).
* For custom-built React storefronts, use the Adobe Commerce SDK. You can configure this SDK to tag and forward your data to the Adobe Experience Platform Edge. [Learn more](#method-3).

## Get IDs

Retrieve your [IMS Org ID and Datastream ID](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html).

   Connecting your Adobe Commerce instance to the Adobe Experience Platform Edge requires that you have an Adobe Experience Platform account so you can obtain an IMS Org ID. Later, when you add the IMS Org ID in the [[!DNL Commerce] Admin](#update-admin), you are linking the IMS Org ID to your Mage ID. This creates the link between Adobe Commerce and Adobe Experience Manager. The IMS Org ID is set globally based on the specific Adobe Commerce instance you are using. The Datastream ID allows for event-forwarding from Adobe Commerce to Adobe Experience Manager and can be associated to a specific website, storeCode, or storeView within your specific Adobe Commerce instance.

## Choose storefront configuration

Choose the onboarding method that meets your storefront configuration and follow the instructions.

* [Method 1](#method-1): Luma (PHP) or AEM
* [Method 2](#method-2): PWA
* [Method 3](#method-3): Custom-built

### Method 1: Luma (PHP) or AEM storefront {#method-1}

This onboarding method is recommended when installing Experience Platform connector to:

* An existing Luma (PHP) storefront
* An existing AEM storefront

1. Install the Experience Platform Connector metapackage.

   ```bash
   composer require magento/platform-connector
   ```
   
   This metapackage contains the following modules:

   * `module-platform-connector-admin` - Updates the Admin UI
   * `module-platform-connector` - Sets the `ImsOrgId` and `datastreamId` in the Magento Storefront Events SDK

1. Install Commerce Data Services extension to include profile and checkout events.

   ```bash
   composer require magento/data-services
   ```

1. (Optional) To include [!DNL Live Search] data, which comprises search events, install the [[!DNL Live Search]](../live-search/install.md) extension.

1. (Optional) To include [!DNL Product Recommendations] data, which comprises [!DNL Product Recommendations] events, install the [[!DNL Product Recommendations]](../product-recommendations/install-configure.md) extension.

1. Add your [IMS Org ID and Datastream ID](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) to the [[!DNL Commerce] Admin](#update-admin).

### Method 2: PWA Studio storefront {#method-2}

This onboarding method is recommended when installing Experience Platform connector to:

* An existing PWA storefront

WIP, tracked in PWA-788

1. Do this.

1. Add your [IMS Org ID and Datastream ID](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) to the [[!DNL Commerce] Admin](#update-admin).

### Method 3: Custom-built React {#method-3}

This onboarding method is recommended when installing Experience Platform connector to:

* A custom-built React storefront

For custom-built React storefronts, the Magento Storefront Events SDK and Magento Storefront Event Collector need to be installed and configured to send events to AEP. This requires that the SDK and Collector are loaded with an `EventForwardingContext` and `AEPContext`. The `AEPContext` requires an [IMS Org Id and a datastream ID](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html).

1. Install the [Magento Storefront Events SDK](https://www.npmjs.com/package/@adobe/magento-storefront-events-sdk):

   ```bash
   npm i @adobe/magento-storefront-events-sdk
   ```

1. Install the [Magento Storefront Event Collector](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

   ```bash
   npm i @adobe/magento-storefront-event-collector
   ```  

1. Set event forwarding context.

   ```bash
   mse.context.setEventForwarding(eventForwardingCtx);
   ```

   **Example**

   ```javascript
   mse.context.setEventForwarding({
   snowplow: /*boolean, optional, defaults to true for backwards compatibility*/,
   aep: /*boolean, optional, defaults to false*/
   });
   ```

1. Set the AEP context. This sets the IMS Org Id and Datastream Id.

   ```bash
   mse.context.setAEP(aepCtx);
   ```
   
   **Example**

   ```javascript
   mse.context.setAEP({
   imsOrgId: /*string, required*/
   edgeConfigId: /*string, required*/
   renderDecisions: /*boolean, defaults to false - specifies whether decisions sent to alloy from target should be auto loaded on a page*/
   });
   ```

1. Send events using the Magento Storefront Events SDK schema.

   **Example**

   ```javascript
   import mse from "@adobe/magento-storefront-events-sdk";
   // handler - can go in a different module
   function addToCartHandler(event) {
    // do something with the event
   }
   // subscribe to events
   mse.subscribe.addToCart(addToCartHandler);

   // set context data
   const shoppingCartContext = {
    id: "1",
    items: [
        {
            id: "shoppingCart",
            product: {
                productId: 111111,
                sku: "ts001",
                pricing: {
                    regularPrice: 20.0,
                    currencyCode: "USD",
                },
            },
            quantity: 1,
        },
      ],
   };
   mse.context.setShoppingCart(shoppingCartContext);

   // publish events
   mse.publish.addToCart();

   // unsubscribe from events
   mse.unsubscribe.addToCart(addToCartHandler);
   ```
