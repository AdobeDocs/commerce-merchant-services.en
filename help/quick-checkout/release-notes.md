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

## Admin panel updates

These release notes describe feature changes and fixes that occurred and were released outside of the regular versioned feature releases for the Admin panel.

+++Admin panel updates

_October 5, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-379 --> [!DNL Quick Checkout] Admin panel integrates a [feature tour powered by Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html).

![New](../assets/new.svg)<!-- Issue BOLT-377 --> The **Reports** tab in the [!DNL Quick Checkout] Admin panel contains the outline of diagrams and reporting information that will soon be available.

![New](../assets/new.svg)<!-- Issue BOLT-377 --> The **Reports** tab in the [!DNL Quick Checkout] Admin panel shows the filter date range for diagrams and reporting information that will soon be available.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-369 --> [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) now displays the react app version in the footer.

+++

## v1.2.0

_September 8, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-341 --> General availability release---[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) is now compatible with Adobe Commerce versions 2.4.5.

![New](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] for Adobe Commerce and Magento Open Source provides an [Admin panel view](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) with all the necessary information to set up and use the extension.

![New](../assets/new.svg)<!-- Issue BOLT-364 --> An administrator user [can set up user roles and permissions](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) to allow other users to view the [!DNL Quick Checkout] Admin panel.

![New](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] Admin panel now contains a page header that includes specific sections such as **Overview**, **Reports**, and **Settings**.

![New](../assets/new.svg)<!-- Issue BOLT-379 --> [!DNL Quick Checkout] Admin panel adds a Welcome widget that provides a feature tour powered by Gainsight.

![New](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Admin panel view](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorporates a **Configuration** step that appears when the API and publishable keys are not provided in the [Settings](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) view.

![New](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Admin panel view](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorporates a **Resources** section that changes depending on the onboarding stage.

![New](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Admin panel view](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) includes a **Help and Support** section.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-369 --> The [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) now displays the extension version in the footer.

## v1.1.0

_August 12, 2022_

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-375 --> User experience improvements in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) now include only the parameters that are visible and validated when the extension is enabled.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-349 --> Compatibility improvements for existing shipping addresses with the Bolt wallet.

## v1.0.0

_August 9, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-341 --> General availability release---[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) is now compatible with Adobe Commerce versions 2.4.1 to 2.4.4.

![New](../assets/new.svg)<!-- Issue BOLT-340 --> The [!DNL Quick Checkout] for Adobe Commerce can be installed either for Adobe Commerce [on cloud infrastructure](install.md#adobe-commerce-on-cloud-infrastructure) or [on-premises](install.md#on-premises) instances. These methods require the use of a command-line interface.

![New](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerce brings an optimized storefront that allows for a [one-click checkout experience](overview.md) with no filling fields required for consumers.

![New](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerce automatically recognizes each shopper in its network for [one-click purchases](checkout-flow.md) directly on your site.

![New](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerce allows a shopper to be simultaneously [logged in both Adobe Commerce and Bolt networks](checkout-flow.md/#quick-checkout-use-cases) to provide a better `one-click checkout` experience.

![New](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] for Adobe Commerce supports a [sandbox account](testing.md#testing-in-sandbox) that allows merchants to assess the extension in test mode.

![New](../assets/new.svg)<!-- Issue BOLT-780 --> Your shoppers can check out via the [[!DNL Quick Checkout]](checkout-page.md) extension or via a [manual order creation](create-order-admin.md).

![New](../assets/new.svg)<!-- Issue BOLT-666 --> Merchants can configure the [!DNL Quick Checkout] with basic payment actions, such as [`Authorize and Capture` or `Authorize` ](onboarding.md#complete-admin-configuration), or switching between sandbox and production environments.

![New](../assets/new.svg)<!-- Issue BOLT-288 --> Custom [user session lifetime](user-session-lifetime.md) for [!DNL Quick Checkout] for Adobe Commerce.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-375 --> User experience improvements in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) allows you to save your configuration when all required parameters are provided.

![Known issue](../assets/bug.svg)<!-- Issue BOLT-342 --> Common [troubleshooting](https://support.magento.com/hc/en-us/articles/6909450342541) issues during installation of [!DNL Quick Checkout].
