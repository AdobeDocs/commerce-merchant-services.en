---
title: '[!DNL Composable Catalog Data Model]'
description: 'Learn how the [!DNL Composable Catalog Data Model] for Adobe Commerce helps you setup your catalog to match your business model and go-to-market strategy'
hidefromtoc: yes
recommendations: noCatalog
---
# [!DNL Composable Catalog Data Model]

A product catalog is essential for online shopping experiences, enabling customers to browse, search, and make purchases. For operational efficiency, a product catalog should closely mirror the company's business structure. Businesses often need to sell products at varying prices based on geographic market, distribution channel, customer segment, and other variables. To accommodate this, an ecommerce platform must offer a flexible catalog data model that allows companies to produce variations of their catalog tailored to these scenarios. Adobe Commerce's Composable Catalog Data Model (CCDM) addresses these needs. CCDM provides building blocks that merchants can use to create and manage catalogs at scale. This enables businesses to configure catalogs that align with their business structure and go-to-market strategies.

At a high level, with CCDM you can:

- Use a single base catalog for all your business needs. Scale your catalog quickly across new brands, markets, business-units, go-to-market channels, and customer segments without the need for complete re-architecture. This eliminates data duplication and sets up your ecommerce platform for high operational efficiency.
- Unlock catalog syndication and deliver the right content by designing your product catalog to reflect your business, including products, customers, pricing, and distribution.
- Quickly ingest and update catalog data and rapidly deliver the updates to the storefront for your promotions and campaign needs.
- Accomplish perfect lighthouse scores with ready-to-use, lightning-fast UI components powered by Edge Delivery Services for seamless product browsing and recommendations.
- Adopt a modern composable architecture using Adobe's extensibility architecture ([App Builder](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-development)) to import product data and power headless commerce storefronts using Adobe's [API Mesh](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-and-api-mesh).

## Key features

