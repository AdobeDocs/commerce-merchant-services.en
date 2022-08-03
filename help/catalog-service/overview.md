---
title: "[!DNL Catalog Service]"
description: "[!DNL Catalog Service] for Adobe Commerce provides a way to retrieve the contents of Product Display Pages and Product List Pages faster than the native Adobe Commerce GraphQL queries."
---

# [!DNL Catalog Service] for Adobe Commerce

>[!IMPORTANT]
>
> This product is for Beta users only. Contact your Adobe Commerce Beta program manager for assistance and questions.

The [!DNL Catalog Service] for Adobe Commerce extension provides rich view-model (read-only) catalog data to quickly and fully render product-related storefront experiences, including:

*  Product detail pages
*  Product list and category pages
*  Search result pages
*  Product carousels
*  Product comparison pages
*  Any other pages that render product data, such as cart, order, and wish list pages

The [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) to request and receive product data. GraphQL is a query language that a [Progressive Web App](https://developer.adobe.com/commerce/pwa-studio/) (PWA) or other frontend client uses to communicate with the application programming interface (API) defined on a backend such as Adobe Commerce. GraphQL is a popular method of communication because it is lightweight and allows a system integrator to specify the contents and order of each response.

Adobe Commerce has two GraphQL systems. The core GraphQL system provides a wide range of queries (read operations) and mutations (write operations) that allow a shopper to interact with many types of pages, including product, customer account, cart, checkout, and more. However, the queries that return product information are not optimized for speed. The services GraphQL system can only perform queries on products and related information. These queries are more performant than similar core queries.

The following diagram shows the two GraphQL systems:

![Catalog architecture diagram](assets/catalog-service-architecture.png)

In the core GraphQL system, the PWA sends a request to the Commerce application, which receives each request, processes it, possibly sending a request through multiple subsystems, then returns a response to the storefront. This round trip can cause slow page load times, potentially leading to lower conversion rates.

[!DNL Catalog Service] sends queries to a separate GraphQL gateway. The service accesses a separate database that contains product details and related information, such as product attributes, variants, prices, and categories. The service keeps the database in sync with the Adobe Commerce through indexation.
Because the service bypasses direct communication with the application, it is able to reduce the latency of the request and response cycle.

The core and service GraphQL systems do not directly communicate with each other. You access each system from a different URL, and calls require different header information. You can use [!DNL Catalog Service] and [!DNL Live Search] together, if you have a valid license key for both products. However, you can implement [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) to integrate the two Adobe Commerce GraphQL systems with private and third-party APIs and other software interfaces using Adobe IO.

