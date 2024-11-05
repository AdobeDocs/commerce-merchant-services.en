---
title: '[!DNL Composable Catalog Data Model]'
description: 'Learn how the [!DNL Composable catalog data model] for Adobe Commerce helps you setup your catalog to match your business model and go-to-market strategy'
recommendations: noCatalog
---
# [!DNL Composable catalog data model] for Adobe Commerce

Using the Adobe Commerce Composable catalog data model, you can map your unique business model to your ecommerce channels with ease including:

- **Multibrand**–Sell multiple brands in multiple countries from one platform
- **B2B2C/B2B2B**—Sell products at different prices based on your dealer, distributor, or reseller network
- **B2B Commerce**–Reflect negotiated prices (price books) and control which products you sell to specific customers online

SAMPLE MESSAGING:

Adobe Commerce's catalog data model allows you to set-up your catalog to match your business model and go-to-market strategy.

It allows you to import your product data including prices, attributes, and other data from your back-office systems such as Product Information Management (PIM), Enterprise Resource Planning (ERP) and other sources using our data ingestion APIs
It allows you to create unique variations of your base catalog to fit how you do business including channel, country/locale, prices, customer type, and more
It exposes this catalog data model to your storefront using headless APIs
All of this is hosted on Adobe's cloud architecture for scalable data processing and rendering to front-end shoppers.
Using the Adobe Commerce's catalog data model you can map your unique business model to your ecommerce channels with ease including:

Multi-Brand: Sell multiple brands in multiple countries from one platform
B2B2C / B2B2B: Sell products at different prices based on your dealer, distributor or reseller network
B2B Commerce Reflect negotiated prices (price books) and control which products you sell to specific customers online
And more…

Target persona

*Business decision maker who wants to know if Adobe Commerce can support how they do business.

*Solution Architect that works for a solution partner

*Developer who is familiar with Adobe Commerce

Use it in a sentence

The composable catalog data model allows you to set-up your product catalog and prices in Adobe Commerce the way you want to do business online.

Composable catalog data model – a new solution for designing your product catalog in Adobe Commerce to match your business strategy including countries you sell in, who you sell to, and other settings.



Milestone 1: 

Goal: All the capabilities which are required to:
Demo the MVP version of Phase 1.
End-to-end validation of all the concepts we have planned: From feed ingestion to display on storefront.
Ready for initial VIP engagement.

As a merchant I am able to:

Ingest data directly into Adobe Commerce SaaS layer (DCAT-1746)
Create simple products (DCAT-1693)
Create prices book information for products (DCAT-1682)
Create channels (DCAT-1692)
Create policies (DCAT-1683)
Query data from Catalog Storefront service, Live Search and PREX (DCAT-1718, DCAT-1719, DCAT-1720, DCAT-1721, DCAT-1722, DCAT-1723)


So that:

I can use the catalog data(simple products) in the storefront for both browse and checkout experience.




Important Note:

We should explore how we can demo this end-to-end (ingestion to storefront) with the help of PDP drop-in and PLP widget. This demo can be a foundation for all future capabilities.

Docs should cover:
1. How to send data directly to SaaS
1. How to send data to Core Commerce

So, think about CCDM as just a data modelling capability for a catalog

Currently for summit, Commerce Optimizer is essentially a stand alone DX UI(and not coupled with Commerce monolith in anyway - fully decoupled) for our following capabilities:

Direct Data ingestion into SaaS (completely ignoring monolith)
Storefront servies: CS, LS, PREX APIs
LS, PREX merchandising rules UI (currently in Commerce monolith UI, but since optimizer is not related to monolith at all, we will support LS, PREX rule management in our new UI)
So basically, optimizer is a 'SaaS only' story with a net new UI which is hosted on Dx. (The goal is to sell SaaS without requiring to sell commerce monolith)

So essentially in the near future we will have the following flavors of Commerce implementations:
Only Commerce monolith (existing)
Commerce monolith + existing SaaS (existing)
Commerce monolith + CCDM SaaS (new -> this is planned for dec '24 release)
Commerce optimizer (CCDM + LS, CS, PREX)

Concepts​

Channels define your retail structure in meaningful business groups ​
Dealers for automotive industry.​
Subsidiaries for multi-brand conglomerate.​
Manufacturing location for suppliers.​

​Policies define data access filters which empower you to deliver the right content to the right destination.​
POS physical stores​
Marketplaces​
Advertisement pipelines(Google, FB, IG)​

Locales help you segregate data right at the data ingestion phase 


Capabilities​

Flexible product components…​
Simple, configurable, bundles, bundle of bundles​
Subscriptions​
Attachments​

​Scale with ease…​
Multi-brand, multi-geography support with a single data ingestion​
Rapid delivery of product/price updates to storefront​

​Minimal customizations…​
Map your catalog model to how you deliver your business goals​


WITH CCDM, your catalog data goes directly into SaaS rather than Commerce database then SaaS. This speeds up API calls and responses to the catalog significantly and ultimately delivers a more performant catalog.

Adobe Commerce's Composable catalog data model allows you to set up your catalog to match your business model and go-to-market strategy.

- Integrate with backend systems and use Adobe's ingestion APIs to import product data including prices, attributes, and other data from your Product Information Management (PIM), Enterprise Resource Planning (ERP) or other system

- Create unique versions of your base catalog to match how you run your business including distribution and sales channels, locale, customer type, and more.

- Power lightning fast storefront experiences by querying your Composable catalog data model using Adobe's headless APIs and delivering data via Adobe Edge delivery services or other headless storefront implementations.

## Architecture

<!--Add architecture diagram ![Catalog data model architecture](assets/ls-cs-data-flow.png) -->














Background
Overview, Architecture and Implementation (Data Modeling with Catalog Service)

Intro - solution overview, concepts, architecture, 
Explain where data resides (In CCDM, or remain in core commerce)
Explain use case in context of new customers (Milestone 1) and existing customers (migration, using Commerce with CCDM) 
Differences between existing implementation and CCDM context (initial state to migrated state) - might not need to included in CCDM docs, but awareness of differences can help identify updates required to existing docs (product widgets, adapters,understanding data still residing in core and how to use)
Content Plan
Expectations:

Engineering owners to ensure the API docs are provided to Margaret Eker 
Margret consolidates each section and Product managers(Sandra Gonzalez Mangana Alex Jose ) review this.



Intro and Overview (Milestone 1)

What is the Composable Catalog Data Model for Adobe Commerce?
Product description, capabilities, advantages, architecture, implementation overview

Technical Admin
Admin users    
DATA-5927 - Docs Update: Catalog data model Experience League overview Options Queue

Alex Jose 

Onboarding/Getting Started Workflow (Milestone ?)

Prerequisites and requirements for using CCDM

Technical Admin    

Admin User Management

Overview

Entitlement, Account management and permission
Revoke access
Logging (question)




Implementation Workflow (Milestone ?)

Develop Catalog model to enable business use cases vel example with diagrams based on VIP customers (Radwell, Toyota, ...) 

All users with focus on Commerce developers (SIs), business analysts, merchandisers, 