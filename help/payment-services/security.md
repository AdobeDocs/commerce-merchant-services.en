---
title: Security and compliance
description: Review security and compliance requirements for your site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
---
# Security and compliance

Security is of the utmost concern in [!DNL Payment Services] and no private or Payment Card Industry (PCI) regulated information is passed across your [!DNL Payment Services].

## Commerce security

[!DNL Adobe Commerce] and [!DNL Magento Open Source] include support for several security features.

See [Security](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} in the core user guide to review security best practices, and learn how to manage Admin sessions and credentials, implement CAPTCHA, and manage website restrictions.

## PCI compliance

The Payment Card Industry (PCI) established a set of requirements for businesses that accept payment by credit card over the Internet. In addition to maintaining a secure environment, merchants who handle customer credit card information are responsible for meeting some standard guidelines.

See [PCI Compliance Guidelines](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} for more information.

Merchants can complete a [self-assessment questionnaire (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, which is a self-validation tool to assess security for cardholder data.

### Credit Card Fields

With Credit Card Fields, no PCI-regulated data is passed across your services. You don't have to store or maintain that data, which vastly reduces PCI compliance concerns.

### Card vaulting

When a shopper [vaults---or "saves"---their credit card information](vaulting.md) for future purchases in your stores, minimal credit card information is shared with the shopper (last four digits, card expiration date, and brand of card). Credit card information is stored with the payment provider. When a card expires, or they no longer need the information saved, they can delete that token so that the information is no longer stored by the payment provider.

### PayPal Smart Buttons

With PayPal Smart Buttons, no PCI-regulated data is passed across your services. You don't have to store or maintain that data, which vastly reduces PCI compliance concerns.

For security reasons, PayPal does not pass the billing address during checkout---country, email, and name is the only billing information used. You can optionally enable your site's PayPal checkout to return the complete billing address by contacting PayPal and completing a vetting process.

PayPal also has integrated fraud protection that uses machine learning to help you fight fraud. See PayPal's [Seller Protection documentation](https://www.paypal.com/us/webapps/mpp/security/seller-protection) for more information.
