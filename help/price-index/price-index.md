---
title: Price Indexing Service
description: Using the Price Indexing service to improve performance
seo-title: Adobe Commerce Services Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
---
# Price Indexing Service

The Price Indexing Service moves price calculations from the single-threaded monolith to Adobe's multi-threaded cloud environment. This vastly decreases indexing time for large catalogs and frees up server resources for other tasks. 

This indexing is available for free for Commerce customers. It is built into existing SaaS products. 

This mini-guide describes how this service works and how to enable it.

## Overview

The price indexer service works by disabling the internal price indexer and sending the data to the SaaS infrastructure through the new Price feed. Prices are then sent directly to customer facing page, also increasing performance.

### System requirements

To get the SaaS price indexer, you need:

* Adobe Commerce 2.4.5+ (2.4.4 support coming in 2023)
* At least one of the following SaaS services:

    * Catalog Service
    * Live Search
    * Product Recommendations

* Installation of supporting extensions

>[!Note]
>
> Currently, the new price indexer only supports Simple, Virtual, Configurable, and Bundle Dynamic products types. Support for Downaloable, Gift Cards, and Bundle Fixed product types is expected in 2023.

## FAQ

1. What are these improvements and how are they achieved?

The improvements for the price indexation process and synchronization time are the result of a project that sought to speed up the time it takes for price changes to get reflected on a customer's website after they have been submitted. It allows merchants, especially those with large and complex catalogs, or that have a large number of websites or customer groups, to process price changes more rapidly and continuously.

1. Where are the speed improvements coming from? How is the process changing compared to the old one?

We are removing the biggest bottleneck of the pipeline: moving computational heavy processes (indexation, calculation, computation) from the single-threaded PHP monolith, to the multi-thread Cloud infrastructure. This allows merchants to quickly scale up resources to boost price indexation times, and reflect those changes to websites at much faster speeds.

1. What are the requirements?

* Adobe Commerce 2.4.4+
* Any of the supported SaaS applications must be installed: Live Search, Product Recommendations, and Catalog Service for Adobe Commerce

1. Who is this for?

Merchants who will see the largest uptick are those with:

* Frequent price changes
* Multiple websites and/or customer groups
* Large number of unique prices across websites or customer groups.

1. What are the main benefits?

Considerable reduction in time to process price changes and see them reflected on website.
It uses Adobe's cloud infrastructure. The customer's Adobe Commerce instance is no longer used to process these calculations, freeing up resources for other processes.

1. What speed improvements can I expect from this new process?

Price changes are updated across websites and customer groups up to 90% faster, depending on catalog composition and the frequency of prices updates.

1. Will Magento OS be supported?

SaaS services are only available to Adobe Commerce customers.

1. Do I have to pay for the price index service?

No, it is free to utilize for all Adobe Commerce merchants

1. Will extensions or apps that rely on the current price indexer be affected? If so, how?

If you have 3rd party applications that rely on the current price indexer, we recommend you read our documentation and consult with the extension provider before making any changes. 
