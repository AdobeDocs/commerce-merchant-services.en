---
title: Guide Overview
description: Adobe Experience Platform connector for Adobe Commerce connects your [!DNL Commerce] instance to other Adobe Experience Cloud products.
---
# Experience Platform connector overview

The Experience Platform connector extension allows Adobe Commerce merchants to send data to the Adobe Experience Platform edge so other Adobe Experience Cloud products, such as Adobe Analytics and Adobe Target, can use that [!DNL Commerce] data. By connecting your [!DNL Commerce] data to other products in the Adobe Experience Cloud, you can perform tasks, such as analyze user behavior on your site, perform AB testing, and create personalized campaigns.

Storefront events capture shopper interactions, such as `View Page`, `View Product`, `Add to Cart`, and so on. Captured data does not include personally identifiable information (PII). All user identifiers, such as cookie IDs and IP addresses, are strictly anonymized. [Learn more](https://www.adobe.com/privacy/experience-cloud.html). See the complete list of [storefront events](events.md).

## Prerequisites for using the Experience Platform connector {#prereqs}

To use the Experience Platform connector, you must first:

- Fill out the following [form](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) and Adobe will provision you with access to Datastreams and the Adobe Experience Platform (if needed).

When access is granted:

1. [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account.
1. Look at your [organization](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) @AdobeOrg.
1. Access the datastream workspace and [create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en).

The organization ID and datastream is used when you connect your Adobe Commerce instance to the Adobe Experience Platform.

## Next steps

- Install the [Experience Platform connector extension](install.md).

    The Experience Platform connector extension is installed from the command line of the server and connects to your Adobe Commerce installation as a [service](../landing/saas.md). When the process is complete, Experience Platform connector appears on the **System** menu under **Services** in the [!DNL Commerce] _Admin_.

## Audience

This guide is designed for the Adobe Commerce merchant who must connect their Adobe Commerce storefront data to other Adobe DX products.

## Known issues

Currently, the Experience Platform connector has the following known issues:

- Search events are not supported on an Adobe Commerce Enterprise Edition with the B2B module installed.
- Storefront data takes about an hour to get from Adobe Commerce to the various destinations after connecting to the Adobe Experience Platform edge.

## Support

If you need information or have questions that are not covered in this guide, post to the following Slack channel:

- `#beacon-ama`
