---
title: '[!DNL Catalog Service]'
description: '[!DNL Catalog Service] for Adobe Commerce provides a way to retrieve the contents of Product Display Pages and Product List Pages much more quickly than the native Adobe Commerce GraphQL queries.'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
---
# [!DNL Catalog Service] for Adobe Commerce

{{catalog-service-beta}}

The [!DNL Catalog Service] for Adobe Commerce extension provides rich view-model (read-only) catalog data to quickly and fully render product-related storefront experiences, including:

*  Product detail pages
*  Product list and category pages
*  Search result pages
*  Product carousels
*  Product comparison pages
*  Any other pages that render product data, such as cart, order, and wish list pages

The [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) to request and receive product data. GraphQL is a query language that a frontend client uses to communicate with the application programming interface (API) defined on a backend such as Adobe Commerce. GraphQL is a popular method of communication because it is lightweight and allows a system integrator to specify the contents and order of each response.

Adobe Commerce has two GraphQL systems. The core GraphQL system provides a wide range of queries (read operations) and mutations (write operations) that allow a shopper to interact with many types of pages, including product, customer account, cart, checkout, and more. However, the queries that return product information are not optimized for speed. The services GraphQL system can only perform queries on products and related information. These queries are more performant than similar core queries.

## Architecture

The following diagram shows the two GraphQL systems:

![Catalog architecture diagram](assets/catalog-service-architecture.png)

In the core GraphQL system, the PWA sends a request to the Commerce application, which receives each request, processes it, possibly sending a request through multiple subsystems, then returns a response to the storefront. This round trip can cause slow page load times, potentially leading to lower conversion rates.

[!DNL Catalog Service] sends queries to a separate GraphQL gateway. The service accesses a separate database that contains product details and related information, such as product attributes, variants, prices, and categories. The service keeps the database in sync with the Adobe Commerce through indexation.
Because the service bypasses direct communication with the application, it is able to reduce the latency of the request and response cycle.

>[!NOTE]
>
>The gateway is for future integration with Product Recommendations. In this release, you can access [!DNL Catalog Service] and [!DNL Live Search] federated queries from the same endpoint if you have a valid license key for both products.

The core and service GraphQL systems do not directly communicate with each other. You access each system from a different URL, and calls require different header information. The two GraphQL systems are designed to be used together. The [!DNL Catalog Service] GraphQL system augments the core system to make product storefront experiences faster.

You can optionally implement [API Mesh for Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) to integrate the two Adobe Commerce GraphQL systems with private and third-party APIs and other software interfaces using Adobe Developer. The mesh can be configured to ensure calls routed to each endpoint contain the correct authorization information in the headers.

## Implementation

The installation process requires configuration of the [Commerce Services Connector](../landing/saas.md). Once that is accomplished, the next step is for a systems integrator to update the storefront code to incorporate the [!DNL Catalog Service] queries. All [!DNL Catalog Service] queries are routed to the GraphQL gateway. The URL is provided during the onboarding process.
