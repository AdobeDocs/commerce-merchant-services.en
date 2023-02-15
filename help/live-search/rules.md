---
title: "Rules"
description: "[!DNL Live Search] rules combine logic with actions to shape the shopping experience."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
---
# Rules

[!DNL Live Search] rules combine logic with actions to shape a shopper's search experience in your store. You can use rules to boost, bury, pin, or hide products to calibrate search results in real time to support your business goals.

Each rule has three main components:

* Conditions – The conditions that trigger an action.
* Events – The actions that take place when the conditions are met.
* Details – The name of the rule, and optional time frame and description.

You can combine multiple conditions and actions, and schedule a rule to be active for a period.

## Requirements

A simple rule can have a single condition and a single event, while a complex rule can have up to ten conditions that trigger up to 25 events.
Rules can have:

* Up to ten conditions
* Up to 25 events

Query text can contain:

* Alphanumeric characters (Letters and numbers)
* Either upper or lowercase characters. Capitalization is ignored.

## Logical Operators

The logical operators `AND` and `OR` join two conditions and return different results. All logical operators used in a rule with multiple conditions are the same. It is not possible to use both `AND` and `OR` in the same rule.

### Match Operators

The Match operators `All` and `Any` determine the logical operator that is used to join multiple conditions in the rule, and can be used to change the existing operator.

* `All` - Uses the `AND` logical operator to join multiple conditions. A rule that uses the `All` Match operator can have only one `Search query is` condition.
* `Any` - Uses the `OR` logical operator to join multiple conditions.

When composing a complex rule, it can help to write it out with indentation to describe the conditions, associated events, and product names or SKUs that are needed to return the results you want to achieve. Then, build the rule and test the result.

## Order of precedence with multiple rules

Only one rule is applied to a search term at any one time.
If multiple rules are found to be applicable to a search phrase, then all these rules are applied. If there is a collision between two rules: `rule 1` that boosts sku1 but `rule 2` hides the same sku, then the most recently applied rule (`rule 2`) will take precedence.

* Rules are orderd by the "Last Modified" timestamp. The most recently modified rule is applied first, and older rules after that, in timestamp order.
* The `query is` condition will take precedence over other conditions. If a newer rule contains a `query contains` condition, but an older rule has a `query is` condition, the `query is` rule will be applied.

### Storefront requests

If an active rule containing a `query is` condition matches the search phrase, it will be applied. If there are multiple matching rules with a `query is` condition, the most recently updated active rule will be applied.
Otherwise, the most recently updated active rule will be applied.

### Preview requests

Request made in the Admin work slightly differently. When previewing in the admin, all rules are applied, including those expired and scheduled.

* If rule being previewed has a `query is` condition, it will be applied.
* If rule being previewed does not have a `query is` condition, and a subsequent active, matching rule with a `query is` condition is found, the `query is` rule will be applied.
* If rule being previewed does not have a `query is` condition, and no other rule with a `query is` condition is found, then the rule being previewed will be applied.

## Category rules and category product assignments

Live Search allows you to filter by Categories.
However, in Adobe Commerce you can create a "virtual category" with [Category product assignments](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). This type of category is built at runtime and does not exist in the category database. Therefore, Live Search cannot read or use this category type.
