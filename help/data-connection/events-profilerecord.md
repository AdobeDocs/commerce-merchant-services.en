---
title: Profile Records
description: Learn what data a profile record captures.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
---
# [!DNL Data Connection] Profile Records (Beta)

The following describes the Commerce profile record data that is available when you install the [!DNL Data Connection] extension. The data in profile records is sent to the Adobe Experience Platform.

## Profile record

Profile record updates are available in the Experience Platform when a new profile is created, updated, or deleted.

### Data collected from profile record

The following describes the data that is captured for a profile record.

|Field|Description|
|---|---|
|`channel`|Contains information about the source of the data. Both `_id` and `_type` contain [namespaced values](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html).|
|`channel._id`|The unique identifier of the channel, such as `"https://ns.adobe.com/xdm/channels/web"`.|
|`channel._type`|Identifies the source of the channel data, such as `"https://ns.adobe.com/xdm/channel-types/web"`.|
|`person`|Contains information about the customer.|
|`person.name`|Contains information about the name of the customer.|
|`person.name.firstName`|Contains the first name of the customer.|
|`person.name.lastName`|Contains the last name of the customer.|
|`person.birthDate`| Date of birth of the shopper.|
|`personalEmail`|A personal email address.|
|`personalEmail.address`|The technical address, for example, `name@domain.com` as commonly defined in RFC2822 and subsequent standards.|
|`billingAddress`|The billing postal address.|
|`billingAddress.street1`|Primary street level information, apartment number, street number, and street name.|
|`billingAddress.street2`|Optional street information second line.|
|`billingAddress.city`|The name of the city.|
|`billingAddress.state`|The name of the state. This is a free-form field.|
|`billingAddress.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`billingAddress.primary`|Indicates if this is the primary billing address. Value is always `False`.|
|`billingAddressPhone`|The phone number associated with the billing address.|
|`billingAddressPhone.number`|The phone number. Note the phone number is a string and may include meaningful characters such as brackets `()`, hyphens `-`, or characters to indicate sub-dialing identifiers like extensions `x` for example,  `1-353(0)18391111` or `+613 9403600x1234`.|
|`billingAddressPhone.primary`|Indicates if this is the primary phone number for the billing address. Value is always `False`.|
|`shippingAddress`|The shipping postal address.|
|`shippingAddress.street1`|Primary street level information, apartment number, street number, and street name.|
|`shippingAddress.street2`|Optional street information second line.|
|`shippingAddress.city`|The name of the city.|
|`shippingAddress.state`|The name of the state. This is a free-form field.|
|`shippingAddress.country`|The name of the government-administered territory. Other than `xdm:countryCode`, this is a free-form field that can have the country name in any language.|
|`shippingAddress.primary`|Indicates if this is the primary shipping address. Value is always `False`.|
|`shippingAddressPhone`|Phone number associated with the shipping address.|
|`shippingAddressPhone.number`|The phone number. Note the phone number is a string and may include meaningful characters such as brackets `()`, hyphens `-`, or characters to indicate sub-dialing identifiers like extensions `x` for example,  `1-353(0)18391111` or `+613 9403600x1234`.|
|`shippingAddressPhone.primary`|Indicates if this is the primary phone number for the shipping address. Value is always `False`.|
|`userAccount`| Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.startDate`| The date the profile was first created.|

>[!NOTE]
>
>Each profile record also includes the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which includes the system generated Commerce Customer ID as the primary identifier for the profile and an email ID that is used as a secondary identifier.

Learn how to [create a profile record-specific schema](profile-data.md) that can ingest the data from your profile records.
