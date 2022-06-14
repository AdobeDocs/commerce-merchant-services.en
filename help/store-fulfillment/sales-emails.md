---
title: Sales Emails
description: Configure settings for the transactional email templates to communicate with customers and store administrators during the order and fulfillment process.
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
---
# Sales Emails

Store Fulfillment offers an extended set of transactional email templates to support order and fulfillment workflows. They offer consistent, automated communication and messaging across channels—
notifying customer and store administrators about order status changes, instructions for in-store pickup orders, and more. 

Store Fulfillment email templates are configured with default messaging and settings. Merchant administrators in Adobe Commerce can manage and modify configurations, and select the email templates to communicate with customers in different scenarios. Administrators can configure and customize templates as well.

Configure the Sales Email templates from the Admin: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**. 

## Emails - General Settings

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Asynchronous Sending</strong></td>
<td>Disable this feature. Asynchronous email sending is not supported. For the fastest communication and response time for Store Pickup, send emails immediately instead of batching them. </td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>

## Order Ready for Pickup in Store

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Enabled</strong></td>
<td>This email is sent to the customer when the store associate has completed picking their order. Set to “No” to disable the email notification. If the email template is disabled, it does not prevent an order from being picked by the store associate.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Ready For Pickup Email Sender</strong></td>
<td>The sender identity used when sending the email notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Ready For Pickup Email Template</strong></td>
<td>The email message template used to notify registered customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Order Ready For Pickup Email Template for Guest</strong></td>
<td>The email message template used to notify guest customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Ready for Pickup Email Template for Alternate Pickup Contact</strong></td>
<td>The email message template used to notify additional contacts named in the order. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Ready For Pickup Email Copy To</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Ready For Pickup Email Copy Method</strong></td>
<td>The method of email “carbon copy” sends to use.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>


## Order has been picked up in Store

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Enabled</strong></td>
<td>This email is sent to the customer when to confirm that they have picked up their order from the store. Set to “No” to disable the email notification. If the email template is disabled, it does not prevent an order from being picked up by the customer.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Has Been Picked Up Email Sender</strong></td>
<td>The sender identity used when sending the email notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Has Been Picked Up Email Template</strong></td>
<td>The email message template used to notify registered customers. A default template is provided with the integration</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Order Has Been Picked Up Email Template for Guest</strong></td>
<td>The email message template used to notify guest customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Has Been Picked Up Email Copy To</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Has Been Picked Up Email Copy Method</strong></td>
<td>The method of email “carbon copy” send to use.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>

## Order Delayed

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Enabled</strong></td>
<td>This email is sent to the customer to notify them about a delay in processing or picking their order at the merchant store. Set to “No” to disable the email notification. If the email template is disabled, feature does not prevent an order from being delayed.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Delayed Email Sender
</strong></td>
<td>The sender identity used when sending the email notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Delayed Email Template</strong></td>
<td>The email message template used to notify registered customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Order Delayed Email Template for Guest</strong></td>
<td>The email message template used to notify guest customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Delayed Email Copy To</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Delayed Copy Method</strong></td>
<td>The method of email “carbon copy” send to use.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>



## Order Canceled

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Enabled</strong></td>
<td>This email is sent to the customer to notify them that their order has been canceled at the merchant store. Set to <code>No</code> to disable the email notification. If the email template is disabled, it feature does not prevent an order from being canceled.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Canceled Email Sender
</strong></td>
<td>The sender identity used when sending the email notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Canceled Email Template</strong></td>
<td>The email message template used to notify registered customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Order Canceled for Guest</strong></td>
<td>The email message template used to notify guest customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Canceled Email Copy To</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Canceled Copy Method</strong></td>
<td>The method of email “carbon copy” send to use.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>


## Order Partly Canceled

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Enabled</strong></td>
<td>This email is sent to the customer to notify them that part of their order has been canceled at the merchant store. Set to <code>No</code> to disable the email notification. If the email template is disabled, it does not prevent an order from being partly canceled.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Partly Canceled Email Sender
</strong></td>
<td>The sender identity used when sending the email notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Partly Canceled Email Template</strong></td>
<td>The email message template used to notify registered customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<td><strong>Order Partly Canceled Email Template for Alternate Pickup Contact</strong></td>
<td>The email message template used to notify additional contacts named in the order. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Order Partly Canceled for Guest</strong></td>
<td>The email message template used to notify guest customers. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Partly Canceled Email Copy To</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Send Order Partly Canceled Copy Method</strong></td>
<td>The method of email “carbon copy” send to use.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>

## Ship to Store

<table>
<thead>
<tr>
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Scope</strong></th>
<th><strong>Required</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Order Has Ship To Store Products Email Sender</strong></td>
<td>Email sent to specified merchant personnel as an aggregate report of all open orders that cannot be picked in a merchant store until their inventory is available. </br></br> Merchants can use this report to initiate and manage store-to-store inventory transfers or replenishment. </br></br>This notification only applies when the [!DNL Ship-to-Store] features are enabled.
</br></br>This label does not affect the selected shipping carrier or their available shipping method labels.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Ship To Store Email Recipients</strong></td>
<td>A comma-delimited list of email addresses to send a copy of each notification.</td>
<td>Store View</td>
<td>No</td>
</tr>
<tr>
<td><strong>Email Template</strong></td>
<td>The email message template used to notify recipients. A default template is provided with the integration.</td>
<td>Store View</td>
<td>No</td>
</tr>
</tbody></table>

>[!NOTE]
>
>If you allow backorders, you must provide an administrator email address to receive notifications about these orders. Add the address to the following configuration settings: **[!UICONTROL Send Order Delayed Email Copy To]** in the [Order Delay](#order-delayed) template, and [!UICONTROL Ship To Store Email Recipients] in the [Ship to Store](#ship-to-store) template. 



