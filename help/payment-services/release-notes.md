---
title: Payment Services Release Notes
---
# Release Notes

These release notes describe the initial release of Payment Services and include:

*  ![New](../assets/new.svg) New features
*  ![Fixed issue](../assets/fix.svg) Fixes and improvements
*  ![Known issue](../assets/bug.svg) Known issues

## v1.0.0

*  ![New](../assets/new.svg)<!-- Issue PAY-2127 -->General availability release. [Payment Services](https://marketplace.magento.com/magento-payment-services.html) is now compatible with Adobe Commerce and Magento Open Source versions 2.4.0 to 2.4.3-p1.

*  ![New](../assets/new.svg)<!-- Issue PAY-124 -->The Payment Services extension for Adobe Commerce and Magento Open Source can be installed either for [Adobe Commerce on cloud infrastructure](install.md#magento-commerce-cloud) or [On-premises](install.md#on-premises) instances. These methods require the use of a Command Line Interface.

*  ![New](../assets/new.svg)<!-- Issue PAY-1986 -->Payment Services supports a [sandbox account](onboard.md#enable-sandbox-testing) that allows merchants to assess the extension in test mode.

*  ![New](../assets/new.svg)<!-- Issue PAY-666 -->Merchants can [configure Payment Services](configure-admin.html) extension with basic payment behaviors (such as Auth-capture together and switching between sandbox or production environments).

*  ![New](../assets/new.svg)<!-- Issue PAY-780 -->Shoppers can checkout with Payment Services or you can take the order over the phone and [create an entire order](create-order.md) in the Admin for them.

*  ![New](../assets/new.svg)<!-- Issue PAY-1856 -->Payment Services offer merchants comprehensive [reporting](financial-reporting.md) so that you can get a clear view of your store orders and payments.

*  ![New](../assets/new.svg)<!-- Issue PAY-311 -->Payment Services supports tiered pricing (based on TPV) adapted to any merchant.

*  ![New](../assets/new.svg)<!-- Issue PAY-1443 -->It is possible to customize the look and feel of PayPal buttons and the CC fields for the [Payment Services](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) extension.

*  ![Known issue](../assets/bug.svg)<!-- Issue PAY-2473 -->Using [incorrect composer keys](https://support.magento.com/hc/en-us/articles/4406603542541) during installation of the extension prevents user to [authenticate](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) with correct `MAGEID`.

*  ![Known issue](../assets/bug.svg)<!-- Issue PAY-2474 -->Payment Services [reports](https://support.magento.com/hc/en-us/articles/4406114741517) for Payout and Order payment status may not synchronize immediately.

*  ![Known issue](../assets/bug.svg)<!-- Issue PAY-2475 -->[PayPal sandbox account](https://support.magento.com/hc/en-us/articles/4406954952461) for Payment Services cannot be verified.
