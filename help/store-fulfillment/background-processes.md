---
title: Background process configuration
description: "Configure the schedules for [!DNL Store Fulfillment] background processes used in synchronizing data with the fulfillment services."                   
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
---

# Background process configuration

The Store Fulfillment integration uses background processes and message queues for optimal performance and scale. Build environments for your Adobe Commerce stores using [deployment variables](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) that automatically start [message queue runners](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Background processes are managed using the standard Adobe Commerce [Scheduled Tasks](https://docs.magento.com/user-guide/system/cron.html) functionality. These processes are responsible for synchronizing order and merchant store configuration data with store fulfillment web services. 

## Manage scheduled tasks for Store Fulfillment

From the Admin, go to **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Review the default configuration for Store Fulfillment services. Depending on your order processing volume and resource availability, you might need to adjust these settings.
