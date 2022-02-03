---
title: Voids
---
# Voids

With Payment Services, you can utilize existing Commerce functionality for voiding transactions. Voids allow you to free the funds in a credit or debit card account that are blocked or held aside by an authorization for the amount of a purchase.

>[!NOTE]
>
>You can only void a transaction if payment is not yet captured.

If your store is [configured](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} to authorize only (not capture) funds at the point of sale, a purchase from your store results in an order with a `Processing` status in the Magento Admin.

You can also [cancel an order](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} that is not invoiced. Any un-captured authorizations are also voided as part of that cancellation process.

>[!NOTE]
>
>Canceling an order also produces a void, but voiding an order does not trigger a cancellation.

Check out the [Order Workflow](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} topic to learn more about the basic steps an order goes through.

See [Processing an Order](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} to learn about the void functionality and how to void an order transaction.
