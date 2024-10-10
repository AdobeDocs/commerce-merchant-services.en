---
title: Implementation Workflow
description: Learn the steps to successfully implement [!DNL Product Recommendations] on your storefront.
exl-id: 766e1191-0330-4515-9331-e45318539dc9
---
# Implementation Workflow

[!DNL Product Recommendations] uses both behavioral and catalog data:

- Behavioral - Data from a shopper’s engagement on your site, such as product views, items added to a cart, and purchases. Adobe Commerce and Adobe Sensei do not collect personally identifiable information.

- Catalog - Product metadata, such as name, price, and availability.

When you install the `magento/product-recommendations module`, Adobe Sensei aggregates the behavioral and catalog data and creates [!DNL Product Recommendations] for each recommendation type. The [!DNL Product Recommendations] service then deploys those recommendations to your storefront. To help you implement product recommendations on your storefront, use the following workflow:

>[!NOTE]
>
> If your storefront is implemented using PWA Studio, refer to the [PWA documentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). If you use a custom frontend technology such as React or Vue JS, learn how to [integrate](headless.md) [!DNL Product Recommendations] into your headless storefront.

## Workflow

1. **Deploy data collection to production**

   Deploying [!DNL Product Recommendations] requires two main [data sources](type.md): catalog and behavioral. Because production is the only environment where your shoppers' actions are captured and analyzed, start data collection on production as early as possible. [Learn](events.md) how Adobe Sensei trains machine learning models that results in higher-quality recommendations. As an added benefit, when you start collecting behavioral data on production, you can [fetch recommendations](verify.md) based on this production data while operating in non-production environments. You can then test and experiment with different recommendations that are computed based on real shopper data collected in production.

   To deploy data collection to production, you must [install and configure](install-configure.md) the [!DNL Product Recommendations] module by providing an [API key](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > Deploying data collection does not change your storefront's appearance or your shoppers' experience. Only creating and deploying recommendation units alters the customer experience on your storefront. Make sure you test on your non-production environment before deploying to production. Also, do not create recommendation units until you customize your template. See the next step.

1. **Customize the template to match your style**

   Your storefront represents your brand, so make sure you modify the product recommendations template to match your site theme.

   >[!TIP]
   >
   > By customizing the template, you can specify your stylesheet, overwrite where a recommendation unit appears on a page, and so on.

   See [Customize](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) in the developer documentation to learn how to complete this step.

1. **Test recommendations on your non-production environment**

   It is always a best practice to test a new technology on your non-production environment before you deploy to production. Testing recommendations on your non-production environment allows you to play with different recommendation unit types, positioning, and pages. You can pull recommendations based on behavioral data already gathered on production while testing in your non-production environment, so that recommendation results are based on the shopping behavior of actual customers.

   >[!TIP]
   >
   > Ensure your non-production environment catalog is largely the same as the one that you have in production. Using similar catalogs ensures that the products returned in the recommendation units closely mimic the products on production.

   See [Fetch](staging-environment.md) behavioral data from your production environment to learn how to complete this step.

1. **Create and deploy recommendations to your production storefront**

   Now that you have deployed the behavioral data collection in production, modified the product recommendations template, and tested recommendations using actual shopper behavior, you are ready to promote all code to production and [create](create.md) live product recommendations.
