---
title: Onboarding
description: Learn the requirements and supported platforms in [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
---
# Onboarding

The onboarding process for [!DNL Product Recommendations] requires access to the command line of the server and consists of the following steps. If you are not familiar with working from the command line, ask a developer or system integrator to help.

- [Implementation Workflow](implementation-workflow.md)
- [Install and Configure](install-configure.md)
- [Settings](settings.md)
- [Verify](verify.md)
- [Staging Environment](staging-environment.md)

## Requirements

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Composer 2

### Supported platforms

- Adobe Commerce on premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

### Page Builder support

[!DNL Product Recommendations] can be added to a page as a Page Builder content type. To add Page Builder support to Product Recommendations, refer to [Install and Configure](install-configure.md).

See [[!DNL Page Builder] Integration](page-builder.md) for instructions on how to add [!DNL Product Recommendations] into [!DNL Page Builder] content.

## Price indexer

Product Recommendation customers can use the new [SaaS price indexer](../price-index/index.md), which provides faster price changes updates and synchornization time.

### B2B support {#b2bsupport}

B2B storefronts often require complex logic that dictates product visibility and pricing for each shopper or customer group. [!DNL Product Recommendations] now [support](release-notes.md) this functionality by honoring [category permissions](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [shared catalogs](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), and [customer group-specific pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). For example, if you have hidden certain categories from your retail customer segment, then a shopper in that segment would not be shown recommendations for products in those categories. Also, when you define a shared catalog for specific customer groups and companies, those shoppers see recommendations only for products they can access. All recommended products reflect correct customer group-specific price based on each shopper's customer group.
