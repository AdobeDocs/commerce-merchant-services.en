---
title: Refunds
Description: Create refunds for Payment Services orders in the Admin as part of the credit memo process.
---
# Refunds

Refunds for Payment Services orders are created in the Admin as part of the credit memo process. A credit memo is a document that shows the amount that is due to the customer, for a full or partial refund, which can be applied toward a purchase or refunded directly to the customer. Credit memos can only be issued for orders that are [invoiced](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

See [Credit Memos](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} for more information and to learn how to issue and print credit memos.

For orders processed with PayPal or a credit card you can:

* Refund the entire amount of the order
* Refund a partial amount of an order (or multiple partial amounts)
* Refund an amount less than the value of a specific order item

See [Issuing a Credit Memo](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} for more information.

>[!NOTE]
>
>If you attempt to partially refund an order for more than the remaining order amount (the original amount minus the total of already created refunds) or issue a refund for an amount greater than the full order amount, for either PayPal or credit card-processed orders, you will receive an error.

The Payment Action setting in your Payment Settings configuration---Either `Authorize` or `Authorize and Capture`---determines the [basic refund workflow](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} for orders.

See the [Payment action setting section](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} of Issuing a Credit Memo for more information.
