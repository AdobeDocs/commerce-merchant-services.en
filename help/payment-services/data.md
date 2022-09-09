---
title: Available data
description: Use financial reporting data to reconcile reporting with non-Commerce systems.
role: User
level: Intermediate
---
# Available data

Some order and payouts data is available to you so that you can coordinate Adobe Commerce financial reporting across external systems.

## Reconcile with ERP system

You can reconcile Adobe Commerce financial reporting with your non-Adobe Enterprise Resource Planning (ERP) system using the increment ID associated with a specific order.

When Payment Services sends the Commerce order to PayPal, the increment ID is included as the `custom_id`. The `custom_id` is visible in the merchant activity detail for a payout and in the PayPal webhook.

`custom_id` at the bottom of the merchant activity detail for a payout:

![`custom_id` in merchant activity detail](assets/merchant-activity.png)

`custom_id` in the details in PayPal's webhook:

``` json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

See PayPal's REST APIs documentation for more information:

*  [`purchase_unit` in which `custom_id` resides](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
*  [Show order details](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
