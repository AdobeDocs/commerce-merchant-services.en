---
title: Workspace
description: Learn how to configure, manage, and monitor Product Recommendation performance.
---
# Workspace

The [!DNL Product Recommendations] workspace displays a list of previously configured recommendations with metrics that help you track the success of each recommendation. The list can be configured to calculate metrics for the last day, week, or month. You can use the metrics to create actionable insights based on how frequently a recommendation unit is viewed or clicked, or to analyze how well your recommendations perform.

![Recommendations workspace](assets/workspace.png)
_Recommendations Workspace_

## Set the scope

Initially the [scope](https://docs.magento.com/user-guide/stores/websites-stores-views.html) of all recommendation settings is set to `Default Store View`. If your Commerce installation includes multiple store views, set **Scope** to the [store view](https://docs.magento.com/user-guide/configuration/scope.html) where your recommendations apply.

## Set metrics date range

1. Click the **Calendar** ![Calendar selector](assets/icon-calendar.png) control.

1. Choose one of the following:

   - Last 24 hours
   - Last 7 days
   - Last 30 days

   The calculated values in the metrics columns change to reflect the current date range.

## Show/hide columns

1. In the upper-left corner, click **Show/hide** ![Column selector](assets/icon-show-hide-columns.png) columns.

   The visible columns have a blue check mark.

1. In the menu, do either of the following:

   - To show a hidden column, click any column name without a check mark.
   - To hide a visible column, click any column name with a check mark.

   The table is refreshed to include only the selected columns.

   ![Recommendations workspace](assets/workspace-select-columns.png)
   _Show/hide columns_

## Settings

The settings determine the SaaS data space that provides the recommendation-behavioral data.

- To change where recommendation-behavioral data originates, choose a different SaaS data space.

- To configure a new SaaS data space, click **Edit Configuration**. To learn more, see [Settings](settings.md).

![Recommendations settings](assets/settings.png)
_Recommendations Settings_

## View details

1. In the table, click the recommendation that you want to examine.

   ![Recommendations workspace](assets/recommendation-detail.png)
   _Home Page Conversion Rate Detail_

1. To change the status of the recommendation, click **Activate** or **Deactivate**.

## Edit recommendation

From the recommendation details page, click **Edit**. To learn more, go to [Edit Recommendations](edit.md).

## Create recommendation

From the recommendation details page, click **Create**. To learn more, go to [Create Recommendations](create.md).

## Workspace Controls

|Control|Description|
|---|---|
|![Calendar selector](assets/icon-calendar.png)|Determines the range of time that is used for metrics calculations. Options: 24 hours / 7 days / 30 days|
|![Column selector](assets/icon-show-hide-columns.png)|Determines the columns that appear in the [!DNL Product Recommendations] table.|
|Settings|Determines the SaaS data space where recommendation-behavioral data is fetched, and also enables visual similarity recommendation type.|
|Create Recommendation|Opens the [Create New Recommendation](create.md) page.|

## Column Descriptions

|Column|Description|
|---|---|
|Name|The name of the recommendation.|
|Page|The page where the recommendation appears.|
|Type|The recommendation type.|
|Status|The recommendation status. Options: Inactive/Active/Draft|
|Created|The date the recommendation was created.|
|Last Edited|The date the recommendation was last edited.|
|Impressions|The number of times a recommendation unit is loaded and rendered on a page. A recommendation unit that is below the fold of the browser's viewport is rendered on the page, but not viewed by the shopper. In this case, the rendered unit is counted as an impression, but a view is counted only if the user scrolls the unit into view.|
|vImpressions|(Viewable Impressions) The number of recommendation units that register at least one view.|
|Views|The number of recommendation units that appear in the viewport of the shopper's browser. This event can fire multiple times on a page.|
|Clicks|The sum of the number of times a shopper clicks an item in the recommendation unit and the number of times the shopper clicks the **Add to cart** button in the recommendation unit|
|Revenue|The revenue driven by the recommendation for the current time range.|
|Lt Revenue|(Lifetime Revenue) The lifetime revenue driven by a recommendation.|
|Viewability|The percentage of recommendation units that register for the view.|
|Ctr|(Registered Click Percent) The percentage of unit impressions for the recommendation that register a click.|
|vCtr|(Viewable Registered Click Percent) The percentage of viewable impressions for the recommendation unit that register a click.|
