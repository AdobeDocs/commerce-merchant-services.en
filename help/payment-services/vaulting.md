---
title: Credit Card Vaulting
description: Shoppers can vault (save) their credit card details for future purchases.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
---
# Credit Card Vaulting

Convert one-time customers into loyal shoppers with credit card vaulting. Shoppers can save---or "vault"---their credit card credentials during checkout to use in a later purchase for the same, or another, store within the same merchant account.

![Vault their credit card for later use](assets/save-card-for-later.png){width="400" zoomable="yes"}

Shoppers use the stored token to complete a future checkout with their saved credit card information.

![Use stored credentials for future purchase](assets/use-stored-card.png){width="400" zoomable="yes"}

They can also easily delete their vaulted credit cards from [Stored Payment Methods](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) in their My Account.

![Stored Payment Methods in My Account](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal can currently store a maximum of five vaulted cards.

## Enable vaulting

You can enable credit card vaulting---for customers _and_ merchants in the Admin---for your stores in [!DNL Payment Services] [Settings](settings.md#card-vaulting).

## Use vaulting in the Admin

If a customer has a previously vaulted credit card, a merchant can create a subsequent order for that customer in the Admin using their vaulted payment methods.

You can only use vaulted cards in the Admin if the customer has both an existing account and a valid token stored in the system from a previously completed payment.

To create an order in the Admin for a customer using their vaulted credit card:

1. [Create an order and add products](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. In _[!UICONTROL Payment & Shipping Information]_, select **[!UICONTROL Stored Cards]** as the payment method.
1. Select the desired vaulted credit card payment method.
1. After completing any other necessary steps for the order, [submit it](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Use vaulted credit card in Admin for customer](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Security

Minimal credit card information is shared with the shopper; they only see the last four digits, expiration date, and brand of their vaulted credit card. Credit card information is stored with the payment provider to satisfy [PCI](security.md#PCI-compliance) compliance standards.
