---
title: '[!DNL Composable Catalog Data Model]'
description: 'Learn how the [!DNL Composable catalog data model] for Adobe Commerce helps you setup your catalog to match your business model and go-to-market strategy'
recommendations: noCatalog
---

# CCDM – ExL docs

- Introduction
- Composable Catalog data model
- Product Data management
- Product Context management
- Key features and benefits
- Architecture
- Data modeling Use Cases
- CCDM: Channels, Policies and scopes
- Sample use case <technical>
- Overall commerce architecture – to be added
- SaaS + Monolith 
- Migration strategy
- FAQ - to be added
- Limitations- to be added
- <note: capability is early access. Please reach out to xx for capability access>

## Introduction:

A product catalog is the backbone of online shopping experiences. They are essential for enabling customers to browse, search, and make purchases. To achieve operational efficiency, an ecommerce product catalog benefits from reflecting the company's business structure as closely as possible. Businesses need to sell different products and different prices depending on geographic market, distribution channel, customer segment and other variables. To achieve this flexibility an ecommerce platform must provide a flexible catalog data model that allows companies to produce variations of their product catalog that adapts to these scenarios. These friction points are solved by Adobe Commerce's Composable Catalog Data Model (CCDM), a new method to create product catalogs for headless commerce implementations. This new approach allows businesses to set up catalogs that align with their business structure and go-to-market strategies.

## What is Composable Catalog Data Model?

There are two distinct aspects to product catalog management – product data and product context. CCDM honors the separation of the duties for both and provides management of these independently of each other.

### Product data:

- **Products**: Products are individual SKUs or collections of SKUs that represent physical goods, intangible services. Products can be grouped into various product types such as simple, configurable, bundle, bundle of bundles, subscriptions, and more.
- **Attributes**: Attributes are meta data associated with products including description, weight, dimensions, and more.
- **Prices**: Prices are amounts for which a product is sold. Prices for the same product can differ based on other variables such as channel, currency, quantity, and more. Prices can be listed in price books for specific channels, customers or geographies.
- **Assets**: Assets are artifacts associated with products such as images, videos, PDFs or other file types.
- **Stock**: Stock represents the available inventory of product that can be sold to customers. This can be a combination of sources from multiple warehouses.

### Product context management:

- **Channel**: This is a distribution channel of products a business wants to sell through. A channel is the highest-level abstraction which encapsulates Locales and Policies.
  - Example: Dealers for Automobile industry. Subsidiaries for multi-brand conglomerates. Manufacturing location for suppliers.
- **Policy**: This is a data access filter which empowers you to deliver the right content to the right destination. This concept enables you with catalog syndication capabilities.
  - Example: POS physical stores Marketplaces Advertisement pipelines (Google, FB, IG)
- **Scope**: This represents the language(locale), currency and unit of measurement for catalogs. This is set at a SKU level during catalog data ingestion. The mandatory scope to be added is 'locale', however the scope is extensible and concepts such as 'markets' and 'brands' can also be added.

## Key features of Composable Catalog Data Model include:

### Key features

- **Direct catalog data ingestion into storefront services pipeline**: Ingest your catalog data directly into the catalog service pipeline for storefront browse and search lifecycle (Product Display Page, Product List Page, Search Results Page, Categories, Breadcrumb etc.) and avoid the data ingestion into Adobe Commerce core.
  - Avoid multiple time-consuming indexations of Adobe Commerce core and directly ingest data into storefront service pipeline which powers: Catalog Service, Catalog Browse (Live Search) and Product Recommendations.
  - Decouple your backend commerce implementation with modern storefront experiences with ease.
- **New catalog product scopes**: 
  - Channels, policies and locale are new product scopes introduced by CCDM.
  - These product scopes replace website-store-storeview scopes in the storefront services layer. 
  - Learn more <link>
  - This is the biggest new introduction with CCDM. This unlocks the ability to scale to multi-geography, multi-business unit, multi-brand and multi-language use cases with ease using a single base catalog.
  - Eliminate data redundancy in your catalog management.
