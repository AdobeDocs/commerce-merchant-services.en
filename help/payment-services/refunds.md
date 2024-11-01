---
title: Refunds
description: Create refunds for [!DNL Payment Services] orders in the Admin as part of the credit memo process.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
---
# Refunds

Refunds for [!DNL Payment Services] orders are created in the Admin as part of the credit memo process. A credit memo is a document that shows the amount that is due to the customer, for a full or partial refund, which can be applied toward a purchase or refunded directly to the customer. Credit memos can only be issued for orders that are [invoiced](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"}.

See [Credit Memos](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos){target="_blank"} in our core user guide for more information and to learn how to issue and print credit memos.

For orders processed with PayPal or a credit card you can:

* Refund the entire amount of the order
* Refund a partial amount of an order (or multiple partial amounts)
* Refund an amount less than the value of a specific order item

See [Issuing a Credit Memo](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create){target="_blank"} in our core user guide for more information.

>[!NOTE]
>
>An error occurs for PayPal or credit card-processed orders if you attempt to partially refund an order for more than the remaining order amount (original amount minus the total of existing refunds), or if you issue a refund for an amount greater than the full order amount.

The [!UICONTROL Payment Action] setting in your [!UICONTROL Payment Settings] configuration---Either `Authorize` or `Authorize and Capture`---determines the [basic refund workflow](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos#refund-workflow){target="_blank"} for orders.

See the [Payment action setting section](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create#payment-action-setting){target="_blank"} of _Issuing a Credit Memo_ for more information.
