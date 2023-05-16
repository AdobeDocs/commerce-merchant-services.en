---
title: Transactions Report
description: Use the Transactions report...
role: User
level: Intermediate
---
# Transactions Report

[!DNL Payment Services] for [!DNL Adobe Commerce] and [!DNL Magento Open Source] offers you comprehensive reporting so that you can get a clear view of your store's transactions, orders, and payments.

![Financial reports view](assets/reports-justpayouts.png) REPLACE

The Transactions report provides visibility into transaction authorization rates and negative transaction trends so that you can effectively monitor the health of your store and preemptively identify and address any transaction issues.

See individual transactions and their payment methods, result, payment processor codes, and more.

You can download the Transactions report in a .csv file format for use in existing accounting or order management software.

>[!NOTE]
>
>You cannot view financial reports if you have not [onboarded and activated Live mode](production.md#enable-live-payments) for [!DNL Payment Services].

## Availability

On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Transactions]** to see the transactions for your orders.

![Order payment statuses in the Admin](assets/order-payment-status-report.png) REPLACE

## Select data source

In the Transactions report view, you can select the data source---_[!UICONTROL Live]_ or _[!UICONTROL Sandbox]_---for which you want to see report results.

![Data sources selection](assets/datasource.png)

If _[!UICONTROL Live]_ is the selected data source, you can see report information for your stores that use [!DNL Payment Services] in _[!UICONTROL Live]_ mode. If [!UICONTROL Sandbox]_ is the selected data source, you can see report information for your Sandbox environment.

Data source selections work as follows:

* If you do not have any stores that use [!DNL Payment Services] in Live mode, the data source selection defaults to _[!UICONTROL Sandbox]_.
* If you have any stores (one or multiple) that use [!DNL Payment Services] in Live mode, the data source selection defaults to _[!UICONTROL Live]_.
* Report exports always honor the data source selection.

To select the data source for your [!UICONTROL Transactions] report:

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Click **[!UICONTROL Data source]** and select _[!UICONTROL Live]_ or _[!UICONTROL Sandbox]_.

   The report results regenerate based on the data source selected.

## Customize dates timeframe

From the Transactions report view, you can customize the timeframe of the transactions you want to view by selecting specific dates. By default, 30 days of order payment statuses are shown in the grid.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Click the **[!UICONTROL Transaction dates]** calendar selector filter.
1. Choose the applicable date range.
1. View the transactions for your specified dates in the grid.

## Show and hide columns

The Transactions report shows all available columns of information by default. You can, however, customize which columns you see in your report.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Click the _Column settings_ icon (![column settings icon](assets/column-settings.png)).
1. To customize which columns you see in the report, check or uncheck columns in the list.

   The Transactions report will immediately show any changes you made in the Column settings menu. The column preferences will be saved and will remain in effect if you navigate away from the report view.

## Download transactions

You can download a .csv file with all transactions visible in the transactions view grid, whether you are viewing the default 30 days of statuses or a customized timeframe.

1. On the _Admin_ sidebar, go to **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. If you want to see statuses for a timeframe other than the last 30 days, [customize the date range timeframe for your statuses](#customize-dates-timeframe).
1. Click the _Download_ (![download icon](assets/icon-download.png)) icon.

Your transactions are downloaded in a .csv format.

## Transactions information

The Order payment status view shows extensive info for each status shown in the grid.

### Column descriptions

Transactions reports include the following information.

| Column | Description |
| ------------ | -------------------- |
| [!UICONTROL Provider Transaction ID] | Commerce order ID<br> <br>To see related [order info](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, click the ID. |
| [!UICONTROL Transaction Date] | Order date timestamp |
| [!UICONTROL Payment Method] | Date timestamp of payment authorization |
| [!UICONTROL Result] | Current Commerce [order status](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Processor Code] | Invoice status of order---*[!UICONTROL No]*, *[!UICONTROL Partial]*, or *[!UICONTROL Yes]* |
| [!UICONTROL AVS Code] | Shipping status of order---*[!UICONTROL No]*, *[!UICONTROL Partial]*, or *[!UICONTROL Yes]* |
| [!UICONTROL CVV Code] | Grand total amount of the order |
| [!UICONTROL Amount] | Currency type of order |
| [!UICONTROL Currency] | Status of payment for a specific order |
| [!UICONTROL Type] | Amount paid on an order |

### Results descriptions

| Column | Description |
| ------------ | -------------------- |
| [!UICONTROL OK] | Commerce order ID<br> <br>To see related [order info](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, click the ID. |
| [!UICONTROL Rejected by Payment Provider] | Order date timestamp |
| [!UICONTROL Rejected by Bank] | Date timestamp of payment authorization |