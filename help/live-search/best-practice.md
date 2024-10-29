---
title: '[!DNL Live Search] Best Practices'
description: Learn the best practices for implementing [!DNL Live Search] in your store.
role: Admin, Developer
exl-id: 69b2c2a6-c8a9-4640-8d2b-08fcd7a96034
---
# Best Practices

This article helps merchandisers enhance their site search functionality, ensuring a seamless and efficient shopper experience that maximizes conversion rates. By following the strategies outlined, you learn how to implement advanced search features, and continuously refine your search tool for optimal performance with Adobe Commerce [!DNL Live Search].

There are several key factors that determine the relevance and effectiveness of search results:

- Well-structured product data ensures that search algorithms can effectively match products to queries. Low quality product data leads to low relevant search results. To directly impact the success of your merchandising strategy:
    - Set up the correct attributes as searchable with their corresponding weight.
    - Make sure that data within those attributes is relevant.
- A well-designed search experience builds trust with customers and instills confidence that they will find what they need.
- Search rules are critical as they can elevate the visibility of certain products based on popularity, new arrivals, promotional criteria or any other merchandising strategy to meet your business requirements.
- Faceted navigation allows shoppers to refine their search and get relevant results quickly.

To manage [!DNL Live Search], go to **Marketing** > *SEO & Search* > **[!DNL Live Search]** in the Adobe [!DNL Commerce] Admin. 

## Optimize your search functionality

In this section, you learn how to optimize your search functionality by using features such as autocomplete to provide real-time suggestions as shoppers type, synonyms and spellings to ensure that shoppers find products even if they use different words, facets to allow shoppers to narrow down search results, and search redirects to automatically redirect shoppers from a search query to a specific page.

### Autocomplete

Autocomplete, also known as type-ahead or autosuggest, is an interactive search feature that dynamically displays suggestions to shoppers as they enter their search terms. This helps shoppers quickly and easily find products by offering real-time suggestions based on their input.

The [!DNL Live Search] [[!DNL popover]](storefront-popover.md) widget enables autocomplete search options to suggest popular products. With each character typed by the shopper, the popover updates with suggested products and thumbnail images of the top search results.

[!DNL Live Search] starts returning results when the user has typed in two characters. For a partial match, the maximum number of characters per word is 20. The number of characters in a "search as you type" query is not configurable.

Learn more about the [popover](storefront-popover.md) widget.

### Synonyms and misspellings

