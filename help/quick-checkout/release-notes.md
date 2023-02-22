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

_December 14, 2022_

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-524 --> The [!DNL Quick Checkout] Admin panel now shows the correct total orders and updated reporting information.

_November 30, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-502 --> Now, the [reporting](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tab has a new "Last year" preset.

![New](../assets/new.svg)<!-- Issue BOLT-471 --> User experience improvements in the [!DNL Quick Checkout] Admin panel show more information in [Tooltips](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-514 --> User experience improvements in the [!DNL Quick Checkout] Admin panel show correct total orders numbers, consistency in colors, and the correct legends for all charts.

_November 2, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-293 --> Now, the [reporting](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tab in the [!DNL Quick Checkout] Admin panel shows charts and reporting information of your store's checkout experience statistics.

![New](../assets/new.svg)<!-- Issue BOLT-422 --> The [_Overview_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) section of the Reports topic section shows detailed information about your store's checkout performance, including the average checkout time, new accounts created during checkout, and checkout abandonment.

![New](../assets/new.svg)<!-- Issue BOLT-423 --> The [_Trends_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) section of the Reports tab shows your checkout experience trends filtered by account type and new accounts created during checkout.

![New](../assets/new.svg)<!-- Issue BOLT-439 --> The **Reports** tab displays [default filter presets](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) that can be used to show specific data ranges.

![New](../assets/new.svg)<!-- Issue BOLT-433 --> You can now see a _No Data Available_ warning for a chart when a request returns no data.

![New](../assets/new.svg)<!-- Issue BOLT-473 --> User experience improvements from the [!DNL Quick Checkout] Admin panel include the ability to enable a [checkout tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) setting that allows Adobe Commerce to share reporting information with Bolt.

_October 5, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-379 --> Now, when a new merchant accesses the [!DNL Quick Checkout] Admin panel for the first time a [feature tour powered by Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) appears.

![New](../assets/new.svg)<!-- Issue BOLT-377 --> The **Reports** tab in the [!DNL Quick Checkout] Admin panel shows charts and reporting analytics.

![New](../assets/new.svg)<!-- Issue BOLT-377 --> The **Reports** tab in the [!DNL Quick Checkout] Admin panel shows the date range and filter presets for charts and reporting analytics.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-369 --> Now, the [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) displays the app version in the footer.

+++

## v1.7.0

_February 22, 2023_

![Fixed issue](../assets/fix.svg)<!-- Issue AC-8002 --> User experience improvements when placing an order using a [Multishipping](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) method. This functionality enables the display of payment methods during checkout when [!DNL Quick Checkout] is enabled.

## v1.6.0

_February 9, 2023_

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-567 --> User experience improvements when [placing an order](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) using the [In-store delivery](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) method with the [!DNL Quick Checkout] disabled.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-569 --> Improvements in the logout functionality that allows shoppers to [logout from the Bolt Network](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_January 18, 2023_

![New](../assets/new.svg)<!-- Issue BOLT-522 --> A new configuration can be enabled/disabled to detect if [shoppers](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) can be automatically logged in Bolt.

![New](../assets/new.svg)<!-- Issue BOLT-523 --> A new configuration can be enabled/disabled that allows merchants to specify if shoppers can be automatically logged in to both networks, or just Bolt network.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-542 --> User experience improvements when [saving card or address to a Bolt account](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) when a shopper provides email.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-550 --> User experience improvements in [automatic login](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) when a Bolt user provides email.

![Fixed issue](../assets/fix.svg)<!-- Issue BOLT-544 --> Compatibility improvements for [callback URLs](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) with [multi-sites](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) in Bolt. 

## v1.4.0

_November 30, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-513 --> Now, when an Adobe Commerce customer is logged into the store during the checkout process, and has a Bolt account, an option to log into the shopper's Bolt account is displayed.

![New](../assets/new.svg)<!-- Issue BOLT-512 --> A new configuration automatically detects if logged-in shoppers can also be logged in Bolt.

![New](../assets/new.svg)<!-- Issue BOLT-480 --> A new configuration in the [!DNL Quick Checkout] Admin Panel allows you to change the default navigation flow to the **Shipping** page once a Bolt customer logs in. By default, it is configured to the **Payments** page.

## v1.3.0

_November 2, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-293 --> Now, [!DNL Quick Checkout] includes the ability to enable a [checkout tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) setting that allows Adobe Commerce to share reporting information with Bolt.

![New](../assets/new.svg)<!-- Issue BOLT-461 --> You can now see a warning message in your [!DNL Quick Checkout] Admin panel if [checkout tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) configuration is disabled.

## v1.2.0

_September 8, 2022_

![New](../assets/new.svg)<!-- Issue BOLT-341 --> General availability release---[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) is now compatible with Adobe Commerce versions 2.4.5.

![New](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] for Adobe Commerce and Magento Open Source provides an [Admin panel view](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) with all the necessary information to set up and use the extension.

![New](../assets/new.svg)<!-- Issue BOLT-364 --> An administrator user [can set up user roles and permissions](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) to allow other users to view the [!DNL Quick Checkout] Admin panel.

![New](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] Admin panel now contains a page header that includes specific sections such as **Overview**, **Reports**, and **Settings**.

![New](../assets/new.svg)<!-- Issue BOLT-379 --> When a new merchant accesses the [!DNL Quick Checkout] Admin panel for the first time a Welcome widget appears that provides a feature tour.

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

![Known issue](../assets/bug.svg)<!-- Issue BOLT-342 --> Common [troubleshooting](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) issues during installation of [!DNL Quick Checkout].
