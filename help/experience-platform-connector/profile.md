---
title: Upload Shopper Profiles to Adobe Experience Platform
description: Learn how to upload shopper profiles to Adobe Experience Platform.
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
---
# Upload shopper profile to Adobe Experience Platform

Adobe Commerce merchants can upload customer profile data to [Real-Time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), which is part of Adobe Experience Platform. Profile allows you to consolidate your customer data into a unified view, offering an actionable and timestamped account of every customer interaction.

>[!NOTE]
>
> Profile data must include an email address, as that is how the link between a shopper and their storefront behavioral data is created.

After you upload your shopper's profiles, event data associated with any interactions your shoppers take on your site is sent to Profile through the Experience Platform connector and linked to that shopper's profile.

>[!NOTE]
>
> The `createAccount` [storefront event](events.md) does not automatically create a customer profile in Profile. This is restricted for security reasons and is intentional.

In this topic you will learn how to upload your Adobe Commerce customer profiles to Real-time Customer Profile in Experience Platform.

1. Determine where you store your customer data. For some merchants, this data is stored in Adobe Commerce and can be [exported](https://docs.magento.com/user-guide/system/data-export.html) as a CSV file. For others, it might be in a separate Customer relationship management (CRM) system.

1. After you determine where you store your customer data, find the appropriate [source connector](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) based on where your customer data is stored. If you do not see an appropriate source connector, then use the [local file upload](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) connector and import your shopper profiles from a CSV file.

    >[!NOTE]
    >
    > If you use the local file upload connector, you must enable the **Profile dataset** option when [defining the dataset](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). This identifies the dataset as being profile data.

After you create the shopper profiles in Profile, all storefront data associated with that shopper will be linked to their profile. 

## Upload profiles frequently

To ensure an enhanced shopper experience, you should import profile data periodically. Some source connectors allow you import profile data on a schedule.
