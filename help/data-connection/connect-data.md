---
title: Connect Commerce Data to Adobe Experience Platform
description: Learn how to connect your Commerce data to the Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
---
# Connect Commerce data to Adobe Experience Platform

When you install the [!DNL Data Connection] extension, two new configuration pages appear in the **System** menu under **Services** in the Commerce _Admin_.

- Commerce Services Connector
- [!DNL Data Connection]

To connect your Adobe Commerce instance to the Adobe Experience Platform, you must configure both connectors, starting with the Commerce Services connector then finishing with the [!DNL Data Connection] extension.

## Configure the Commerce Services connector

If you have previously installed an Adobe Commerce service, you probably have already configured the Commerce Services connector. If not, then you must complete the following tasks on the [Commerce Services connector](../landing/saas.md) page:

1. Log in to your Commerce account to [retrieve your production and sandbox API keys](../landing/saas.md#credentials).
1. Select a [SaaS data space](../landing/saas.md#saas-configuration).
1. Log in to your Adobe account to [retrieve your Organization ID](../landing/saas.md#ims-organization-optional).

After you configure the Commerce Services connector, you then configure the [!DNL Data Connection] extension.

## Configure the [!DNL Data Connection] extension

In this section, you learn how to configure the [!DNL Data Connection] extension.

### Add service account and credential details

If you plan to collect and send [historical order data](#send-historical-order-data) or [customer profile data](#send-customer-profile-data), you must add service account and credential details. Also, if you are configuring the [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) extension, you must complete these steps.

If you are only collecting and sending storefront or back office data, you can skip to the [general](#general) section.

#### Step 1: Create a project in Adobe Developer Console

Create a project in the Adobe Developer Console that authenticates Commerce so it can make Experience Platform API calls.

To create the project, follow the steps outlined in the [Authenticate and access Experience Platform APIs](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) tutorial.

As you go through the tutorial, ensure that your project has the following:

- Access to the following [product profiles](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **Default production all access** and **AEP Default all access**.
- The correct [roles and permissions are configured](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- If you decided to use JSON Web Tokens (JWT) as your server-to-server authentication method, you must also upload a private key.

The result of this step creates a configuration file that you use in the next step.

#### Step 2: Download configuration file

Download the [workspace configuration file](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Copy and paste the contents of this file into the **Service Account/Credential details** page of the Commerce Admin.

1. In the Commerce Admin, navigate to **Stores** > Settings > **Configuration** > **Services** > **[!DNL Data Connection]**.

1. Select the server-to-server authorization method that you implemented from the **Adobe Developer Authorization Type** menu. Adobe recommends using OAuth. JWT has been deprecated. [Learn more](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (JWT only) Copy and paste the contents of your `private.key` file into the **Client Secret** field. Use the following command to copy the contents.

   ```bash
   cat config/private.key | pbcopy
   ```

   See [Service Account (JWT) Authentication](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) for more information about the `private.key` file.

1. Copy the contents of the `<workspace-name>.json` file into the **Service Account/Credential details** field.

    ![[!DNL Data Connection] Admin Configuration](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Click **Save Config**.

### General

1. In the Admin, go to **System** > Services > **[!DNL Data Connection]**.

1. On the **Settings** tab under **General**, verify the ID associated with your Adobe Experience Platform account, as configured in the [Commerce Services Connector](../landing/saas.md#organizationid). The organization ID is global. Only one organization ID can be associated per Adobe Commerce instance.

1. In the **Scope** drop-down, set the context to **Website**.

1. (Optional) If you already have an [AEP Web SDK (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) deployed to your site, enable the checkbox and add the name of your AEP Web SDK. Otherwise, leave these fields blank and the [!DNL Data Connection] extension deploys one for you.

    >[!NOTE]
    >
    >If you specify your own AEP Web SDK, the [!DNL Data Connection] extension uses the datastream ID associated with that SDK and not the datastream ID specified on this page (if any).

### Data collection

In this section, you specify the type of data you want to collect and send to the Experience Platform edge. There are three types of data:

- **Behavioral** (client-side data) is data captured on the storefront. This includes shopper interactions, such as `View Page`, `View Product`, `Add to Cart`, and [requisition list](events.md#b2b-events) information (for B2B merchants).

- **Back office** (server-side data) is data captured in the Commerce servers. This includes information about the status of an order, such as if an order was placed, canceled, refunded, shipped, or completed. It also includes [historical order data](#send-historical-order-data).

- **Profile** is data related to your shopper's profile information. Learn [more](#send-customer-profile-data).

To ensure that your Adobe Commerce instance can begin data collection, review the [prerequisites](overview.md#prerequisites).

See the events topic to learn more about [storefront](events.md#storefront-events), [back office](events-backoffice.md), and [profile](events-backoffice.md#customer-profile-events-server-side) events.

>[!NOTE]
>
>All fields in the **Data collection** section apply to the **Website** scope or higher.

1. Select **Storefront events** if you want to send storefront behavioral data.

1. Select **Back office events** if you want to send order status information, such as if an order was placed, canceled, refunded, or shipped.

    >[!NOTE]
    >
    >If you select **Back office events**, all back office data is sent to the Experience Platform edge. If a shopper chooses to opt out of data collection, you must explicitly set the shopper's privacy preference in the Experience Platform. This is different from storefront events where the collector already handles consent based on shopper preferences. Learn [more](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) about setting a shopper's privacy preference in the Experience Platform.

1. (Skip this step if you are using your own AEP Web SDK.) [Create](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) a datastream in the Adobe Experience Platform or select an existing datastream you want to use for collection. Enter that datastream ID in the **Datastream ID** field.

1. Enter the **Dataset ID** that you want to contain your Commerce data. To find the dataset ID:

    1. Open the Experience Platform UI and select **Datasets** in the left-navigation to open the **Datasets** dashboard. The dashboard lists all available datasets for your organization. Details are displayed for each listed dataset, including its name, the schema the dataset adheres to, and status of the most recent ingestion run.
    1. Open the dataset associated with your datastream.
    1. In the right-hand pane, view the details about the dataset. Copy the dataset ID.

1. To ensure back office event data updates based on a schedule according to a [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) job, you must change the `Sales Orders Feed` index to `Update by Schedule`.

    1. On the _Admin_ sidebar, go to **[!UICONTROL System]** > _[!UICONTROL Tools]_ > **[!UICONTROL Index Management]**.

    1. Select the checkbox for the `Sales Orders Feed` indexer.

    1. Set **[!UICONTROL Actions]** to `Update by Schedule`.

    1. If you are enabling back office data for the first time, run the following commands to reindex and trigger a resync. Subsequent resyncs occur automatically as long as the [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) job is set up correctly.

        ```bash
        bin/magento index:reindex sales_order_data_exporter_v2
        ```

        ```bash
        bin/magento saas:resync --feed orders
        ```

#### Field descriptions

| Field | Description |
|--- |--- |
| Scope | Specific website where you want the configuration settings to apply. |
| Organization ID (global)| ID that belongs to the organization that purchased the Adobe DX product. This ID links your Adobe Commerce instance to Adobe Experience Platform. |
|Is the AEP Web SDK already deployed to your site|Select this checkbox if you have deployed your own AEP Web SDK to your site|
|AEP Web SDK Name (global)| If you already have an Experience Platform Web SDK deployed to your site, specify the name of that SDK in this field. This allows the Storefront Event Collector and Storefront Event SDK to use your Experience Platform Web SDK rather than the version deployed by the [!DNL Data Connection] extension. If you do not have an Experience Platform Web SDK deployed to your site, leave this field blank, and the [!DNL Data Connection] extension deploys one for you.|
|Storefront events|Is checked by default as long as the Organization ID and datastream ID are valid. Storefront events collect anonymized behavioral data from your shoppers as they browse your site.|
|Back office events| If checked, event payload contains anonymized order status information, such as if an order was placed, canceled, refunded, or shipped. |
|Datastream ID (website) | ID that allows data to flow from Adobe Experience Platform to other Adobe DX products. This ID must be associated to a specific website within your specific Adobe Commerce instance. If you specify your own Experience Platform Web SDK, do not specify a datastream ID in this field. The [!DNL Data Connection] extension uses the datastream ID associated with that SDK and ignores any datastream ID specified in this field (if any).|
|Dataset ID (website) | ID of the dataset that contains your Commerce data. This field is required unless you have deselected the **Storefront events** or **Back office events** checkboxes. Also, if you are using your own Experience Platform Web SDK and therefore did not specify a datastream ID, you must still add the dataset ID associated with your datastream. Otherwise, you cannot save this form.|

After onboarding, storefront data begins to flow to the Experience Platform edge. Back office data takes about five minutes to appear at the edge. Subsequent updates are visible at the edge based on the cron schedule.

### Send customer profile data

There are two types of profile data that you can send to the Experience Platform: profile records and time series profile events.

A profile record contains data that is saved when a shopper creates a profile in your Commerce instance, such as the shopper's name. When your schema and dataset are [properly configured](profile-data.md), a profile record is sent to the Experience Platform and forwarded to Adobe's profile management and segmentation service: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

Time series profile events contain data about your shopper's profile information, such as if they create, edit, or delete an account on your site. When profile event data is sent to the Experience Platform, it resides in a dataset where it can be used by other DX products.

1. Make sure you have [provided](#add-service-account-and-credential-details) service account and credential details.

1. Make sure you have a schema and dataset specified for [profile record data ingestion](profile-data.md) and [time series profile event data ingestion](update-xdm.md#time-series-profile-event-data).

1. Place a checkmark in the **Customer profiles** checkbox if you want to send profile data to the Experience Platform.

1. Enter the **Profile Dataset ID**.

    Profile record data must use a different dataset than what you are currently using for behavioral and back office event data.

1. If you do not want to stream profile events through the same datastream ID that you are using for behavioral and back office data, remove the checkmark from the **Stream customer profiles through same datastream ID** and enter the datastream ID you want to use instead.

It can take about 10 minutes for a profile record to be available in Real-Time CDP. Profile events begin streaming immediately.

>[!TIP]
>
>If you are not seeing profile data in the Experience Platform, see the [Commerce KnowledgeBase](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) for troubleshooting suggestions.

#### Field descriptions

| Field | Description |
|--- |--- |
|Customer profiles|Select this checkbox if you want to collect and send customer profile records.|
|Profile Dataset ID|A profile record must use a different dataset than the dataset used for behavioral and back office events.|
|Stream customer profiles through same datastream ID|Decide if you want to use the same datastream currently used for your behavioral and back office events or not.|
|Datastream for customer profiles|Specify the customer profile record-specific datastream.|

### Send historical order data

Adobe Commerce collects up to five years of [historical order data and status](events-backoffice.md#back-office-events). You can use the [!DNL Data Connection] extension to send that historical data to the Experience Platform to enrich your customer profiles and personalize the customer experiences based on those past orders. The data is stored in a dataset within Experience Platform.

While Commerce already collects the historical order data, there are several steps you must complete to send that data to Experience Platform.

Watch this video to learn more about historical orders then complete the following steps to implement historical order collection.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### Set up the Order Sync service

The order sync service uses the [Message Queue Framework](https://developer.adobe.com/commerce/php/development/components/message-queues/) and RabbitMQ. After you complete these steps, order status data can sync to SaaS, which is required before it is sent to Experience Platform.

1. Make sure you have [provided](#add-service-account-and-credential-details) service account and credential details.

1. [Enable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

    >[!NOTE]
    >
    >RabbitMQ is already set up for Commerce versions 2.4.7 and newer, but you must enable consumers.

1. Enable message queue consumers by cron job in `.magento.env.yaml` using `CRON_CONSUMERS_RUNNER` environment variable.

    ```yaml
       stage:
         deploy:
           CRON_CONSUMERS_RUNNER:
             cron_run: true
    ```

    >[!NOTE]
    >
    >See the [deploy variables documentation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) to learn about all the available configuration options.

With the order sync service enabled, you can then specify the historical order date range in the **[!UICONTROL [!DNL Data Connection]]** page.

#### Specify order history date range

Specify the date range for the historical orders that you want to send to Experience Platform.

1. In the Admin, go to **System** > Services > **[!DNL Data Connection]**.

1. Select the **Order History** tab.

1. Under **Order History Sync**, the **Copy Dataset ID from Settings** checkbox is already enabled. This ensures you are using the same dataset specified in the **Settings** tab.

1. In the **From** and **To** fields, specify the date range for the historical order data you want to send. You cannot select a date range that exceeds five years.

1. Select **[!UICONTROL Start Sync]** to trigger the sync to begin. Historical order data is batched data as opposed to storefront and back office data that is streaming data. Batched data takes about 45 minutes to arrive in Experience Platform.

##### Field descriptions

| Field | Description |
|--- |--- |
| Copy Dataset ID from Settings | Copies the dataset ID you entered on the **Settings** tab.|
|Dataset ID (website) | ID of the dataset that contains your Commerce data. This field is required unless you have deselected the **Storefront events** or **Back office events** checkboxes. Also, if you are using your own Experience Platform Web SDK and therefore did not specify a datastream ID, you must still add the dataset ID associated with your datastream. Otherwise, you cannot save this form.|
| From | Date from which you want to begin collecting order history data.|
| To |  Date from which you want to end collecting order history data.|
| Start Sync | Begins the process of syncing the order history data to the Experience Platform edge. This button is disabled if the **[!UICONTROL Dataset ID]** field is blank or the dataset ID is invalid.|

### Data Customization

On the **Data Customization** tab, you can view any custom attributes configured in [!DNL Commerce] and sent to Experience Platform.

>[!IMPORTANT]
>
>Ensure that the datastream ID you [specified](#data-collection) on the **Data Collection** tab matches the ID linked to the schema for ingesting custom attributes.

When creating custom attributes for orders and sending them to the Experience Platform, the attribute names in Commerce must match those in the [!DNL Commerce] schema on the Experience Platform. If they do not match, it can be difficult to identify the differences. If you have mismatched names, the **Custom Order Attributes** table can help solve the problem.

![Custom Order Attributes](assets/custom-order-attribute.png)

The **Custom Order Attributes** table provides visibility into the configuration and mapping of custom order attributes between the [!DNL Commerce] back office and the [!DNL Commerce] schema in Experience Platform. This table allows you to view order level and order item level custom attributes across different sources, making it easier to identify missing or misaligned attributes. It also displays dataset IDs to help differentiate between live and historic datasets, as each can have its own custom attributes.

If you do not see a green checkmark next to a custom attribute name in the table, it indicates a mismatch between attribute names in the sources. Correct the attribute name in one source, and a green checkmark will appear, indicating that the names now match.

- If the attribute name is updated in the schema in Experience Platform, you must save the configuration on the **Data Customization** tab to trigger the Experience Platform schema change. This change will be reflected in the  **Custom Order Attributes** table when you click the **[!UICONTROL Refresh]** button.
- If the attribute name is updated in [!DNL Commerce], an order event must be generated to update the name in the **Custom Order Attributes** table. The change will be reflected in about 60 minutes.

Learn more about how to [set up custom attributes](custom-attributes.md).

#### Field descriptions

| Field | Description |
|--- |--- |
|Scope | Switches storeviews. You can see different datasets and the corresponding custom attributes based on the storeview selected.|
|Dataset | Displays the datasets that contain the custom attributes. Live and historic datasets can have their own custom attributes.|
|Adobe Commerce | Displays any custom attributes created in the [!DNL Commerce] back office.|
|Experience Platform | Displays any custom attributes specified in your [!DNL Commerce] schema in Experience Platform.|
|Refresh|Retrieves any custom attribute names from the [!DNL Commerce] schema in Experience Platform. |

## Confirm that event data is collected

To confirm that data is being collected from your Commerce store, use the [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) to examine your Commerce site. After you confirm that data is being collected, you can verify that your storefront and back office event data appears at the edge by running a query that returns data from the [dataset you created](overview.md#prerequisites).

1. Select **Queries** in the left navigation of Experience Platform and click [!UICONTROL Create Query].
    
    ![Query Editor](assets/query-editor.png)

1. When the Query Editor opens, enter a query that selects data from the dataset.

    ![Create query](assets/create-query.png)

    For example, your query might look like the following:

    ```sql
    SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
    ```

1. After the query runs, the results are displayed in the **Results** tab, next to the **Console** tab. This view shows the tabular output of your query.

    ![Query Editor](assets/query-results.png)

In this example, you see event data from the [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview), and so on. This view allows you to verify that your Commerce data arrived at the edge.

If the results are not what you expect, open your dataset and look for any failed batches imports. Learn more about [troubleshooting batch imports](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

### Verify profile data appears in the Experience Platform

If you are not seeing profile data in the Experience Platform, see the [Commerce KnowledgeBase](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) for troubleshooting suggestions.

## Next steps

When Commerce data is sent to the Experience Platform edge, other Adobe Experience Cloud products, such as Adobe Journey Optimizer, can use that data. For example, you can configure Journey Optimizer to listen to certain events, and based on that event data, trigger an email for a first-time user or if there is an abandoned cart. Learn how you can extend your Commerce platform by [creating customer journeys](using-ajo.md) in Journey Optimizer.
