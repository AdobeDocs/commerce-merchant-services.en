---
title: Create Custom Events
description: Learn how to create custom events connect your Adobe Commerce data to other Adobe DX products.
---
# Create Custom Events

You can extend the [eventing platform](events.md) by creating your own storefront events to collect data unique to your industry. When you create and configure a custom event, it is sent to the [Magento Storefront Event Collector](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Handle Custom Events

Custom events are supported for the Adobe Experience Platform only. Custom data is not forwarded to Adobe Commerce dashboards and metrics trackers.

For any `custom` event, the collector adds a `personId` (`ecid`) to `customContext` and wraps an `xdm` object around it before forwarding to the Edge.

Example:

Custom event published through MSE SDK:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> Using custom events may affect default Adobe Analytics reports.

## Handle Event Overrides (custom attributes)

Attribute overrides for standard events are supported for the Experience Platform only. Custom data is not forwarded to Commerce dashboards and metrics trackers.

For any event with a set `customContext`, the collector overrides `personId` and Adobe Analytics counters, and forwards all other attributes set in `customContext`.

Examples:

Product view with overrides published though MSE SDK:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

Product view with Adobe Commerce overrides published though MSE SDK:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Overriding events with custom attributes may affect default Adobe Analytics reports.
