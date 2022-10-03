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

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4 / 8.1
- Composer

### Supported platforms

- Adobe Commerce on prem (EE) : 2.4.x
- Adobe Commerce on Cloud (ECE) : 2.4.x

### Page Builder support

[!DNL Product Recommendations] can be added to a page as a Page Builder content type. To add Page Builder support to Product Recommendations, refer to [Install and Configure](install-configure.md).

   >[!NOTE]
   >
   >[!DNL Page Builder] recommendation units can be created only for the default store view.

### B2B support {#b2bsupport}

B2B storefronts often require complex logic that dictates product visibility and pricing for each shopper or customer group. [!DNL Product Recommendations] now [support](release-notes.md) this functionality by honoring [category permissions](https://docs.magento.com/user-guide/catalog/category-permissions.html), [shared catalogs](https://docs.magento.com/user-guide/catalog/catalog-shared.html), and [customer group-specific pricing](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). For example, if you have hidden certain categories from your retail customer segment, then a shopper in that segment would not be shown recommendations for products in those categories. Also, when you define a shared catalog for specific customer groups and companies, those shoppers see recommendations only for products they can access. All recommended products reflect correct customer group-specific price based on each shopper's customer group.
