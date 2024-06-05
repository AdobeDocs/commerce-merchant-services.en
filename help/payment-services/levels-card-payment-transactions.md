---
title: Level 2 and level 3 processing
description: Card payment processing levels within [!DNL Payment Services] transactions.
role: Admin
feature: Payments
exl-id: db8993fe-dd6f-48b5-9e7b-69a0f2e08552
---
# Level 2 and level 3 processing

There are three levels of card processing available through [!DNL Payment Services]:

* Level 1 is the most common, requires less information and therefore generally incurs higher interchange fees compared to transactions processed with Level 2 or Level 3 data, which are usually related to corporate and purchase credit cards.

* With level 2 and level 3, [!DNL Payment Services] customers on interchange plus plus (IC++) pricing who accept a lot of purchase card or corporate card transactions can potentially receive a lower processing rate by allowing [!DNL Payment Services] to send more information about a transaction. If the transaction qualifies, according to the card network requirements, then the merchant may receive a lower processing rate for a particular transaction.

>[!NOTE]
>
>Level 2 and level 3 pricing only applies for Visa and MasterCard transactions. American Express only offers level 2 pricing. Discover does not offer level 2 nor level 3 pricing. See [payment processing](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} in the PayPal Developer documentation for more information.

See [What is IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} in PayPal developer documentation for more information.

Level 2 and level 3 processing data enables merchants to lower their IC++ pricing if they provide some additional details about the purchase that reduces the processor risk and provides beneficial aspects:

* Large customers will be paying less by providing this processing data.

* Customers are less likely to run into fraudulent situations since the orders have more information.

However, card networks, like Visa and Mastercard, ultimately determine whether a transaction qualifies for level 2 or level 3 processing:

* Level 2 data contains additional information, such as the tax amount for the order, or the customer code or PO number.

* Level 3 data is more detailed information about the sale, which helps to qualify for even lower interchange rates compared to Level 2. Level 3 data contains information like a description of the item purchased, the quantity of units purchased, unit of measure for the items ordered, and other specific details.

[!DNL Payment Services] collects this data and provides detailed reporting of your payment transactions.

## Level 2 and level 3 card payment transactions in [!DNL Payment Services]

To qualify for level 2 or level 3 processing, merchants must send the previous information, although it is the card networks who ultimately determine which level a transaction qualifies for when processing it.

See the [Payment processing FAQ](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} in PayPal developer documentation for more information.

Level 2 and level 3 processing is disabled by default for [!DNL Payment Services] merchants at store level.

Level 2 and level 3 processing are available if you are already using IC++ pricing. To enable this feature you can do this via the [Command-line Interface (CLI](configure-cli.md).

>[!IMPORTANT]
>
>If you have any questions, please reach out to your [!DNL Payment Services] account manager.
