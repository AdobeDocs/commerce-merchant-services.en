---
title: Create Custom Events
description: Learn how to create custom events to connect your Adobe Commerce data to other Adobe DX products.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
---
# Create Custom Events

You can extend the [eventing platform](events.md) by creating your own storefront events to collect data unique to your industry. When you create and configure a custom event, it is sent to the [Adobe Commerce Events Collector](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## Handle custom events

Custom events are supported for the Adobe Experience Platform only. Custom data is not forwarded to Adobe Commerce dashboards and metrics trackers.

For any `custom` event, the collector:

- Adds `identityMap` with `ECID` as a primary identity
- Includes `email` in `identityMap` as a secondary identity _if_ `personalEmail.address` is set in the event
- Wraps the full event inside an `xdm` object before forwarding to the Edge

Example:

Custom event published through Adobe Commerce Events SDK:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> Using custom events may affect default Adobe Analytics reports.

## Handle event overrides (custom attributes)

Attribute overrides for standard events are supported for the Experience Platform only. Custom data is not forwarded to Commerce dashboards and metrics trackers.

For any event with `customContext`, the collector overrides joins fields set in the relevant contexts with fields in `customContext`. The use case for overrides is when a developer wants to reuse and extend contexts set by other parts of the page in already supported events.

>[!NOTE]
>
>When overriding custom events, event forwarding to Experience Platform should be turned off for that event type to avoid double counting.

Examples:

Product view with overrides published though Adobe Commerce Events SDK:

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Overriding events with custom attributes may affect default Adobe Analytics reports.
