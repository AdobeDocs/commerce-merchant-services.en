---
title: 'How [!DNL Commerce] Services Handles Privacy Requests'
description: Learn how [!DNL Commerce] services handles requests to access and delete data.
role: Admin, Leader
feature: Security, Compliance
---
# Privacy requests

Adobe Experience Platform Privacy Service provides a RESTful API and user interface to help you manage customer data requests. With Privacy Service, you can submit requests to access and delete personal customer data from Adobe Experience Cloud applications, facilitating automated compliance with legal and organizational privacy regulations.

For more information on Privacy Service and how to create and manage privacy requests, see Adobe Experience Platform documentation:

* [Privacy Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
* [Managing privacy jobs in Privacy Service UI](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide)

## Managing individual data privacy requests

You can submit individual requests to access and delete consumer data from [!DNL Commerce] in two ways:

* Through the **Privacy Service UI**. See the documentation [here](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide#_blank).
* Through the **Privacy Service API**. See the documentation [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/#_blank) and API information [here](https://developer.adobe.com/experience-platform-apis/#_blank).

Privacy Service supports two types of requests: **data access** and **data deletion**.

>[!NOTE]
>
>This article only covers how to make privacy requests for [!DNL Commerce]. If you also plan to make privacy requests for the Platform data lake, refer to this [guide](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/privacy) in addition to this article. For Real-Time Customer Profile, please refer to this [guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/privacy) and for Identity Service, please refer to this [guide](https://experienceleague.adobe.com/en/docs/experience-platform/identity/privacy). For delete and access requests, you need to call these individual systems to make sure the requests are handled by each of them. Making a privacy request to [!DNL Commerce] will not remove data from all these systems.

## Data access

For **access requests**, specify "Commerce Data for Marketing" from the UI (or `commerceMarketingData` as a product code in the API).

## Data deletion

For deletion requests, Privacy Service deletes [!DNL Commerce] data stored in Commerce SaaS services for marketing purposes, meaning profiles and orders of data subjects are no longer sent to Adobe marketing applications for use in campaigns and customer journeys. However, Privacy Service does not delete data in the [!DNL Commerce] application, as it may still be needed for merchant transactional needs. Merchants are responsible for any data deletion/access requests in the [!DNL Commerce] application. See [Shared responsibility security and operational model](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) to learn more.

[!DNL Commerce] will notify merchants about deletion requests by sending them information for data subjects requesting deletion of certain data.

## How to Create Access and Delete Requests

### Prerequisites

To make requests to access and delete data for Adobe [!DNL Commerce], you must have:

* an IMS Org ID
* an Identity identifier of the person you want to act on and the corresponding namespace(s). For more information about identity namespaces in Adobe [!DNL Commerce] and Experience Platform, see the [identity namespace overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces).

### GDPR Request/delete access example:

For **access requests**, specify "Commerce Data for Marketing" from the UI (or "commerceMarketingData" as a product code in the API).

For **delete requests**, make sure that the "Commerce Data for Marketing" checkbox is enabled. Additionally, if customer profile and order data has already been sent from [!DNL Commerce] to Adobe Experience Platform, you need to submit delete requests to three downstream services.

The three downstream services are:

* Profile (product code: "profileService")
* AEP Data Lake (product code: "AdobeCloudPlatform")
* Identity (product code: "identity")

To send access and delete requests through the Privacy API, you must authenticate and manage permissions for Privacy Service:

* [Authenticate and access the Privacy Service API](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/api/getting-started)
* [Manage permissions for Privacy Service](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/permissions)

**Required headers**

```bash
curl --location --request POST 'https://platform.adobe.io/data/core/privacy/jobs' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{CLIENT_ID}}' \
--header 'x-gw-ims-org-id: {{IMS_ORGID}}' \
--header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
```

**Request**

```json
{
    "companyContexts": [
      {
        "namespace": "imsOrgID",
        "value": "{{IMS_ORGID}}"
      }
    ],
    "users": [
      {
        "key": "sampleUserKey1",
        "action": ["access"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "dsmith@sample.com",
            "type": "standard"
          }
        ]
      },
      {
        "key": "sampleUserKey2",
        "action": ["access","delete"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "ajones@sample.com",
            "type": "standard"
          }
        ]
      }
    ],
    "include": ["commerceMarketingData"],
    "expandIds": false,
    "priority": "normal",
    "regulation": "gdpr"
}

```

**Response**

```json
{
    "requestId": "17284033173196154RX-223",
    "totalRecords": 3,
    "jobs": [
        {
            "jobId": "a52ca032-858e-11ef-bbb4-27391388a0a6",
            "customer": {
                "user": {
                    "key": "sampleUserKey1",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "dsmith@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca034-858e-11ef-bbb4-d5d952d69769",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "delete"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca033-858e-11ef-bbb4-8361a5022341",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        }
    ]
}

```
