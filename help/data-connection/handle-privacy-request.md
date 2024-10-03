---
title: How Commerce Services Handles Privacy Requests
description: Learn how Commerce services handles requests to access and delete data.
role: Admin, Leader
feature: Security, Compliance
---
# How Commerce services handles privacy requests

The following outlines the data flow within Adobe's privacy management system. Here's a breakdown of the components and their interactions:

1. **Adobe Central Privacy**: This appears to be the central hub for managing privacy-related data and processes.

2. **Blob Storage**: Data is stored in a blob storage system, which is typically used for storing large amounts of unstructured data.

3. **Pipeline**: Data flows through a pipeline, which likely processes and transforms the data before it reaches the next stage.

4. **AEP Datalake**: The processed data is stored in the Adobe Experience Platform (AEP) Datalake, a centralized repository for large-scale data storage and analytics.

5. **UPS (Unified Profile Service)**: Data from the AEP Datalake is used to create and manage unified customer profiles.

6. **UIS (Unified Identity Service)**: This service manages identity data, ensuring that customer profiles are accurately linked and maintained.

7. **Adobe Commerce**: Data is integrated with Adobe Commerce, which likely uses this information for e-commerce activities.

8. **Backoffice Admin**: Administrative tasks and data management are handled by the backoffice admin.

9. **MongoDB**: Some data is stored in MongoDB, a NoSQL database known for its flexibility and scalability.

10. **Other Systems**: Data may also interact with other unspecified systems.

11. **Order Service (Party Parrots)**: This service handles order-related data, possibly for processing and fulfillment.

12. **Backoffice Collector (Lighthouse)**: This component collects data for backoffice operations.

13. **Data Files**: Finally, data files are generated and stored, possibly for reporting or archival purposes.

This flow ensures that data is collected, processed, stored, and utilized efficiently across various services and systems within Adobe's ecosystem.


FROM KIRAN:

For the commerce page, we can provide similar documentation to other service. I need to provide payloads. Got occupied with other priority today, Will send the payloads later today or tmrw.
For example: audience-manager,
Ref:
https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/overview/data-privacy/data-privacy-requests#access-data

Data Access Requests
You can send individual data access requests through the Privacy Service UI (documentation here or by calling the Privacy Service API (documentation here and API reference here.
The Privacy Service UI allows you to create new job requests either by using the Request Builder or by uploading a JSON file.
To see what a valid JSON file looks like, you can download a sample JSON.
We understand your commitment to honoring your data privacy requests within the time period set by the legislation.
Data Deletion Requests
You can send data deletion requests through the Privacy Service UI (documentation here or by calling the Privacy Service API (documentation here and API reference here.
The Privacy Service UI allows you to create new job requests either by using the Request Builder or by uploading a JSON file.
To see what a valid JSON file looks like, you can download a sample JSON.
Adobe understands your commitment to honoring your data privacy customer requests within 30 days. For that reason, Adobe is committed to processing your data deletion request as soon as possible.
In response to your consumer data deletion requests, Commerce deletes traits and segments associated with the Commerce identifier included in the request. Additionally, the respective Commerce identifiers for the individual opted out of further data collection by Commerce and the respective ID mappings will be removed.
When you send declared IDs, such as cross device CRM IDs or cookie IDs (We support standard namespace: EmailId only ), in data privacy requests, Commerce will perform the necessary deletion on all the linked devices (up to 100 devices per declared ID) Commerce Data owned by adobe and respective customer data owned by merchant needs to follow this documentation to delete data in merchant database.
Commerce will attempt to notify activation partners merchants about deletion requests by sending them  information for Data Subjects requesting deletion of certain data.
