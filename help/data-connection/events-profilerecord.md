---
title: Profile Records
description: Learn what data a profile record captures.
role: Admin, Developer
feature: Personalization, Integration, Eventing
---
# [!DNL Data Connection] Profile Records

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
|`userAccount`| Indicates any loyalty details, preferences, login processes, and other account preferences.|
|`userAccount.startDate`| The date the profile was first created.|

>[!NOTE]
>
>Each profile record also includes the [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) field, which includes the shopper's email address, when available, and ECID.

Learn how to [create a profile record-specific schema](profile-data.md) that can ingest the data from your profile records.