Live Search manages misspellings by default. You can set up synonyms to include words that shoppers might use that differ from words specified in your catalog. You do not want to lose a sale because someone is looking for a "sofa", while your product is listed as a "couch". You can capture a broad range of search terms by entering all the possible words that customers might use to find your products. You can [set synonyms as one way or two way](synonyms-add.md#step-2-define-the-synonym-by-type) to improve results.

#### Tips to optimize synonyms

- Map brand names and abbreviations to their full names, for example "HP" to "Hewlett-Packard" and common product nicknames, for example "iPhone" to "Apple iPhone".
- Include industry-specific jargon and terms that shoppers might use interchangeably, for example "sneakers" and "running shoes".
- Regularly update the synonym list based on new search trends, product additions, and shopper behavior.
- Test the effectiveness of synonym mappings by analyzing search results and shopper feedback. Refine mappings to improve accuracy and relevance.

Learn more about synonyms:

- [Types of synonyms](synonyms-type.md)
- [Create synonyms](synonyms-add.md)
- [Manage synonyms](synonyms-manage.md)
- [Language support](settings.md#language)

### Facets

Filter and facet functionality is a critical component of your [!DNL Commerce] site, designed to enhance the shopper experience by allowing shoppers to narrow down search results and find products more efficiently. This functionality helps shoppers sort through vast catalogs of items by applying specific criteria, making the shopping process faster, easier, and more satisfying. By implementing effective, shopper-friendly filters and facets, you can help customers find exactly what they need quickly and efficiently, ultimately boosting satisfaction and conversion rates.

To set up a product attribute as a facet, it must have the following [properties set](facets-add.md#step-1-add-a-facet):

- **[!UICONTROL Use in Search]** -  `Yes`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### Tips to optimize facets

- Determine the most relevant and useful attributes for your products, such as title, category, brand, price range, color, and size and set them as [dynamic facets](facets-type.md). 
- Set and sort product attributes that are consistent across your catalog and highly relevant for your products to improve relevancy and filtering capabilities for your shoppers.
- Ensure that facet labels are easy to understand and consistently named across the site. For example, use "Price Range" instead of "Cost".
- Avoid overwhelming shoppers by limiting the number of facets to the most important ones. Too many options can cause decision fatigue. By default, [!DNL Live Search] is limited to a maximum of 100 attributes configured as facets and 30 buckets returned within each facet. Learn more about [facet limitations](boundaries-limits.md#facets). 
- Allow shoppers to select multiple filter criteria simultaneously to refine results. For example, letting shoppers select both "Red" and "Blue" colors.
- Display the number of available products next to each facet option to give shoppers an idea of the search results they can expect.
- Implement collapsible facet sections to keep the interface clean and manageable, especially on mobile devices.
- Allow shoppers to easily reset individual facets or all selected filters to start a new search.

Learn more about facets:

- [Types of facets](facets-type.md)
- [Add facets](facets-add.md)
- [Manage facets](facets-manage.md) (edit, pin a facet, delete, publish)
- [Price faceting](settings.md#price-faceting)

### Search redirects

A search redirect allows you to automatically redirect shoppers from a search query to a specific page. Search redirects can improve shopper experience and guide customers to the most relevant content, such as a product page, category, landing page, or a tailored set of search results. Search redirects help streamline the shopping experience and ensure that shoppers find what they are looking for quickly and efficiently.

Recommended use cases for setting up search redirects:

- **Popular Products or Categories** - Redirect shoppers to a specific product page or category when they search for common or popular terms. For example, searching for "iPhone" might redirect directly to the iPhone category page or a specific model page.
    
- **Promotional Campaigns** - During promotional events or sales, redirect relevant search terms to landing pages that highlight special offers or featured products.
    
- **Brand Searches** - When shoppers search for a brand name, redirect them to the brand's dedicated page where all products from that brand are listed.
    
- **Product Discontinuation** - If a product is discontinued, you can redirect searches for that product to similar products or the new version of the product.

Always test search redirects to ensure they are working correctly and are leading to the most relevant pages. Continuously monitor their performance and make adjustments as needed.

Learn how to [manage search redirects](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms).

## Improve search result relevance

This section discusses how to improve search result relevance by implementing effective search rules and using product metadata to ensure accurate and detailed attributes are searchable.

### Search rules

To optimize your conversion rate and revenue, you must implement effective search rules. Adjust product rankings based on sales data, stock levels, and promotions with [Search Merchandising](rules.md).

It is crucial to establish a well thought out default search rule. Your [default rule](rules.md#default-rule) determines how search results are initially sorted and displayed to shoppers, enhancing their overall experience and increasing the likelihood of purchase. Regular monitoring and adjustment of this rule ensures that it continues to meet shopper needs and business objectives effectively.

#### Tips to optimize search rules

- Pin or boost products with high sales volumes or recent sales activity.
- Prioritize products with high ratings and positive reviews.
- Ensure that in-stock items are ranked higher.
- Slightly prioritize products with higher profit margins without compromising relevance.
- Highlight products that are on sale or part of special promotions.
- Set search rules during promotion or sales periods automatically by using the date range during your promotion period.
- Tailor search results based on individual shopper behavior using [intelligent ranking](rules-add.md#intelligent-ranking), such as "recommended for you", "most viewed" and so on. To tailor shopper behavior, you must ensure that eventing is correctly implemented. For Luma merchants, eventing is available out-of-the-box. For headless or custom implementations, you must [implement eventing](events.md) based on your specific needs.

Learn more about search rules:

- [Merchandising workspace](rules-workspace.md#set-the-scope)
- [Requirements](rules.md#requirements)
- [Default search rule](rules.md#default-rule)
- Manage search rules
    - [Create](rules-add.md)
    - [Edit, view, delete](rules-manage.md)
- Data collection
    - [[!DNL Live Search] events](events.md)
    - [Adobe Commerce Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
    - [GitHub Commerce events](https://github.com/adobe/commerce-events/tree/main/examples) 

### Leverage Product Metadata

Ensure that accurate and detailed product attributes are [set up as searchable](workspace.md#set-attributes-as-searchable). Note that SKU, name, and category attributes are searchable by default and cannot be excluded from search. 

To increase search relevance, assign a weight to each searchable attribute. Attributes with a higher weight should appear higher within the search results. Sorting by relevance is affected by multiple criteria, such as search weight. This means that sometimes attributes with lower search weight can still have more relevance than attributes with higher search weight. Other criteria can include the number of matches in any given attribute, position of found search term, and overall text structure before and after a search term.

Ensure that each product has relevant content within each searchable attribute. It is not recommended to set an attribute as searchable if it has large amounts of content as that can reduce search result relevance.

Learn more about product attributes for search:

- [Set attributes as searchable](workspace.md#set-attributes-as-searchable)
- [Assign weight to attributes](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## Monitoring Search Results

To optimize search results with [!DNL Live Search], monitor relevant Key Performance Indicators (KPIs) such as unique queries, average click position, click-through rates, conversion rate, and zero results rate to understand how shoppers interact with your search functionality. This data guides you to regularly update and refine your search rules.

You can monitor these KPIs within the [!DNL Live Search] [Performance workspace](performance.md) where you find the following metrics: 

- **Unique Searches** - The count of distinct search queries performed on your [!DNL Commerce] site. Each unique search is counted only once, even if it is repeated multiple times by the same shopper or different shoppers. This metric helps you understand the diversity of search terms used by customers and provides insights into what products or information shoppers are seeking. Tracking unique searches allows you to:

    - Identify popular search trends and frequently searched items.
    - Detect potential gaps in your product catalog or content.
    - Optimize your search functionality by adding [synonyms](synonyms.md), creating, or updating search rules.

- **Average Click Position** - Indicates that the average position of search results clicked by shoppers after performing a search query on your site. This metric provides insights into the relevance and effectiveness of your search results.

    A lower average click position (closer to 1) suggests that shoppers find relevant results quickly, indicating that your search strategy is effective. It helps you understand shopper behavior and how far they are willing to scroll to find the desired product. If the average click position is high, it may indicate that the most relevant results are not appearing at the top, which necessitates a review and optimization of your search strategy.

- **Click-Through Rate (CTR)** - Measures the percentage of shoppers who click on a search result after performing a search query. A high CTR indicates that the search results are relevant and appealing to shoppers, as they are clicking on the results they find. Monitoring CTR can help identify areas for improvement. Low CTR may suggest that search results are not matching shopper intent, prompting a need to refine search rules, enhance product data, or improve result presentation.

- **Conversion Rate** - Indicates the effectiveness of your search feature in driving sales and achieving business goals. It reflects the overall effectiveness of your search functionality in meeting shopper needs and facilitating a smooth shopping experience. A high conversion rate indicates that your search results are highly relevant and persuasive, leading shoppers to complete purchases. If the conversion rate is low, it may suggest issues with search relevance, product availability, or the overall shopper journey from search to purchase.

- **Zero Results** - Measures the percentage of search queries on your [!DNL Commerce] site that return no results. This metric is crucial for understanding how often shoppers' searches are unsuccessful and can provide insights into potential gaps in your product catalog or search setup. A high zero results rate can frustrate shoppers, leading to a poor shopping experience and potential loss of customers. It can indicate missing products or categories in your catalog that shoppers are searching for, guiding inventory and product listing decisions.

    To reduce the zero results rate, you can:

    - Offer alternative or related search terms, such as [synonyms](synonyms.md) when no exact matches are found.
    - Provide shoppers with related or alternative suggestions when their search yields no results by setting search redirects.
    - Regularly review zero result queries to identify patterns and make necessary adjustments to your product catalog and search settings.

- **Popular Results** - Can significantly enhance your search results by aligning them with shopper preferences and behaviors.

You can use this metric data to optimize your search functionality in the following ways:

- Implement rules to automatically rank popular products higher in search results. Products frequently clicked on or purchased can be given priority to appear at the top. Manually curate lists of popular products for specific search queries and ensure that these items are prominently displayed.
- Highlight products that are currently trending or have recently seen a spike in popularity. This can be particularly effective during seasonal events, holidays, or promotional periods. To achieve this use the intelligent ranking that better suits your use case and business need when setting up a search rule.
- Highlight popular filters or facets, if shoppers frequently filter by certain brands or price ranges, make those options more prominent by pinning those facets and sort them accordingly.
- When a search yields zero results, use popular results data to suggest alternative products or related categories that have high shopper engagement.
- Analyze popular search terms and product data to identify important keywords. Optimize your product searchable attributes with these keywords to improve search relevance.
- Regularly analyze your results data to understand changing trends, shopper preferences and behavior, identify top search terms, and detect issues. Use this feedback loop to continuously refine and improve your search rules and product offerings

To get correct data within your [!DNL Live Search] report, you must ensure that eventing is correctly implemented. For Luma merchants, eventing is available out-of-the-box. For headless or custom implementations, you must [implement eventing](events.md) based on your specific needs.
