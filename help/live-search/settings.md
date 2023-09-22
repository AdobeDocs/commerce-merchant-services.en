---
title: "[!DNL Live Search] Settings"
description: "Configure settings for the [!DNL Live Search] service."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
---
# Settings

Use the *Settings* tab to configure the price facet ranges and intervals and the default language for the index. 

Price faceting specifies the number of price range groups and how price values are distributed among them.

Language settings tell the [!DNL Live Search] service which language to expect when writing the index.

![Settings](assets/settings.png)

## Price faceting

You can specify the number of price range groups and how price values are distributed among them. Each price range overlaps the previous group by one. For example, five groups with an interval of 20 creates the following price ranges: 0-20, 20-40, 40-60, 60-80, and >80. If there are not enough products in the catalog to fill all defined ranges, the display of the available groups is adjusted accordingly. For example: 0-20, 60-80, >80.

1. In the Admin, go to **Marketing** > *SEO & Search* > **[!DNL Live Search]**.
1. On the **Settings** tab under *Price faceting*, do the following:
   * Enter the **Number of selections**, or price groupings to be available. Up to 50 price groupings can be defined.
   * Enter the **Interval value**, or price range for each group. The maximum value is 10,000.
1. Click **Save**.

   It takes about 15 minutes for the updated settings to be available in the storefront.

### Field descriptions

| Field | Description |
|--- |--- |
| Number of selections | Specifies the number of price range groupings that can be used as search filters in the storefront. Default value: 8, Maximum value: 50 |
| Interval value | Specifies the price range interval for each group. For example, five selections with an interval value of 20 creates five groupings of 0-20, 20-40, 40-60, 60-80, and >80. Default value: 5, Maximum value: 10,000 |

## Language

The Language setting tells [!DNL Live Search] which language to expect when reading the catalog and writing the index. 

Languages have different sets of rules for grammar: how words are separated, verb tenses and synonyms, for example.
The Language setting ensures that the correct set of rules are applied to the indexing mechanism.

The Language settings should be set to the primary language of the catalog.