|Key features|Benefit|
|---|---|
|**Direct catalog data ingestion into storefront services pipeline**: Ingest your catalog data directly into the catalog service pipeline for the storefront browse and search lifecycle (Product Display Page, Product List Page, Search Results Page, Categories, Breadcrumb, and so on.)|<ul><li>Directly ingest catalog data into the storefront service pipeline which powers: Catalog Service, Product Discovery (Live Search), and Product Recommendations. With this, you can deliver catalog updates at scale for millions of SKUs. This unlocks time sensitive large scale promotion management. </li></ul>|
|**New catalog product scopes**: Channel, policy, and scope are new product scopes introduced by CCDM. These product scopes replace the website, store, and storeview scopes in the storefront services layer. [Learn more](#channel-policy-and-scope).|<ul><li>With the new scopes, CCDM unlocks the ability to scale to multi-geography, multi-business unit, multi-brand and multi-language use cases with ease using a single base catalog.</li><li>Eliminate data redundancy in your catalog management.</li></ul>|
|**Scale to tens of millions of SKUs**|Unlock catalog management at scale. Here you can ingest and manage over 200MM SKUs with ease.|
|**Product type support**|<ul><li>Simple, configurable</li><li>Bundles and bundles of bundles (future roadmap)</li><li>Subscriptions and plans (future roadmap)</li></ul>|
|**Headless commerce**|<ul><li>Full support for headless commerce implementations through Catalog Service, Product Discovery (Live Search) and Product Recommendations APIs.</li></ul>|
|**Modern lightning-fast UI components**|<ul><li>Out of the box UI component support for product search and product recommendations.</li><li>The UI components are extensible and flexible so that they can be used by both Adobe's Edge Delivery Service as well as any other storefront implementation.</li></ul>|

## What type of merchant benefits the most from CCDM?

The following table highlights common challenges merchants encounter and how CCDM addresses them.

|Merchant type|Use case|Problems solved|
|---|---|---|
|Multi-brand conglomerate|<ul><li>They sell several brands</li><li>They sell in several countries</li><li>They sell in different languages</li></ul>|Use a single base unified catalog and achieve operational efficiency while expanding to several brands, geographies and languages.|
|Automobile/Manufacturing parts conglomerate|<ul><li>Sells auto or machine parts. The products are the same for all customers.</li><li>Different dealers sell parts to customers</li><li>Each dealer has its own prices, stock and shipping methods</li></ul>|To have different shipping integrations, each dealer should have a separate website. But separate websites force the typical catalog data model to duplicate the data. So, if there are 3000 dealers in USA, a merchant creates 3000 catalog copies even though the same catalog is used by all dealers. This data duplication interferes with performance limits. CCDM eliminates data duplication.|
|Packaging/logistics company|<ul><li>They have several shipping locations</li><li>They have a different price for each customer</li><li>The same product available in 2 locations for 2 customers have 4 possible prices</li></ul>|Despite the use of customer groups to cover pricing per customer, the typical catalog data model does not have the capability to manage price per location. Additionally, merchants want unique visibility rules per location/website. Management of such complex price and visibility rules can be unlocked at scale with CCDM. |

## Architecture

CCDM is a highly scalable, flexible catalog data model which unlocks multi-brand, multi-business unit, multi-language use cases with ease. The model replaces the use of the classic Adobe Commerce product scopes (website, store, storeview) with new CCDM product scopes (channel, policy, and locale).

The following diagram provides a high-level view of the CCDM framework.

![[!DNL Composable Catalog Data Model] Architecture](assets/ccdm-architecture.png)

At the top of this diagram, catalog data (PIM, ERP, and so on) is ingested into the CCDM framework. This catalog data contains SKUs. Each SKU contains scope details (locale) and product attributes, which map to the new CCDM product scopes (channels, policies, and locale).

When all this data is ingested into the CCDM framework, the result is a new unified base catalog that is available in the Catalog Service data pipeline. In the next part of the diagram, you see multiple channels. Each channel represents a business unit. For example, *Texas retail*, *Texas retail seasonal*, and so on. As you can see from the diagram, locales, policies, and price books can all be shared across channels.​

Finally, the diagram shows how this distinct catalog data can be surfaced in various locations, such as an Edge Delivery Services storefront, a marketplace, an advertisement channel, a custom micro-storefront, and so on.

To learn how you can ingest your catalog data into CCDM using the catalog data ingestion API and how to set up your locales, policies, and price books using the catalog management and rules API, see the [developer documentation](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

To learn more about the concepts that make up CCDM, see the following sections.

## Product catalog management

Product catalog management encompasses two distinct aspects: product data and product context. CCDM respects the separation of these duties, offering independent management for each.

- **Product data** - What product is being sold and at what price?
- **Product context** - Who is selling to whom and where?

![[!DNL Composable Catalog Data Model] aspects](assets/ccdm-parts.png)

### Product data

Product data includes the following types:

- **Products** - Individual SKUs or collections of SKUs that represent physical goods or intangible services with attributes that represent the product including description, weight, size, dimensions, and more. Attributes also specify the channel and policy scopes for a SKU. Products can be grouped into various product types such as simple, configurable, bundle, bundle of bundles, subscriptions, and more.
- **Metadata** - Product attribute metadata defines and manages how product attributes are displayed on the storefront in product listings, detail pages, search results, and so on. Metadata also defines how product attributes are used in search—sorting, filtering, search weights, and so on.
- **Price books and prices** - Determines the selling prices of products. In CCDM, a product SKU and price are decoupled, hence you are empowered to define multiple price books for a single SKU. By decoupling the prices from the SKU, you can unlock scope-specific prices across different customers tiers, business units, and geographies. You can define regular and discounted prices and manage all of this at scale.
- **Assets** - Artifacts associated with products, such as images, videos, PDFs or other file types (future roadmap).
- **Stock** - Represents the available inventory of product that can be sold to customers. Stock can be a combination of sources from multiple warehouses.

### Product context management

Product context management covers the following aspects:

- **Channel** - Distribution channel defines the path that a business wants to sell products through. A channel is the highest-level abstraction which encapsulates locales and policies.
  - Example: Dealers for the automobile industry. Subsidiaries for multi-brand conglomerates. Manufacturing location for suppliers.
- **Policy** - Data access filter which empowers you to deliver the right content to the right destination. This concept enables catalog syndication capabilities.
  - Example: Point of sale physical stores, marketplaces, advertisement pipelines (Google, Facebook, Instagram)
- **Scope** - Represents the language (locale), currency, and unit of measurement for catalogs. Scope is set at a SKU level during catalog data ingestion.

During product data ingestion and update, a SKU contains the details of scopes and attributes (the attributes map to channels and policies). These define the product context identifiers to which a SKU belongs:

![[!DNL Composable Catalog Data Model] Product Context Identifiers](assets/ccdm-product-id.png)

In the above image, each SKU provides:

- Scope identifiers​
    - Locale: Mandatory​
- Product attributes
    - Product attributes are used to map to the relevant channels and policies​
    - Example: As an automobile manufacturer, you can choose to create a channel and policy combination for product attributes: (1) Dealers (2) Car brands.​
- Prices and assigned price books
   - Each SKU can have multiple prices defined using multiple pricebooks.
   - Example: You offer employees a reduced regular price on auto parts with an additional discount of 25%. You offer VIP customers a higher regular price with a discount of 10%. The product SKU price information ensures that the right price is displayed for each customer segment.

The channel and policy definitions are created using dedicated APIs:

![[!DNL Composable Catalog Data Model] Channel, Policy, and Scope Mapping](assets/ccdm-scope-map.png)

- **Scope** (locale) - Set at a SKU level during product data ingestion.​
- **Channel** - Definition created using dedicated APIs. ​
- **Policy** - Definition created using dedicated APIs.

### Where to go from here

- Ingest data into CCDM using the [data ingestion API](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/).
- Manage your catalog and define the channels, policies, and scopes using the [catalog management and rules API](https://developer-stage.adobe.com/commerce/services/composable-catalog/admin/using-the-api/)
- [Complete a tutorial](https://developer-stage.adobe.com/commerce/services/composable-catalog/ccdm-use-case/) that shows how a company with a single base catalog can use the CCDM APIs to add product data, define catalogs using projections, and retrieve the catalog data for display in a headless storefront.
