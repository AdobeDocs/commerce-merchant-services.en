---
title: Test in Staging Environment
description: Learn how to use [!DNL Product Recommendations] from your production environment in your staging environment for testing purposes.
---
# Test in Staging Environment

Before you deploy recommendations to your production environment, you should test on a non-production environment to ensure that everything is working as expected.

[!DNL Product Recommendations] return products based on [shopper-behavioral data](behavioral-data.md) collected from your storefront. In a non-production environment, however, it is likely you do not have any behavioral data from shoppers. The only recommendation type that you can test without behavioral data is `More like this`. This recommendation type does not require any input data, as it uses a direct content similarity match.

The following recommendation types require behavioral data:

- Most Viewed
- Viewed this, viewed that
- Bought this, bought that

How can you test your recommendations in a non-production environment using behavioral data? There are a couple of options.

## Fetch recommendations from production environment (recommended)

Adobe Commerce allows you to fetch recommendations from your production environment and preview them in your non-production environment by [switching](settings.md) the SaaS data space.

To fetch recommendations from your production environment, you must make sure that:

- Storefront data collection is [configured and enabled](install-configure.md) on production.
- Your non-production environment catalog is largely the same as the one that you have in production. Using similar catalogs ensures that the products returned in the recommendation units closely mimic those on production.

## Generate behavioral data on non-production environment

1. Deploy the `magento/product-recommendations` module to a non-production environment where the catalog data is similar to your production catalog.

1. Use one of the non-production Data Space IDs for [configuration](https://docs.magento.com/user-guide/configuration/services/saas.html) in the Admin.

1. Generate the data yourself by clicking around your storefront to mimic the behavior of actual shoppers (or create an automation script). Through your testing, you generate behavioral events on your non-production environment. Those events are used to produce the product affinities that power recommendations. For testing, [!DNL Commerce] suggests that you interact with the following recommendation types:

   - Most Viewed - Requires minimal input data. Users must view products.
   - Viewed this, viewed that - Requires multiple users to view multiple products.
   - Bought this, bought that - Requires multiple users to purchase multiple products.

### Caveats

- The behavioral and catalog data from the non-production SaaS Data Space identify an isolated environment in which the resulting product recommendations are based entirely on the behavioral data generated on the associated storefront.

- Because you do not have large amounts of behavioral data, input data for computing product associations is sparse. However, that data is still sent to Sensei to compute the machine learning models and provide recommendations based on data you generated within this environment.
