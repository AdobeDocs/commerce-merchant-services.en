---
title: Voids
description: Voids allow you to free the funds in a credit or debit card account that are blocked or held aside by an authorization for the amount of a purchase.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
---
# Voids

With [!DNL Payment Services], you can use existing Commerce functionality for voiding transactions. Voids allow you to free the funds in a credit or debit card account that are blocked or held aside by an authorization for the amount of a purchase.

>[!NOTE]
>
>You can only void a transaction if payment is not yet captured.

If your store is [configured](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} to authorize only (not capture) funds at the point of sale, a purchase from your store results in an order with a `Processing` status in the Commerce Admin.

You can also [cancel an order](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order){target="_blank"} that is not invoiced. Any uncaptured authorizations are also voided as part of that cancellation process.

>[!NOTE]
>
>Canceling an order also produces a void, but voiding an order does not trigger a cancellation.

To learn more about the basic steps an order goes through, see the [Order Workflow](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing){target="_blank"} topic in the core user guide.

To learn about the void functionality and how to void an order transaction, see [Processing an Order](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#process-an-order){target="_blank"} in the core user guide.
