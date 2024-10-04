---
title: 'How [!DNL Commerce] Services Handles Privacy Requests'
description: Learn how [!DNL Commerce] services handles requests to access and delete data.
role: Admin, Leader
feature: Security, Compliance
---
# Privacy requests

Adobe Experience Platform Privacy Service provides a RESTful API and user interface to help you manage customer data requests. With Privacy Service, you can submit requests to access and delete personal customer data from Adobe Experience Cloud applications, facilitating automated compliance with legal and organizational privacy regulations.

For more information on the Privacy Service and how to create and manage privacy requests, see the Adobe Experience Platform documentation:

* [Privacy Service overview](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html)
* [Managing privacy jobs in the Privacy Service UI](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html)

## Managing individual data privacy requests

You can submit individual requests to access and delete consumer data from [!DNL Commerce] in two ways:

* Through the **Privacy Service UI**. See the documentation [here](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide#_blank).
* Through the **Privacy Service API**. See the documentation [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/#_blank) and API information [here](https://developer.adobe.com/experience-platform-apis/#_blank).

The Privacy Service supports two types of requests: **data access** and **data deletion**.

## Data access

For **access requests**, specify "Commerce Data for Marketing" from the UI (or "???" as a product code in the API).

## Data deletion

For deletion requests, the Privacy Service deletes all [!DNL Commerce] data stored in the Experience Platform for marketing purposes, meaning profiles and orders of data subjects are no longer sent to Adobe marketing applications for use in campaigns and customer journeys. However, the Privacy Service does not delete data in the [!DNL Commerce] application, as it may still be needed for merchant transactional needs. Merchants are responsible for any data deletion/access requests in the [!DNL Commerce] application. See [Shared responsibility security and operational model](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) to learn more.

[!DNL Commerce] will notify merchants about deletion requests by sending them information for data subjects requesting deletion of certain data.

## How to Create Access and Delete Requests

### Prerequisites

To make requests to access and delete data for Adobe [!DNL Commerce], you must have:

* an IMS Org ID
* an Identity identifier of the person you want to act on and the corresponding namespace(s).For more information about identity namespaces in Adobe [!DNL Commerce]and Experience Platform, see the [identity namespace overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces).

### Required field values in Adobe [!DNL Commerce] for API requests

```json
"companyContexts":
    "namespace": imsOrgID
    "value": <Your IMS Org ID Value>

"users":
    "action": either access or delete

    "userIDs":
        "namespace": e.g. email, aaid, ecid, etc.
        "type": standard
        "value": <Data Subject's Identity Identifier>

"include":
    ??? (which is the Adobe product code for Adobe [!DNL Commerce])
    profileService (product code for Profile)
    AdobeCloudPlatform (product code for AEP Data Lake)
    identity (product code for Identity)

"regulation":
    gdpr, ccpa, pdpa, lgpd_bra, or nzpa_nzl (which is the privacy regulation that applies to the request)
```

### GDPR Access Request example:

From the UI:

NEED SCREENSHOT ![](assets/accessrequest.png)

Through the API:
NEED JSON FROM KIRAN

```json
// JSON Request

```

```json
// JSON Response

```

### GDPR Delete Request example:

From the UI:

NEED SCREENSHOT ![](assets/deleterequest.png)

Through the API:
NEED JSON FROM KIRAN

```json
// JSON Request

```

```json
// JSON Response

```
