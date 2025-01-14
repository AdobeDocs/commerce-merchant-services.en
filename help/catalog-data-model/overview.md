---
title: '[!DNL Composable Catalog Data Model]'
description: 'Learn how the [!DNL Composable catalog data model] for Adobe Commerce helps you setup your catalog to match your business model and go-to-market strategy'
hidefromtoc: yes
recommendations: noCatalog
---
# [!DNL Composable Catalog Data Model]

A product catalog is the backbone of online shopping experiences. They are essential for enabling customers to browse, search, and make purchases. To achieve operational efficiency, an ecommerce product catalog benefits from reflecting the company's business structure as closely as possible. Businesses need to sell different products at different prices depending on geographic market, distribution channel, customer segment, and other variables. To achieve this flexibility, an ecommerce platform must provide a flexible catalog data model that allows companies to produce variations of their product catalog that adapt to these scenarios. Adobe Commerce's Composable catalog data model (CCDM) helps to solve these friction points. CCDM is a collection of APIs that merchants can use to create and manage product catalogs for headless commerce implementations. This API-first approach allows businesses to set up catalogs that align with their business structure and go-to-market strategies.

>[!NOTE]
>
>To learn about the APIs that CCDM provides for creating and managing your commerce catalog, see the [developer documentation](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

## Product catalog management

Product catalog management encompasses two distinct aspects: product data and product context. CCDM respects the separation of these duties, offering independent management for each.

- **Product data** - What product is being sold and at what price?
- **Product context** - Who is selling to whom and where?

![[!DNL Composable Catalog Data Model] aspects](assets/ccdm-parts.png)

### Product data

Product data includes the following types:

- **Products** - Individual SKUs or collections of SKUs that represent physical goods or intangible services. Products can be grouped into various product types such as simple, configurable, bundle, bundle of bundles, subscriptions, and more.
- **Attributes** - Meta data associated with products including description, weight, dimensions, and more.
- **Prices** - Amounts for which a product is sold. Prices for the same product can differ based on other variables such as channel, currency, quantity, and more. Prices can be listed in price books for specific channels, customers, or geographies.
- **Assets** - Artifacts associated with products, such as images, videos, PDFs or other file types.
- **Stock** - Represents the available inventory of product that can be sold to customers. Stock can be a combination of sources from multiple warehouses.

### Product context management

Product context management covers the following aspects:

- **Channel** - Distribution channel defines the path that a business wants to sell products through. A channel is the highest-level abstraction which encapsulates locales and policies.
  - Example: Dealers for the automobile industry. Subsidiaries for multi-brand conglomerates. Manufacturing location for suppliers.
- **Policy** - Data access filter which empowers you to deliver the right content to the right destination. This concept enables catalog syndication capabilities.
  - Example: Point of sale physical stores, marketplaces, advertisement pipelines (Google, Facebook, Instagram)
- **Scope** - Represents the language (locale), currency, and unit of measurement for catalogs. Scope is set at a SKU level during catalog data ingestion. The mandatory scope to be added is 'locale', however the scope is extensible and concepts such as 'markets' and 'brands' can also be added.

## Key features

|Key features|Benefit|
|---|---|
|**Direct catalog data ingestion into storefront services pipeline**: Ingest your catalog data directly into the catalog service pipeline for the storefront browse and search lifecycle (Product Display Page, Product List Page, Search Results Page, Categories, Breadcrumb, and so on.) and avoid the data ingestion into Adobe Commerce core.|- Avoid multiple time-consuming indexations of Adobe Commerce core and directly ingest data into the storefront service pipeline which powers: Catalog Service, Catalog Browse (Live Search) and Product Recommendations.<br>- Effortlessly decouple your backend commerce implementation to create modern, seamless storefront experiences.|
|**New catalog product scopes**: Channel, policy, and scope are new product scopes introduced by CCDM. These product scopes replace the website, store, and storeview scopes in the storefront services layer. [Learn more](#channel-policy-and-scope).|- With the new scopes, CCDM unlocks the ability to scale to multi-geography, multi-business unit, multi-brand and multi-language use cases with ease using a single base catalog.<br>- Eliminate data redundancy in your catalog management.|
|**Scale to tens of millions of SKUs**|- Support tens of millions of SKUs in your product catalog browse and discovery lifecycle with ease by leveraging the direct catalog data ingestion to storefront services pipeline. With CCDM, you are no longer bound by the catalog limits in the Adobe Commerce core admin.<br>- Decouple your experiences to support scale: (1) Direct storefront services pipeline data ingestion for large scale SKUs; (2) Ingest only your transactional SKUs to Adobe Commerce core admin.|
|**Product type support**|- Simple, configurable<br>- Bundles and bundles of bundles (future roadmap)<br>- Subscriptions and plans (future roadmap)|
|**Headless commerce**|- Full support for headless commerce implementations through Catalog Service, Catalog Browse (Live Search) and Product Recommendations APIs.|
|**Modern lightning-fast UI components**|- Out of the box UI component support for product search and product recommendations.<br>- The UI components are extensible and flexible so that they can be used by both Adobe's Edge Delivery Service as well as any other storefront implementation.|

## Overall benefits of [!DNL Composable Catalog Data Model]

- Use a single base catalog for all your business needs. Scale your catalog quickly across new brands, markets, business-units, go-to-market channels, and customer segments without the need for complete re-architecture. This eliminates data duplication and sets up your ecommerce platform for high operational efficiency.
- Deliver lightning-fast shopping experiences without the overhead of re-platforming your entire commerce system. Use CCDM for your storefront while using your existing commerce platform for your backend requirements.
- Unlock catalog syndication and deliver the right content to the right destination by designing your product catalog to reflect how you do business including which products you sell, who you sell them to, what price they pay, and how you distribute these products. 
- Quickly ingest and update catalog data and rapidly deliver the updates to the storefront for your promotions and campaign needs.
- Add ready-to-use, lightning-fast UI components compatible with Edge Delivery Services for seamless product browsing and recommendations.
- Adopt a modern composable architecture using Adobe's extensibility architecture ([App Builder](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-development)) to import product data and power headless commerce storefronts using Adobe's [API Mesh](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-and-api-mesh).

## Architecture

CCDM is a highly scalable and flexible catalog data model which unlocks multi-brand, multi-business unit, multi-language use cases with ease. The model replaces the use of the classic Adobe Commerce product scopes (website, store, storeview) with new CCDM product scopes (channel, policy, and scope (locale)).

### Use cases

|Merchant type|Use case|Problems solved|
|---|---|---|
|Multi-brand conglomerate|- They sell several brands<br>- They sell in several countries<br>- They sell in different languages|Classic Adobe Commerce scopes (website, store, and storeview) would lead to data explosion. One would need a website for each brand, country and language.|
|Automobile/Manufacturing parts conglomerate| - Sells auto or machine parts. The products are the same for all customers.<br>- Different dealers sell parts to customers<br>- Each dealer has its own prices, stock and shipping methods|To have different shipping integrations, each dealer should have a separate website. But separate websites force the classic data model to duplicate catalogs.<br> So, if there are 3000 dealers in USA, a merchant creates 3000 catalog copies even though the same catalog is used by all dealers .<br> Data duplication interferes with performance limits.|
|Packaging/logistics company|- They have several shipping locations<br>- They have a different price for each customer<br>- The same product available in 2 locations for 2 customers have 4 possible prices|Despite the use of customer groups to cover pricing per customer, the classic model does not have the scope to manage price per location.<br> The only option is to copy each product for each location which means it is not the same root product anymore.<br> Data duplication interferes with performance limits.|

### Channel, Policy, and Scope

During product data ingestion and update, a SKU contains the details of scopes and attributes (the attributes map to channels and policies). These define the product context identifiers to which a SKU belongs:

![[!DNL Composable Catalog Data Model] Product Context Identifiers](assets/ccdm-product-id.png)

In the above image, each SKU contains:

- Scope identifiers​
    - Locale: Mandatory​
    - Brand, Market: Optional ​
- Product attributes
    - Product attributes are used to map to the relevant channels and policies​
    - Example: As an automobile manufacturer, you can choose to create a channel and policy combination for product attributes: (1) Dealers (2) Car brands.​

The channel and policy definitions are created using dedicated APIs:

![[!DNL Composable Catalog Data Model] Channel, Policy, and Scope Mapping](assets/ccdm-scope-map.png)

- **Scope** (locale) - Set at a SKU level during product data ingestion.​
- **Channel** - Definition created using dedicated APIs. ​
- **Policy** - Definition created using dedicated APIs.

## Overall commerce architecture – to be added 

With the above context, the full data model of CCDM can now be understood below:

??? Do we want to include the whole architecture diagram???

The above architecture diagram sheds light on how ecommerce Catalog Administrators and Merchandisers can leverage the Composable Catalog Data Model to craft and manage an entire product portfolio which scales for multi-brand, multi-language, multi-business unit use cases with ease without introducing data duplication.

### Use case

See the developer documentation for an end-to-end example that demonstrates how a company with a single base catalog can use CCDM to:

- Support products across two geographical markets and two different brands.
- Attain operational efficiency by not duplicating their product catalog across different websites.
- Limit product visibility on the websites based on the geographical market and the brand of the product.
