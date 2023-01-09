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

*  Up to ten conditions
*  Up to 25 events

Query text can contain:

*  Alphanumeric characters (Letters and numbers)
*  Either upper or lowercase characters. Capitalization is ignored.

## Logical Operators

The logical operators `AND` and `OR` join two conditions and return different results. All logical operators used in a rule with multiple conditions are the same. It is not possible to use both `AND` and `OR` in the same rule.

### Match Operators

The Match operators `All` and `Any` determine the logical operator that is used to join multiple conditions in the rule, and can be used to change the existing operator.

*  `All` - Uses the `AND` logical operator to join multiple conditions. A rule that uses the `All` Match operator can have only one `Search query is` condition.
*  `Any` - Uses the `OR` logical operator to join multiple conditions.

When composing a complex rule, it can help to write it out with indentation to describe the conditions, associated events, and product names or SKUs that are needed to return the results you want to achieve. Then, build the rule and test the result.
