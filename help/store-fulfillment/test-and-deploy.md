---
title: Test and Deploy Store Fulfillment
description: Test plan to verify the Store Fulfillment functionality. Tests cover the Inventory Sync API, the end-to-end fulfillment workflow for canceled orders, Store Fulfillment app user management, and the Customer Check-In experience.
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
---
# Test and Deploy Store Fulfillment for Adobe Commerce

After you have completed the onboarding process in your development environment, you can start the process to test and deploy the Store Fulfillment solution to your production environment.

**Prerequisites**

Before testing or synchronizing any information, stores, or orders, verify that you have completed the following tasks:

- Completed the [General Configuration](enable-general.md) for Store Fulfillment services.

- [Add and validate the account credentials and connection details for your sandbox and production environments](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Confirm that the [Adobe Commerce Integration](connect-set-up-service.md#configure-store-fulfillment-account-credentials) for the Store Fulfillment solution is available and authorized.

## Prepare for testing

The connection configuration must be completed before you can create any test orders or perform integration testing. Before testing, you must also verify that your store data is synchronized.

1. Synchronize Store Fulfillment sources.

   - Go to **[!UICONTROL Stores > Sources]**.

   - Select **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. From the store grid, verify that stores been marked as `Synced` before creating test orders.

## Sample test plan

Retailers validate the basic functionality of the Store Fulfillment solution during the configuration and test phases of a deployment. This sample test plan provides a starting point for testing. Add additional scenarios based on your requirements.

>[!NOTE]
>
>After completing the initial onboarding for the Store Fulfillment solution or updating an existing installation, always test the application in a non-production environment before you deploy to production.

This sample test plan covers the following functional areas:

| Functional Area                     | Function                                 | Role                             |
|-------------------------------------|------------------------------------------|----------------------------------|
| Inventory and Order Synchronization | Inventory API Sync                       | Adobe Commerce Admin             |
| End-to-End                          | Order Cancellation Workflows             | Customer, Admin, Store Associate |
| Admin                               | Store Fulfillment App permissions        | Admin                            |
| Adobe Commerce Frontend             | Product Types                            | Customer, Admin                  |
| Frontend Checkout</br>Check-In Form | Check-In Experience                      | Customer, Admin                  |
| Store Assist App                    | Order</br>Pick</br>Stage</br>and Handoff | Store Associate                  |

### Inventory API synchronization

This section of the test plan covers inventory and order synchronization to verify that updates to pickup sources and stocks are synchronized correctly between Adobe Commerce and the Store Fulfillment solution.

**Functional Area**: Inventory and Order Synchronization</br>
**Role:** Admin</br>
**Test type:** All Positive

<table>
<thead>
<tr>
<th>Function</th>
<th>Test Scenario</th>
<th>Expected results</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Add pickup stock source</strong></td>
<td>Save a new pickup stock source.</td>
<td>The real-time sync sends the source details to the Walmart GIF service within 5 minutes.</td>
</tr>
<tr>
<td><strong>Update existing pickup stock source</strong></td>
<td>Save updates to an existing pickup stock source.</td>
<td>The real-time sync operation sends the details to the Walmart GIF within 5 minutes</td>
</tr>
<tr>
<td><strong>Pickup stock source</br><code>Is Synced</code> status</strong></td>
<td>Save updates to an existing pickup stock source.</td>
<td>After a successful operation, the <code>Is Synced</code> column of the Manage Source page updates from <code>No</code> to <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>Modified stock reservation process</strong></td>
<td>Create and submit a new order for a product.</td>
<td>The salable quantity for the product decreases accordingly.</td>
</tr>
<tr>
<td><strong>New Order Push, API Sync—Customer order</strong></td>
<td>Customer submits a store pickup order.</td>
<td><ul><li>In the Admin Order view, an <strong>Adobe Commerce Admin user</strong> sees that the Order Sync status updated to <code>Sent</code></li><li>The order details log includes the message <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>New Order Push, API Sync—Admin submits order</strong></td>
<td>An Adobe Commerce <strong>Admin</strong> submits a pickup order.</td>
<td><ul><li>In the Admin Order view, the Order Sync status updates to <code>Sent</code>.</li><li>The order details log includes the message <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>New Order Push, Exception Queue<strong></td>
<td>Identify several Virtual and downloadable products in the Adobe Commerce Admin that can be fulfilled through Adobe Commerce without requiring interaction with Fulfillment service (FaaS).</td>
<td>These products are removed or flagged appropriately in the export to prevent a downstream conflict with the FaaS.</td>
</tr>
</tbody>
</table>

### Order Cancellation workflows

This section of the test plan includes scenarios to test the end-to-end workflow for orders that are cancelled through Adobe Commerce.

**Functional area:** Adobe Commerce Admin</br>
**Role:** End-to-End (Admin, Store Associate, Customer)</br>
**Test result type:** Positive for all scenarios

<table style="table-layout:fixed">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Expected Results</th>
</tr>
<tr>
<td><strong>Full order cancellation</strong></td>
<td><ol>
<li>Place order.</li>
<li>Wait until the order is synced.</li>
<li>Verify invoice creation (if authorize and capture) receipt of invoice email.</li>
<li>Create Credit Memo with all the ordered products from the Invoice view.</li>
</ol>
</td>
<td>
<ul>
<li>Order history updated with <code>We refunded $X online. Transaction ID: transactionID</code> and <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>Order status is <code>Closed</code>. (We have set PAYMENT REVIEW now.)</li>
<li>Credit memo created in Adobe Commerce. (Wait until cron works.)</li>
<li>If all items picked, then ready for pickup email <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> flag is <code>true</code>.)</li>
<li>If all items not picked, then cancellation email and DISPLAY COMMENT HISTORY show <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> flag is <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>Partial Order Cancellation<strong></td>
<td>
<ol>
<li>Place order with at least two products.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Wait two hours for transaction settlement.</li>
<li>Create Credit Memo with only part of the ordered products from the Invoice view.</li>
</td>
<td>
<ul>
<li>Order history update: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Order history update: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Receipt of order refund email: <code>$x amount was refunded</code></li>
<li>Order status is <code>Processing</code>.</li>
<li>Credit memo created in Adobe Commerce (Wait until cron works).</li>
<li>If some items were not picked, confirm that the [!UICONTROL Ready for Pickup] email with the nil pick or refund section is displayed. <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> flag is <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Ready for Pickup</br></br>Full cancellation</br>(all products are set as picked with 0 qty)</strong></td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Go to the Postman and run the Ready for Pickup request with all products set as <code>picked</code> with <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>Order history updated: <code>We refunded $X offline</code></li>
<li>The order status is <code>CLOSED</code>.
<li>The Credit Memo is created. (Wait until cron works.)</li>
<li>Refund email received: <code>$x amount was refunded</code></li>
<li>Order Cancellation email sent.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Ready for Pickup - Partial cancellation</strong></br></br><strong>(Some products are picked, and some are picked with <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Go to the Postman and run the Ready for Pickup request with part of the products set as picked with 0 qty and the rest of them picked.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] and [!UICONTROL Canceled Items] tables. </li>
<li>The order status is READY FOR PICKUP. </li>
<li>Order history updated: <code>We refunded $X offline.</code>
<li>Order history updated: <code>Order notified as partly canceled at: Date and hour</code>
<li>Refund email received: <code>$x amount was refunded</code>
<li>The credit memo is created. (Wait until cron works.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Ready for Pickup - Partial Cancellation</br></br>Some products are picked, and some are picked with <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Go to the Postman and run the Ready for Pickup request with part of the products set as picked with 0 qty and the rest of them picked.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] and [!UICONTROL Canceled Items] tables. </li>
<li>The order status is READY FOR PICKUP. </li>
<li>Order history updated: <code>We refunded $X offline.</code>
<li>Order history updated: <code>Order notified as partly canceled at: Date and hour</code>
<li>Refund email received: <code>$x amount was refunded</code>
<li>The credit memo is created. (Wait until cron works.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensed (during dispensation) </br></br>Full cancellation (all products are set as rejected)</strong>
</td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Go to the Postman and run the Ready for Pickup request with all the products set as picked.</li>
<li>Open your mailbox, find the Ready for Pickup email. Then, click **[!UICONTROL Confirm Arrival]**.</li>
<li>Check in.</li>
<li>Go to Postman and run the Dispensed request with all the products set as rejected.</li>
</ol>
<td><ul>
<li>Order history updated: <code>We refunded $X offline.</code></li>
<li>Refund email received: <code>$x amount was refunded</code></li>
<li>Status set to <code>CLOSED</code>.</li>
<li>Credit Memo created. (Wait until cron works.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensed (during dispensation)</br></br>Partial Cancellation</br>(Some products are dispensed; some are rejected.)</strong>
</td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Go to Postman, and run the Ready for Pickup request with all the products set as picked.</li>
<li>Open your mailbox. Find the Ready for Pickup email, and select <code>Confirm Arrival</code>.</li>
<li>Check in.</li>
<li>Go to the Postman, and run the Dispensed request with some products set to dispensed and some set to rejected</li>
</ol>
</td>
<td>
<li>Order history updated: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>Refund email received: <code>$x amount was refunded</code>
<li>Order Status set to <code>Ready for pickup Dispensed</code>
<li>Credit Memo created. (Wait until cron works.)</li>
</td>
</tr>
<tr>
<td> <strong>New RMA After return (full)</strong>
</td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>If the authorize and capture option is configured, verify that the invoice was created and that the customer received the invoice email.</li>
<li>Pick all the products with Postman.</li>
<li>Check in.</li>
<li>Make a dispense.</li>
<li>Go to order, and select<strong>[!UICONTROL Create returns]=
<li>Create the RMA.</li>
</ol>
</td>
<td>
<ul>
<li>The RMA was created and is displayed below the <strong>[!UICONTROL Returns]</b> tab on the Order view.</li>
<li>Customer received RMA confirmation email.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>New RMA After return — Partial</strong>
</td>
<td>
<ol>
<li>Place the order.</li>
<li>Wait until the order is synced.</li>
<li>Check that invoice was created (if authorize and capture) and invoice email received.</li>
<li>Pick all the products with Postman.</li>
<li>Check in.</li>
<li>Make a dispense.</li>
<li>Go the order, and select  <strong>[!UICONTROL Create returns]</strong></li>
<li>Create the RMA with part of the ordered products.</li>
</ol>
<td>
<ul>
<li>RMA created and displayed below the <strong>[!UICONTROL Returns]</strong> tab on the Order view.</li>
<li>Customer received the RMA confirmation email.</li>
<li>After creating RMA, get the RMA authorization: From the Admin, go to <strong>[!UICONTROL Sales > Returns]</strong>. Select the RMA that you created and authorize it.</li>
<li>Verify that customer received the RMA authorization confirmation email.</li>
<li>Check that the refund was added to the transactions and order history.</li>
</ul>
</td>
</tr>
</table>


### Store Fulfillment App permissions

This section of the test plan covers the account management for Store Fulfillment App Users.

- Confirm that a Store Associate can authenticate with a new user account created from the Adobe Commerce Admin.
- Confirm that updates to existing accounts are successfully applied.

**Functional area:** Adobe Commerce Admin</br>
**Role:** Admin, Store Associate</br>
**Test type:** All positive

<table style="table-layout:auto">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Expected Results</th>
</tr>
<tr>
<td><strong>User Account Management - Create Account</strong></br></br>
</td>
<td>
<ol>
<li><strong>Admin</strong> — Log into the Adobe Commerce Admin</li>
<li>Go to <strong>[!UICONTROL System] > Store Fulfillment App Permissions > All Store Fulfillment App Users</strong></li>
<li><strong>Add New User.</strong></li>
</ol>
<td>
<ul>
<li>Account successfully created.</li>
<li>New User account is displayed on the [!UICONTROL Store Fulfillment Users] dashboard.</li>
<li><strong>Store Associate</strong> log in to the Store Assist app with new user account.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>User Account Management - Update existing user account</strong>
</td>
<td>
<ol>
<li>Log into the Adobe Commerce Admin with Admin user account.</li>
<li>Go to <strong>[!UICONTROL System] > Store Fulfillment App Permissions > All Store Fulfillment App Users</strong>.</li>
<li>In the User account list, open an existing active User account by selecting <strong>[!UICONTROL Edit]</strong>.
<li>Disable the account by changing <strong>[!UICONTROL Is Active]</strong> to <strong>No</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>On the <strong>[!UICONTROL Store Fulfillment App Users]</strong> dashboard, the status for the updated account changed to <strong>[!UICONTROL Inactive]</strong>.</li>
<li>Store Associate cannot log in to the Store Assist app with the inactive account credentials.</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce Product types

The test scenarios for Adobe Commerce Product Types verify that customers see the correct product, stock, and delivery method information for different product types:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] in the Adobe Commerce storefront.

**Functional area:** Adobe Commerce Frontend</br>
**Role:** Store Assist App User (Store Associate)</br>
**Test type:** All positive

<table style="table-layout:auto">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Comments</th>
</tr>
<tr>
<td><strong>Configurable products</strong>
</td>
<td>
<ul>
<li>Verify that user can see only those configurable options, which source is enabled, stock is assigned and that there are some items in stock—check child products.</li>
<li>Verify that when selecting a different store, options that are not available are shown as crossed out.</li>
<li>Verify that if user selects different store, configurable options get unselected.</li>
<li>Verify that if a configurable product is already in cart, and a user selects different store, the product show as out of stock.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Grouped products</strong>
</td>
<td>
<ul>
<li>Verify that the  Delivery methods and [!UICONTROL Add to cart] button are disabled for the customer when all child products have
<code>qty</code> set to <code>0</code>.</li>
<li>Verify that the Delivery methods are enabled for the customer when at least one of child products has <code>qty</code> set to <code>0.</code></li>
<li>Verify that [!UICONTROL Store Pickup Delivery] method is visible and active only for the products which have [!UICONTROL Available for Store Pickup] enabled. (Check child product.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Virtual products</strong>
</td>
<td>
Verify that virtual products do not offer the  [!UICONTROL In-store Pickup] delivery method.
<td></td>
</td>
</tr>
<tr>
<td><strong>Bundle products</strong>
</td>
<td>
<ul>
<li>Verify that if at least one child product has [!UICONTROL Available for Store Pickup] disabled, the Store Pickup delivery option is not available to the customer.</li>
<li>Verify that if at least one child product has [!UICONTROL Available for Home Delivery] disabled, the Home Delivery option is not available for the customer.</li>
<li>Verify if at least one of the child products in a bundle is out of stock, the bundle (parent product) is also shown
as [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Check-In Experience

This section of the test plan covers the Check-In Experience for Store Pickup orders for the following capabilities:

- Alternate pickup contact—Verify the workflow for adding an [!UICONTROL Alternate Pickup Contact] and selecting a [!UICONTROL Preferred Contact] on Store Pickup orders.

- Check-in form—Verify the workflow for submitting a check-in request for Store pickup orders.

**Functional areas:** Cart Checkout, Check-In Form for store pickup orders</br>
**Role:** Admin, Customer, Store Associate</br>
**Test type:** All positive

### Alternate Pickup Contact


**Functional area:** Cart Checkout</br>
**Role:** Customer</br>
**Test type:** All positive

<table style="table-layout:auto">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Expected Results</th>
</tr>
<tr>
<td><strong>Alternate Pickup Contact</br>
Check-In<strong>
</td>
<td>
A customer submits an order with the In-Store Pickup option.</td>
<td>During the checkout process, the customer sees the [!UICONTROL Alternate Pickup Contact] the option on the Shipping step.
</td>
</tr>
<tr>
<td><strong>Alternate Pickup Preferred Contact, Check in</strong>
<td>
A customer submits an order with the In-Store Pickup option. During checkout, the customer adds an [!UICONTROL Alternate Pickup Contact].</td>
<td>During the checkout process, the customer sees the [!UICONTROL Preferred Contact] option on the shipping step.</td>
</td>
</tr>
<tr>
<td><strong>Alternate Pickup Contact Details, Check in</strong>
</td>
<td>
A customer submits an order with the In-Store Pickup option. During checkout, the customer selects [!UICONTROL Alternate Pickup Contact] on the shipping step.
</td>
<td>The customer sees input options to enter contact details: [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone], and [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Alternate Pickup, Check in Email</strong>
</td>
<td>A customer submits an order with the In-Store Pickup option. During checkout, the customer selects [!UICONTROL Alternate Pickup Contact] on the shipping step, adds the contact details, and submits the order.</td>
<td>Both the customer and the alternate contact receive a Check-In Email for the order.</td>
</tr>
<td><strong>Alternate Pickup, Order detail</strong></td>
<td>A customer submits an order with the In-Store Pickup option. During checkout, the customer selects [!UICONTROL Alternate Pickup Contact] on the shipping step, adds the contact details, and submits the order.</td>
<td>Admin sees the additional contact information on the saved order.</td>
</tr>
<tr>
<td><strong>Alternate Pickup Contact, Store Associate order view</strong>
</td>
<td>A customer submits an order with the In-Store Pickup option. During checkout, the customer selects [!UICONTROL Alternate Pickup Contact] on the shipping step, adds the contact details, and submits the order.</td>
<td>The Store Associate can see the additional contact information on the order in FaaS/ChaaS.</td>
</td>
</tr>
</tbody>
</table>

### Check-in Form


**Functional area:** Check-In Form</br>
**Role:** Customer</br>
**Test type:** All positive

<table style="table-layout:auto">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Expected Results</th>
</tr>
<tr>
<td><strong>Check in Action—Submit request</strong>
</td>
<td>On the check-in form, a customer completes all required fields, and submits the request.</td>
<td>Customer receives a success response.</td>
</tr>
<tr>
<td><strong>Check in Action—View request details</strong></td>
<td>A customer successfully submits a check-in request.</td>
<td>The order status updates in the FaaS system, and the Store Associate can see the check-in request details in the FaaS.
</td>
</tr>
<tr>
<td><strong>Check in Action—Submit request only once</strong></td>
<td>After submitting a check-in request for an order, a customer selects the link to check-in a second time.</td>
<td>On the Check-In form, the customer does not see an option to edit or resubmit the form.</td>
</tr>
<tr>
<td><strong>Check in Action—Confirm Arrival</strong></td>
<td>An in-store pickup order is marked ready for pickup in the FaaS. The customer receives a Ready for Pickup email, and selects [!UICONTROL Confirm Arrival].</td>
<td>The customer sees the Check-In form for the order.</td>
</tr>
</tbody>
</table>

## Store Assist app

This section of the test plan covers scenarios for testing order, pick, and handoff workflows in the Store Assist App.

**Functional area:** Store Assist App</br>
**Role:** Store Associate</br>
**Test type:** All positive

<table style="table-layout:auto">
<tr>
<th>Function</th>
<th>Scenario</th>
<th>Expected Results</th>
</tr>
<tr>
<td>
<strong>Single order picking—happy path, curbside pickup</strong></td>
<td>Pick single and multi-quantity items. No nil picks, and curbside pickup (with staging).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Multi order picking—happy path, curbside pickup</strong></td>
<td>Single and multi-quantity items. No nil picks, and curbside pickup (with staging)</td>
<td></td>
</tr>
<tr>
<td><strong>Single order picking—happy path in-store pickup</strong></td>
<td>Single and multi-quantity items. No nil picks, and in-store pickup (with staging)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Multi order picking—happy path, in-store pickup</strong></td>
<td>Pick single and multi-quantity items. No nil picks, and curbside pickup (with staging).</td>
<td></td>
</tr>
<tr>
<td><strong>Single order picking—not happy path, in-store pickup</strong></td>
<td>Pick single and multi-quantity items with partial and nilpick and in-store pickup (with staging)</td>
</td>
<td></td>
</tr>
<td><strong>Multi order picking—not happy path–curbside pickup</strong></td>
<td>Pick single and multi-quantity items with partial and nilpick and in-store pickup (with staging)</td>
<td></td>
</tr>
<td><strong>Single order picking—not happy path, curbside pickup</strong></td>
<td>Pick single and multi-quantity items with partial and nilpick and curbside pickup (with staging)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Order placed - canceled before picking</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Order placed - canceled before handoff</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Order placed - search in order module</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Order placed - search and manual check in for handoff</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Order placed - all items nilpicked or not available marked by the picker</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Order placed with bundle items -picking and handoff</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Order placed - Hand off with rejection</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Order placed - Hand off with rejection of all items</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## Deploy

After you have verified that the solution has been configured and tested to your specifications, you are ready to deploy from staging to production.

Deployment and testing vary depending on your infrastructure and capabilities.

>[!TIP]
>
>For deployment guidelines, checklists, and best practices for Adobe Commerce on cloud infrastructure projects, see [Deploy your store](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in the Adobe Commerce Developer documentation.
