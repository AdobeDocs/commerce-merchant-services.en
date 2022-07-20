---
title: User session lifetime
description: The Admin provides the ability to configure the cookie lifetime of your Adobe Commerce user for the [!DNL Quick Checkout] extension.
---

# User session lifetime

The lifetime of a shopper session is determined by several factors, which can be configured in your Adobe Commerce Admin. See [Configure the cookie lifetime](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} for more information.

The configured lifetime of cookies can affect your [!DNL Quick Checkout] if:

1. Due to inactivity, the shopper is logged out of Adobe Commerce.
1. The [!DNL Bolt] session expires.

If a shopper places an order when their [!DNL Bolt] session expires, the order is successfully placed but the user is logged out from both networks.

If the user is still active after a successful checkout, they will not be logged out from both Adobe Commerce and [!DNL Bolt].
