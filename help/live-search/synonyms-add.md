---
title: "Add Synonyms"
description: "Add [!DNL Live Search] synonyms to improve response to search requests."
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
---
# Add Synonyms

Increase customer engagement by adding your own curated list of [!DNL Live Search] synonyms. [!DNL Live Search] can manage up to 200 synonyms per `Data Space ID`.

![[!DNL Live Search] synonyms](assets/synonym-workspace.png)

## Step 1: Add a synonym

1. In the Admin, go to **Marketing** > SEO & Search > **[!DNL Live Search]**.
1. For multiple stores, set **Scope** to the [store view](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) where the synonym settings apply.
1. Click the **Synonyms** tab.
1. Click the **Add synonyms** button.

## Step 2: Define the synonym by type

Follow the instructions for the [type of synonym](synonyms-type.md) that you want to create.

### Two-way synonym

1. Accept the default **Two-way** option.

   ![Add two-way synonym](assets/synonym-add-two-way.png)


1. Enter the **Keyword** term or phrase to be matched.
1. Enter the **Expansion** term(s) that you want to add as synonyms for the keyword. Separate multiple terms with a comma.
   In this example, the keyword to match is "pants" and the set of expansion terms are "trousers, slacks".

   ![Two-way synonym example](assets/synonym-add-two-way-example.png)

1. When complete, click **Save**.
   The set of synonyms appears in the list with a two-way arrow between each term that means the terms are interchangeable.

   ![Two-way synonym](assets/synonym-two-way.png)

### One-way synonym

1. Click the **One-way** synonym type.

   ![Add one-way synonym](assets/synonym-add-one-way.png)

1. Enter the **Keyword** and **Expansion** terms. Separate multiple terms with a comma.

   ![One-way synonym example](assets/synonym-add-one-way-example.png)

   In this example, the keyword is "pants" and the one-way expansion terms "capris, peddle-pushers" are each a subset of "pants", but with a specific meaning.

1. When complete, click **Save**.
   The set of synonyms appears in the list with a one-way arrow pointing from the expansion terms to the keyword to indicate the terms are subsets of the keyword. A plus sign separates each expansion term.

   ![One-way synonym](assets/synonym-one-way.png)

## Step 3: Publish changes

1. When your synonyms are complete, click **Publish changes**.
1. Wait for up to two hours for your updates to become available in the storefront.

## Field Descriptions

| Field | Description |
|--- |--- |
| [Type](synonyms.md) | Determines if the synonyms have the same meaning as the keyword, or are a subset of the keyword. Options:<br />Two-way (default) - Terms that have the same meaning as the keyword and return the same search results<br />One-way - Terms that are a subset of the keyword. One-way synonyms return a more narrow list of specific products. |
| Keyword | A word that is commonly associated with a selection of products in your catalog. |
| Expansion | Additional terms that have the same or similar meaning as the keyword. |
