---
title: Best Practices
description: Learn the best practices for implementing [!DNL Live Search] for your store.
---
# Best Practices

This comprehensive guide is designed to help merchandisers enhance their site search functionality, ensuring a seamless and efficient user experience that maximizes conversion rates. By following the strategies outlined, you will learn how implement advanced search features, and continuously refine your search tool for optimal performance with Adobe Commerce Live Search.

There are several key factors that determine the relevance and effectiveness of search results:

- **Product Data Quality** is vital, a detailed, accurate, and well-structured information ensures that search algorithms can effectively match products to queries. Low quality data will lead to low relevant search results, setting up the correct **attributes as searchable** with their corresponding **weight** and making sure **data** within those attributes is relevant will directly impact the success of your merchandising strategy. 
- User experience and overall design.
- Search rules are critical as they can elevate the visibility of certain products based on popularity, new arrivals, promotional criteria or any other merchandising strategy to met your business requirements.
- Faceted Navigation to allow users to refine their search and get relevant results as quickly as possible

To manage [!DNL Live Search] go to Marketing \> SEO & Search - [!DNL Live Search] within your Adobe Commerce admin panel. 

## Optimize your Search Functionality

In this section, you learn how to optimize your search functionality by using features such as autocomplete to provide real-time suggestions as users type, synonyms and spellings to ensure users find products even if they use different words, and facets to allow shoppers to narrow down search results.

### Autocomplete

An autocomplete functionality, also known as typeahead or autosuggest, is an interactive search feature that dynamically displays suggestions to users as they enter their search terms. This helps users find products more quickly and easily by offering real-time suggestions based on their input.

The [!DNL Live Search] [Popover Widget](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/storefront-popover)  will enable autocomplete search options to suggest popular products. With each character typed by the user, the popover is updated with suggested products and thumbnail images of the top search results.

[!DNL Live Search] returns results for a query of two characters or more. For a partial match, the maximum number of characters per word is 20. The number of characters in a "search as you type" query is not configurable.

Learn more about the Popover widget [here](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/storefront-popover).

### Synonyms and Spellings

Incorporate synonyms and common misspellings to ensure comprehensive search results and expand the search query to include words that shoppers might use that differ from those in your catalog. You don't want to lose a sale because someone is looking for a "sofa", while your product is listed as a "couch". You can capture a broad range of search terms by entering all the possible words that customers might use to find your products. Synonyms can be set as one way or two way to facilitate set up and improve results. 

Best practices:

- Map brand names and abbreviations to their full names (e.g., "HP" to "Hewlett-Packard") and common product nicknames (e.g., "iPhone" to "Apple iPhone").
- Include industry-specific jargon and terms that users might use interchangeably (e.g., "sneakers" and "running shoes").
- Regularly update the synonym list based on new search trends, product additions, and user behavior.
- Test the effectiveness of synonym mappings by analyzing search results and user feedback. Refine mappings to improve accuracy and relevance.

Learn more about how to set up synonyms:

