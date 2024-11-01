---
title: Background Process Configuration
description: "Configure the schedules for [!DNL Store Fulfillment] background processes used in synchronizing data with the fulfillment services."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
---

# Background Process Configuration

The Store Fulfillment integration uses background processes and message queues for optimal performance and scale. Build environments for your Adobe Commerce stores using [deployment variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) that automatically start [message queue runners](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework).

Background processes are managed using the standard Adobe Commerce [Scheduled Tasks](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron) functionality. These processes are responsible for synchronizing order and merchant store configuration data with store fulfillment web services.

## Manage scheduled tasks for Store Fulfillment

From the Admin, go to **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Review the default configuration for Store Fulfillment services. You can customize these settings based on your order processing volume and resource availability.
