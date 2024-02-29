---
title: Create New Recommendation
description: Learn how to create a product recommendation unit.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
---
# Create New Recommendation

When you create a recommendation, you create a _recommendation unit_ that contains the recommended product _items_.

![Recommendation unit](assets/unit.png)
_Recommendation unit_

When you activate the recommendation unit, Adobe Commerce starts to [collect data](workspace.md) to measure impressions, views, clicks, and so on. The [!DNL Product Recommendations] table displays the metrics for each recommendation unit to help you make informed business decisions.

1. On the _Admin_ sidebar, go to **Marketing** > _Promotions_ > **Product Recommendations** to display the _Product Recommendations_ workspace.

1. Specify the [Store View](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) where you want the recommendations to display.

   >[!NOTE]
   >
   > Page Builder recommendation units must be created in the default store view, but then can be used anywhere. To learn more about creating product recommendations with Page Builder, see [Add Content - Product Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Click **Create Recommendation**.

1. In the _Name your Recommendation_ section, enter a descriptive name for internal reference, such as `Home page most popular`.

1. In the _Select page type_ section, select the page where you want the recommendation to appear from the following options:

   >[!NOTE]
   >
   > Product Peccomendation is not supported on the Cart page when your store is configured to [display the shopping cart page immediately after adding a product to the cart](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html?lang=en#redirect-to-cart).

   * Home Page
   * Category
   * Product Detail
   * Cart
   * Confirmation
   * [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   You can create up to five active recommendation units for each page type, and up to 25 for Page Builder. The page type is grayed out When the limit is reached.

   ![Recommendation name and page](assets/create-recommendation.png)
   _Recommendation name and page placement_

1. In the _Select Recommendation type_ section, specify the [type of recommendation](type.md) you want to appear on the selected page. For some pages, the [placement](placement.md) of recommendations is limited to certain types.

1. In the _Storefront display label_ section, enter the [label](placement.md#recommendation-labels) that is visible to your shoppers, such as "Top sellers".

1. In the _Choose number of products_ section, use the slider to specify how many products you want to appear in the recommendation unit.

   The default is `5`, with a maximum of `20`.

1. In the _Select placement_ section, specify the location where the recommendation unit is to appear on the page.

   * At the bottom of main content
   * At the top of main content

1. (Optional) To change the order of the recommendations, select, and move the rows in the _Choose position_ table.

   The _Choose position_ section displays all recommendations (if any) created for the page type you selected.

   ![Recommendation order](assets/create-recommendation-select-placement.png)
   _Recommendation order on page_

1. (Optional) In the _Filters_ section, [apply filters](filters.md) to control which products appear in the recommendation unit.

   ![Recommendation filters](assets/create-recommendation-filter-products.png)
   _Recommendation product filters_

1. When complete, click one of the following:

   * **Save as draft** to edit the recommendation unit later. You cannot modify the page type or recommendation type for a recommendation unit in a draft state.

   * **Activate** to enable the recommendation unit on your storefront.

## Readiness indicators

Some recommendation types use behavioral data from your shoppers to [train machine learning models](behavioral-data.md) to build personalized recommendations. 

Requires only catalog data. No behavioral data is needed for these:

* _Most Like This_
* _Recently Viewed_
* _Visual Similarity_

Based on last six months of storefront behavioral data:

* _Viewed this, viewed that_
* _Viewed this, bought that_
* _Bought this, bought that_
* _Recommended for you_

Popularity-based recommendation types use the last seven days of storefront behavioral data:

* Most Viewed
* Most Purchased
* Added to Cart
* Trending

Readiness indicator values are expected to fluctuate due to factors such as the overall size of the catalog, volume of product interaction events (views, adds to cart, purchases), and percentage of skus that register those events within a certain time window, as listed above. For example, during peak holiday season traffic, the readiness indicators might show higher values than in times of normal volume.

To help you visualize the training progress of each recommendation type, the _Select Recommendation type_ section displays a measure of readiness for each type. These readiness indicators are calculated based on a couple factors:

* Sufficient result set size: Are there enough results being returned in most scenarios to avoid using [backup recommendations](behavioral-data.md#backuprecs)? 

* Sufficient result set variety: Do the products being returned represent a variety of products from your catalog? The goal with this factor is to avoid having a minority of products being the only items recommended across the site. 

Based on the above factors, a readiness value is calculated and displayed. A recommendation type is considered ready to deploy when its readiness value is 75% or higher. A recommendation type is considered partially ready when its readiness is at least 50%. A recommendation type is considered not ready to deploy when its readiness value is less than 50%. These are general guidelines but each individual case can differ based on the nature of collected data as outlined above. 

![Recommendation type](assets/create-recommendation-select-type.png)
_Recommendation type_

>[!NOTE]
>
>Indicators may never reach 100%.

## Preview Recommendations {#preview}

The _Recommended products preview_ panel is always available with a sample selection of products that might appear in the recommendation unit when it is deployed to the storefront.

To test a recommendation when working in a non-production environment, you can fetch recommendation data from a [different source](settings.md). This allows merchants to experiment with rules and preview the recommendations before deploying to production.

|Field|Description|
|---|---|
|Name|The name of the product.|
|SKU|The Stock Keeping Unit assigned to the product|
|Price|The price of the product.|
|Result Type|Primary - indicates that there is enough training data collected to display a recommendation.<br />Backup - indicates that there is not enough training data collected so a backup recommendation is used to fill the slot. Go to [Behavioral Data](behavioral-data.md) to learn more about machine learning models and backup recommendations.|

As you create your recommendation unit, experiment with the page type, recommendation type, and filters to get immediate real-time feedback about the products that will be included. As you begin to understand which products appear, you can configure the recommendation unit to meet your business needs.

Adobe Commerce [filters](filters.md) recommendations to avoid displaying duplicate products when multiple recommendation units are deployed on a single page. As a result, the products that appear in the preview panel might differ from those that appear in the storefront.

>[!NOTE]
>
> You cannot preview the `Recently viewed` recommendation type because the data is not available in the Admin.
