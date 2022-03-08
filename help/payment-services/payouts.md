---
title: Payouts report
description: Use the Payouts report for full transparency into the payment amount, processed volume, and detailed reporting on the transaction level for financial reconciliation.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
---
# Payouts report

The Payouts report shows comprehensive payout information at-a-glance, allowing you full transparency into the payment amount, processed volume, and detailed reporting on the transaction level for financial reconciliation.

You don't have to open multiple dashboards or views to cross-reference orders and payments or reconcile accounts. [!DNL Payment Services] for Adobe Commerce and Magento Open Source enables you to take all these actions from one place---Payouts report---so that you can view and manage your payouts efficiently.

See linked Commerce order and transaction IDs, transaction amounts, payment method per transaction, and more, all within the Payouts report in the Admin.

You can download payout transactions in a .csv file format for use in existing accounting or order management software.

>[!NOTE]
>
>The data shown in this table is sorted in descending order (`DESC`) by default using the `TRANS DATE`. The `TRANS DATE` is the date and time when the transaction was initiated.

## Availability

On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![Payout transactions in the Admin](assets/payouts-report.png)

## Select data source

In the Payouts report view, you can select the data source---_[!UICONTROL Live]_ or [!UICONTROL Sandbox]_---for which you want to see report results.

![Data sources selection](assets/datasource.png)

If _[!UICONTROL Live]_ is the selected data source, you can see report information for your live stores. If [!UICONTROL Sandbox]_ is the selected data source, you can see report information for your Sandbox environment.

Data source selections work as follows:

* If you do not have any stores that are in Live mode, the data source selection defaults to [!UICONTROL Sandbox]_.
* If you have any stores (one or multiple) in Live mode, the data source selection defaults to _[!UICONTROL Live]_.
* Report exports always honor the data source selection.

To select the data source for your Order Payment Status report:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Click **[!UICONTROL Data source]** and select _[!UICONTROL Live]_ or [!UICONTROL Sandbox]_.

   The report results regenerate based on the data source selected.

## View transactions

By default, 30 days of transactions are shown in the grid.

The number of rows returned in a search, or shown in the default 30 days of transactions, are shown above the Payouts view grid alongside the Transaction dates calendar selector filter.

Scroll to the left and right to view [information for each payout transaction](#column-descriptions) in the daily report, including transaction date, reference ID, invoice number, and payment method details.

### Customize transactions timeframe

From the Payouts view, you can customize the timeframe for the payout transactions you want to view by entering specific dates or selecting a date range from the date picker:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Click the Transaction dates calendar selector filter.
1. Choose the applicable date range.
1. View the payouts statuses in the grid for your specified dates.

## Download transactions

You can download a .csv file containing all the transactions visible in the Payouts view grid.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Customize the date range timeframe for your transactions](#customize-transactions-timeframe).
1. Click the _Download_ (![](assets/icon-download.png)) icon.

Your payout transactions are downloaded in a .csv format.

## Transactions information

The Payouts view shows extensive info for each transaction shown in the grid.

### Column descriptions

Payout reports include the following information.

| Column | Description |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Payment provider |
| [!UICONTROL Provider trans] | Transaction ID |
| [!UICONTROL Trans date] | Date and time transaction was initiated |
| [!UICONTROL Type] | Transaction type---*[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>See [Transaction types](#transaction-types) for more information. |
| [!UICONTROL Status] | Current status of the transaction---*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaction code that indicates either Credit (*CR*) or Debit (*DR*) |
| [!UICONTROL Reference ID] | Original transaction ID for which this event is related |
| [!UICONTROL Invoice] | Invoice ID (one per order) of the transaction |
| [!UICONTROL Commerce order] | Commerce order ID <br> <br>To see related [order info](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, click the ID. |
| [!UICONTROL Commerce trans] | Commerce transaction ID <br> <br>To see related [transaction info](https://docs.magento.com/user-guide/sales/transactions.html){target="_blank"}, click the ID. |
| [!UICONTROL Pay method] | Credit card type---*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*---and associated card provider (such as *Visa* or *MasterCard*) |
| [!UICONTROL Trans amt] | Amount of the transaction |
| [!UICONTROL Cur] | Currency unit for transaction amount |
| [!UICONTROL Pending] | Amount yet to be disbursed |
| [!UICONTROL Cur] | Currency unit for the pending amount |
| [!UICONTROL Seller amt] | Amount of funds transferred to or from a customer <br> <br>Funds moving out of the seller account show a dash (-) prefix. |
| [!UICONTROL Cur] | Currency unit for the seller amount |
| [!UICONTROL Partner fee] | Partner fees associated with the transaction <br> <br>Funds moving out of the partner fee account show a dash (-) prefix. |
| [!UICONTROL Cur] | Currency unit for the partner fee |
| [!UICONTROL Prov fees] | Fees associated with the transaction <br> <br>Funds moving out of the provider's fee account show a dash (-) prefix. |
| [!UICONTROL Cur] | Currency unit for the provider fee |
| [!UICONTROL Fee %] | Percentage of the transaction amount charged as a fee |
| [!UICONTROL Fixed fee] | Fixed provider fee amount |
| [!UICONTROL Chbk fee] | Chargeback fee associated with the transaction <br> <br>A dash (-) prefix indicates that the chargeback fee was reversed. |
| [!UICONTROL Cur] | Currency unit for the chargeback fee |
| [!UICONTROL Hold amt] | Amount put on hold or released from hold <br> <br>A dash (-) prefix indicates that on-hold funds are being released. |
| [!UICONTROL Cur] | Currency unit for the hold amount |
| [!UICONTROL Recoup amt] | Amount recouped from the recoup account <br> <br>Funds moving out of the recoup account show a dash (-) prefix. |
| [!UICONTROL Cur] | Currency unit for the recoup amount |

### Transaction types

These transaction types may be noted in the payout transactions.

| Report | Description |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Money moved between a buyer and a seller for an order |
| [!UICONTROL AUTH] | Authorization and authorization void transactions |
| [!UICONTROL BONUS] | -- |
| [!UICONTROL CHARGEBACK] | Chargeback fee and chargeback fee reversal transactions |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | Partner fees, payment fees, and fee reversal transactions |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | Recoups from bank or loss accounts |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