- [Type of synonyms](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/synonyms/synonyms-type)
- [Create synonyms](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/synonyms/synonyms-add)
- [Manage synonyms](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/synonyms/synonyms-manage)
- [Language support](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/settings#language)

### Facets

Filter and facet functionality is a critical component of an e-commerce website, designed to enhance the user experience by allowing shoppers to narrow down search results and find products more efficiently. This functionality helps users sort through vast catalogs of items by applying specific criteria, making the shopping process faster, easier, and more satisfying. By implementing effective, user-friendly filters and facets, you can help customers find exactly what they need quickly and efficiently, ultimately boosting satisfaction and conversion rates.

For a product attribute to be set up as a facet it must have properties set up as follows:

- Use in Search -  `Yes`
- Use in Search Results Layered Navigation -  `Yes`
- Use in Layered Navigation -  `Filterable (with results)`

To do this you have to go to "**Stores**  \> Attributes >  **Product**   " ([+info](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/facets-add#step-2-edit-facet-properties-optional))

Best practices:

- Determine the most relevant and useful attributes for your products, such as title, category, brand, price range, color, and size and set them as [dynamic facets](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/facets-type) . 
- Product attributes that are consistent across your catalog and highly relevant for your products can be set as pinned facets and sorted to improve relevancy and filtering capabilities for your users.
- Ensure facet labels are easy to understand and consistently named across the site (e.g., use "Price Range" instead of "Cost").
- Avoid overwhelming users by limiting the number of facets to the most important ones. Too many options can cause decision fatigue. [!DNL Live Search] is by default limited to a maximum of 100 attributes configured as facets and 30 buckets returned within each facet ([+info on facets' limitations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/boundaries-limits#facets)). 
- Allow users to select multiple filter criteria simultaneously to refine results (e.g., selecting both "Red" and "Blue" for color). Display the number of available products next to each facet option to give users an idea of the search results they can expect.
- Implement collapsible facet sections to keep the interface clean and manageable, especially on mobile devices.
- Allow users to easily reset individual facets or all selected filters to start a new search.

Learn more about facets:

- [Type of facets](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/facets-type)
- [Add facets](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/facets-add)
- [Manage facets](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/facets-manage) (edit, pin a facet, delete, publish)
- [Price faceting](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/settings#price-faceting)

### Search redirects

A search redirect allows you to automatically redirect users from a search query to a specific page. This can be particularly useful for improving user experience and guiding customers to the most relevant content, this can be a product page, category, landing page, or a tailored set of search results. This is often used to streamline the shopping experience and ensure that users find what they are looking for quickly and efficiently.

Some recommended use cases for setting up search redirects are:

1. **Popular Products or Categories:** Redirect users to a specific product page or category when they search for common or popular terms. For example, searching for "iPhone" might redirect directly to the iPhone category page or a specific model page.
    
1. **Promotional Campaigns:** During promotional events or sales, redirect relevant search terms to landing pages that highlight special offers or featured products.
    
1. **Brand Searches:** When users search for a brand name, redirect them to the brand's dedicated page where all products from that brand are listed.
    
1. **Product Discontinuation:** If a product is discontinued, searches for that product can be redirected to similar products or the new version of it .

Search redirects helps users find relevant content quickly, reducing frustration and improving satisfaction, reducing the likelihood of them leaving the site without finding what they need.  By directing users to the most relevant pages, search redirects can help increase the likelihood of purchases. 

It is always recommended to test the search redirects to ensure they are working correctly and are leading to the most relevant pages. Continuously monitor their performance and make adjustments as needed.

Learn how to manage search redirects [here](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms).

## Improving Search Results Relevance

Intro text...

### Search rules

To optimize your conversion rate and revenue, implementing effective search rules is essential. Adjust product rankings based on sales data, stock levels, and promotions with [Search Merchandising](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules).

It's crucial to establish a well-thought-out default search rule. Your [default rule](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules#default-rule) will determine how search results are initially sorted and displayed to users, enhancing their overall experience and increasing the likelihood of purchase. Regular monitoring and adjustment of this rule will ensure that it continues to meet user needs and business objectives effectively.

Here are best practices you can apply to search rules:

- Pin or boost products with high sales volumes or recent sales activity.
- Prioritize products with high ratings and positive reviews.
- Ensure in-stock items are ranked higher.
- Slightly prioritize products with higher profit margins without compromising relevance.
- Highlight products that are on sale or part of special promotions.
- Set search rules during promotion or sales periods automatically by using the date range during your promotion period.
- Tailor search results based on individual user behavior, using intelligent ranking such as recommended for you, most viewed ([+info](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add#intelligent-ranking)). In order to tailor user behavior you must ensure eventing is correctly implemented. While LUMA users get eventing out of the box, headless and other custom implementations have to implement eventing for their own needs ([+info](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/events)).

Learn more about search rules:

- [Merchandising admin panel](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-workspace#set-the-scope)
- [Requirements](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules#requirements)
- [Default search rule](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules#default-rule)
- Manage search rules ([create](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add), [edit, view, delete](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-manage)) 
- Data collection
    - [[!DNL Live Search] events](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/events)
    - [Adobe Commerce Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
    - [Github Commerce events](https://github.com/adobe/commerce-events/tree/main/examples) 

### Leverage Product Metadata

Ensure accurate and detailed product attributes are [set up as searchable](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/workspace#set-attributes-as-searchable). Note that SKU, name, and category attributes are searchable by default and cannot be excluded from search. 

To increase search relevance assign a weight to each searchable attribute. Attributes with a higher weight should appear higher within the search results. It is important to highlight that sorting by relevance is affected by multiple criteria and relationships between them at the same time. Search Weight is one of those criteria, this means that sometimes attributes with lower search weight may still have more relevance than attributes with higher search weight. Other criteria may include number of matches in any given attribute, position of found search term, and overall text structure before and after a search term.

Ensure each product has relevant content within each searchable attribute. It is not recommended to set as searchable attribute those with large content on it as it can reduce the relevancy of results. 

Learn more about product attributes for search:

- [Set attributes as searchable](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/workspace#set-attributes-as-searchable)
- [Assign weight to attributes](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## Monitoring Search Results

To optimise search results with Adobe Commerce [!DNL Live Search] as with any other search solution, it is key to monitor relevant KPIs such as search queries, average click position, click-through rates, conversion rate, and zero results rate to understand how users interact with your search functionality. This data will guide you to regularly update and refine your search rules.

You can monitor these KPIs within the [!DNL Live Search] Performance tab where you'll find the following metrics: 

**Unique Searches** refers to the count of distinct search queries performed on your e-commerce site. Each unique search is counted only once, even if it is repeated multiple times by the same user or different users. This metric helps in understanding the diversity of search terms used by customers and provides insights into what products or information users are seeking. Tracking unique searches allows you to:

- Identify popular search trends and frequently searched items.
- Detect potential gaps in your product catalog or content.
- Optimize your search functionality to better meet user needs by adding [synonyms](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/synonyms/synonyms), create and/or update search rules.

The **Average Click Position** is a metric that indicates the average position of search results clicked by users after performing a search query on your site. This metric provides insights into the relevance and effectiveness of your search results.

A lower average click position (closer to 1) suggests that users find relevant results quickly, indicating that your search strategy is effective. It helps in understanding user behavior and how far they are willing to scroll to find the desired product. If the average click position is high, it may indicate that the most relevant results are not appearing at the top, necessitating a review and optimization of your search strategy.

**Click-Through Rate (CTR)** is a key metric that measures the percentage of users who click on a search result after performing a search query. A high CTR indicates that the search results are relevant and appealing to users, as they are clicking on the results they find. Monitoring CTR can help identify areas for improvement. Low CTR may suggest that search results are not matching user intent, prompting a need to refine search rules, enhance product data, or improve result presentation.

**Conversion Rate** is a crucial indicator of the effectiveness of your search feature in driving sales and achieving business goals.  It reflects the overall effectiveness of your search functionality in meeting user needs and facilitating a smooth shopping experience. A high conversion rate indicates that your search results are highly relevant and persuasive, leading users to complete purchases. If the conversion rate is low, it may suggest issues with search relevance, product availability, or the overall user journey from search to purchase.

**Zero Results** is a metric that measures the percentage of search queries on your e-commerce site that return no results. This metric is crucial for understanding how often users' searches are unsuccessful and can provide insights into potential gaps in your product catalog or search setup. A high zero results rate can frustrate users, leading to a poor shopping experience and potential loss of customers. It can indicate missing products or categories in your catalog that users are searching for, guiding inventory and product listing decisions. Some improvements that can be done to reduce the zero results rate:

- Offer alternative or related search terms when no exact matches are found, you can do this by setting up synonyms. 
- Provide users with related or alternative suggestions when their search yields no results by setting search redirects.
- Regularly review zero result queries to identify patterns and make necessary adjustments to your product catalog and search settings.

Using **Popular Results** data can significantly enhance your search results by aligning them with user preferences and behaviors.

Recommendations on how to leverage this data to optimize your search functionality:

- Implement rules to automatically rank popular products higher in search results. Products frequently clicked on or purchased can be given priority to appear at the top. Manually curate lists of popular products for specific search queries and ensure these items are prominently displayed.
- Highlight products that are currently trending or have recently seen a spike in popularity. This can be particularly effective during seasonal events, holidays, or promotional periods. To achieve this use the intelligent ranking that better suit your use case and business need when setting up a search rule.
- Highlight popular filters or facets, if users frequently filter by certain brands or price ranges, make those options more prominent by pinning those facets and sort them accordingly.
- When a search yields zero results, use popular results data to suggest alternative products or related categories that have high user engagement.
- Analyze popular search terms and product data to identify important keywords. Optimize your product searchable attributes with these keywords to improve search relevancy.
- Regularly analyze your results data to understand changing trends, user preferences and behaviour, identify top search terms, and detect issues. Use this feedback loop to continuously refine and improve your search rules and product offerings

To get correct data within your [!DNL Live Search] report you must ensure eventing is correctly implemented. While LUMA users get eventing out of the box, headless and other custom implementations have to implement eventing for their own needs ([+info](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/events)).