- **Scale to tens of Millions of SKUs**: 
  - Support tens of millions of SKUs in your product catalog browse/discovery lifecycle with ease by leveraging the direct catalog data ingestion to storefront services pipeline. You are no longer bound to the limitations of Adobe Commerce core admin.
  - De-couple your experiences to support scale: (1) Direct storefront services pipeline data ingestion for large scale SKUs (2) Ingest only your transactional SKUs to Adobe Commerce core admin.
- **Product type support**:
  - Simple, configurable
  - Bundles and bundles of bundles (future roadmap)
  - Subscriptions and plans (future roadmap)
- **Headless commerce**:
  - Full support for headless commerce implementations through Catalog Service, Catalog Browse (Live Search) and Product Recommendations APIs.
- **Modern lightning-fast UI components**:
  - OOTB UI component support for product search and product recommendations.
  - The UI components are extensible and flexible such that they can be used by both Adobe's Edge Delivery Service as well as any other storefront implementation.

## Overall benefits of Composable Catalog Data Model include:

- Use a single base catalog for all your business needs. Scale your catalog quickly into new brands, markets, business-units, go-to-market channels, and customer segments without re-architecting your entire catalog. This eliminates data duplication and sets up your e-commerce platform for high operational efficiency.
- Deliver lightning-fast shopping experiences without the overhead of re-platforming your entire commerce system. Use CCDM for your storefront while using your existing commerce platform for your backend requirements.
- Unlock catalog syndication and deliver the right content to the right destination by designing your product catalog to reflect how you do business including which products you sell, who you sell them to, what price they pay, and how you distribute these products. 
- Using CCDM you can quickly ingest and update catalog data and deliver rapid catalog updates to the storefront for your promotions and campaign needs.
- OOTB support for lightning-fast Edge Delivery Service compatible UI components for product browse and product recommendations.
- Adopt a modern composable architecture using Adobe's extensibility architecture (App Builder) to import product data and power headless commerce storefronts using Adobe's API Mesh.

## Architecture

CCDM is a highly scalable and flexible catalog data model which unlocks multi-brand, multi-business unit, multi-language use cases with ease. The model replaces the use of the classic Adobe Commerce product scopes (website-store-store view model) with new CCDM product scopes (Channel, Policy and Locale).

## Examples use cases:

### Merchant type

- **Use Case**
- **Pain points solved**
- **Multi-brand conglomerate**
  - They sell several brands 
  - They sell in several countries
  - They sell in different languages 
  - Classic adobe commerce scopes(website-store-storeview) would lead to data explosion. One would need a website for each brand, country and language.
- **Automobile/Manufacturing parts conglomerate**
  - Auto/machine parts are sold. The products are the same for all customers. 
  - Different dealers sell parts to customers
  - Each dealer has own prices, stock and shipping methods
  - To have different shipping integrations each dealer should have a separate website. But separate websites force the classic data model to duplicate catalogs. 
  - So, if there are 3000 dealers in USA, a merchant will create 3000 copies of catalogs despite the same catalog being used across. 
  - Data duplication interferes with performance limits.
- **Feed packaging company**
  - They have several shipping locations 
  - They have different price for each customer 
  - The same product available in 2 locations for 2 customers will have 4 possible prices
  - Despite the use of customer groups to cover pricing per customer, classic model does not have the scope to manage price per location.
  - The only option is to copy each product for each location what means it is not the same root product anymore. 
  - Data duplication interferes with performance limits.

## Channels, Policies and Scopes:

During product data ingestion/update, a SKU will contain the details of scopes and attributes (the attributes map to channels and policies). These define the product context identifiers to which a SKU belongs:
The definitions of Channels and Policies are created via dedicated APIs:
With the above context, the full data model of CCDM can now be understood below:
The above architecture diagram sheds light on how E-commerce Catalog Administrators and Merchandisers can leverage Composable Catalog Data Model to craft and manage an entire product portfolio which scales for multi-brand, multi-language, multi-business unit use cases with ease without introducing data duplication. 
CCDM enables you to map your Catalog Model to your Business structure and delivers high scalability and operational efficiency.
