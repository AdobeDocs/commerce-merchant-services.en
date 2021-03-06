---
title: '[!DNL Quick Checkout] Release Notes'
description: Review the release notes for information about all [!DNL Quick Checkout] releases.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
---
# Release Notes

These release notes describe the initial release of [!DNL Quick Checkout] and include:

![New](../assets/new.svg) New features
![Fixed issue](../assets/fix.svg) Fixes and improvements
![Known issue](../assets/bug.svg) Known issues

See [Upcoming Releases](https://devdocs.magento.com/release/) to learn about release schedules and support.

See [Availabilty](https://devdocs.magento.com/release/availability.html) in the developer documentation to learn about product compatibility.

## v1.0.0

![New](../assets/new.svg)<!-- Issue BOLT-341 --> General availability release---[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) is now compatible with Adobe Commerce versions 2.4.1 to 2.4.4.

![New](../assets/new.svg)<!-- Issue BOLT-340 --> The [!DNL Quick Checkout] for Adobe Commerce can be installed either for Adobe Commerce [on cloud infrastructure](install.md#adobe-commerce-on-cloud-infrastructure) or [on-premises](install.md#on-premises) instances. These methods require the use of a command-line interface.

![New](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerce brings an optimized storefront that allows for a [one-click checkout experience](overview.md) with no filling fields required for consumers.

![New](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerce automatically recognizes each shopper in its network for [one-click purchases](checkout-flow.md) directly on your site.

![New](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] for Adobe Commerce supports a [sandbox account](testing.md#testing-in-sandbox) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue BOLT-780 --> Your shoppers can check out via the [[!DNL Quick Checkout]](checkout-page.md) extension or via a [manual order creation](create-order-admin.md).

![New](../assets/new.svg)<!-- Issue BOLT-666 --> Merchants can configure the [!DNL Quick Checkout] with basic payment actions, such as [`Authorize and Capture` or `Authorize` ](onboarding.md#complete-admin-configuration), or switching between sandbox and production environments.

![Known issue](../assets/bug.svg)<!-- Issue BOLT-342 --> Using [incorrect Composer keys](https://support.magento.com/hc/en-us/articles/6909450342541) during installation of the [!DNL Quick Checkout] prevents the user from [authenticating](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with the correct `MAGEID`.
