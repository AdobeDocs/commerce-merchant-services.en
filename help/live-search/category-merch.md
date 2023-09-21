---
title: "Category Merchandising"
description: "Use [!DNL Live Search] Category Merchandising for a faster shopping experience."
gourl: ls_catalog_merchandising
---

# Category Merchandising

Category Merchandising allows store owners to apply [!DNL Live Search] Intelligent ranking [rules](rules.md) to product categories and subcategories.

The feature is accessed in the admin at **Marketing** > SEO & Search > **[!DNL Live Search]** > **Category Merchandising**.

>[!NOTE]
>
>Category Merchandising is available with [!DNL Live Search] [3.0.0 or higher](release-notes.md). If you see the Category Merchandising tab but it is not populated with data, update the [!DNL Live Search] module.

![Categry Merchandising](assets/category_workspace.png)

The Category Merchandising view shows defined category rules, with columns for:

* Category
* Ranking Strategy
* Inherited Ranking
* Last Updated
* Action

You can search for a category or subcategory in the "Search by category" field.

## Ranking strategies

Category Merchandising uses the same ranking types as with [individual products](rules-workspace.md).
There are two types of ranking: Intelligent and Manual.

**Intelligent ranking** leverages storefront behavioral data analysis by [Adobe Sensei](https://www.adobe.com/sensei.html) to sort all products within chosen categories by a certain algorithm. Once an Intelligent ranking is chosen, the specific order of products is expected to change over time as the underlying data is reanalyzed by Adobe Sensei on an ongoing basis. For example, top trending products will automatically change over time as shopper preferences change. 
Intelligent ranking methods are:

* Most purchased: ranks products by how frequently they were purchased by shoppers in the previous seven days.
* Most added to cart: ranks products by how frequently they were added to cart by shoppers in the previous seven days.
* Most viewed: ranks products by how frequently they were viewed by shoppers in the previous seven days.
* Recommended for you: based on each shopper's previous and current on-site behavior, ranks products by how likely the shopper is to interact with each one.
* Trending: ranks products by recent upswings in popularity based on views.
* None: ranks products by their default order.

**Manual ranking** allows users to override the automatic product sort order by defining manual pin, boost, bury, and hide rules. 

## Inherited ranking

As a merchandiser, you might want to be able to select all of women's wear categories to be sorted by "trending". This includes the subcategories "Women's pants", "Women's shirts", and "Women's accessories". Men's categories should not be affected. You can use inherited rankings to achieve this.

When selecting an Intelligent ranking method for a category or subcategory that has subcategories, you can turn on the **Apply intelligent rankings to subcategories** option. This applies the ranking method to all subcategories.

These subcategories now inherit that rule from the parent category ("Yes" in the Inherited Ranking column). In the Action column, the only available options are **Edit Rule**, and **View Details**. The **Delete** option is disabled for inherited rules on subcategories. Deleting subcategory inheritance requires undoing inheritance from the parent category.

Any category or subcategory can have only one Intelligent ranking applied at any one time. They may have additional Manual rankings applied as well.

If you apply an Intelligent ranking to a category and turn on the **Apply intelligent ranking to subcategories** option, any Intelligent ranking already applied to the subcategories are overwritten.

![Overwritten subcategory list](assets/category_overwite_subs.png){width="700"}

If you click **View All**, a dialog opens with details of the proposed changes.

![Ranking changes details](assets/category_overwrite.png)

When adding an Intelligent ranking directly to a category that has an inherited Intelligent ranking, the inheritance is overridden by the new Intelligent ranking. 

When deleting the Intelligent ranking from the category, the inheritance is re-established.
In both scenarios, any Manual rankings are maintained.

If you remove an Intelligent ranking from a category, and the subcategory inheritance is selected, only the inherited Intelligent rankings are removed from the subcategories. Manual rankings are not subject to inheritance and will remain.

A dialog appears explaining which inherited subcategories are affected by any changes you make to a higher-level category.

![Ranking changes modal dialog](assets/category_overwrite_modal.png){width="1200"}

## Create a category rule

To create a category rule:

1. Click the **Add Rule** button.
1. In the _Select Category_ view, click through the categories and subcategories.
1. Select the checkbox to select the category you wish to rank.
1. Click **Apply**.

    ![Select a category](assets/category_select.png)

1. In the _Add Category rule_ view, select the Intelligent ranking method you wish to apply to the category.
   The Category Preview Page shows the actual results of the selected ranking, using your Live Search data.
1. Click **Save and Publish** to save the rule.

  ![Select the Intelligent ranking method](assets/category_ranking.png)

The [!DNL Live Search] service processes the rule and activates it on the store when finished.

## Modify a category rule

To modify an existing rule:

1. Click the **...** in the Action column and choose **Edit**.
1. In the Edit Category rule view, make any required changes and click **Save and Publish**.

The changes are reflected on the store when [!DNL Live Search] has processed the change.

## Delete a category rule

To delete a category rule:

1. Click the **...** in the Action column and choose **Delete**.
1. In the _Delete rule_ modal, select **Delete** to remove the rule or **Cancel** to cancel the action.

## Manual ranking

Manual ranking lets you override the product order determined by Intelligent Ranking rules (if any) and manually control where products appear within the results.

Events are actions that modify the search results when defined conditions are met. A manual ranking can have up to 25 events.

* Boost: Moves a product higher in the search results.
* Bury: Moves a product lower in the search results.
* Pin a product: Moves a product to a specific position in results.
* Hide a product: Excludes a product from the search results.

Create a manual ranking:

1. Set up an Intelligent ranking rule for a category as described above. The results of the query will appear in the Preview Category Page view. This uses your actual Live Search data to preview the results.

1. Click and drag a product in the Preview Category Page view. Drag and drop it at the desired position. The Product and Position fields are automatically populated in the Events pane.
  
  You may also click the pin icon to pin a product to its current location. Use the ellipsis context menu to "Pin to top" or "Pin to bottom".

To manually add an event:

1. Under Manual Ranking, click the **Select an event** menu and choose an event to take place when the associated conditions are met. 
1. Enter the name of the product that you want to affect. Products are suggested as you type.
1. For multiple events, choose any other events that you want to trigger when conditions are met.
