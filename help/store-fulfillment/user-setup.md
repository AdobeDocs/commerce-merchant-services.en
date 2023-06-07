---
title: User Setup
description: Setup enhanced Inventory Management sources as merchant stores to support the Store Fulfillment solution for Adobe Commerce.
role: User, Admin
level: Intermediate
exl-id: eb735bef-c339-4d0b-b3e7-10328915725b
---
# User Setup

Store Assist app Users are managed in Adobe Commerce. However, these users do not interact with Adobe Commerce directly. The user management is configured in Adobe Commerce to enable secure connections between Adobe Commerce and the app.

The Store Fulfillment App User model is separated from other Adobe Commerce user models. The app maintains its own permission model through user roles and users that can be assigned to all or specific locations. The following permissions are supported: Picking order, Dispensing Order, and Item qty reduction (and cancellation).

>[!TIP]
>
>For best results, [configure your connection](connect-set-up-service.md) before you add users and permissions for Store Associates who use the Store Assist app.

## Store Assist App - User Roles

During the initial user set up for the Store Assist app, create user roles to customize user permissions to the Store Assist app. For example, you can create different roles for store managers and store associates and assign different role resources to manage permissions for each type of user.

Configure User Roles from **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Role Info

| **Field**                  | **Description**         | **Scope** | **Required** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Enable or disable user. | Global    | Yes          |

### Role Resources

| **Field**                        | **Description**                                                                                                                                                                                                                            | **Scope** | **Required** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | List the available permission groups that can be assigned to a user role. At this time, the Store Fulfillment Solution does not have different permission levels defined for resource roles. All user roles have the same resource access. | Global    | Yes          |

## Store Assist - User Information

Manage Store Assist app user profiles from the Admin System settings:  **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Field**                                | **Description**                                                                                                                                                                                                                                                         | **Scope** | **Required** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]**               | Enable or disable user.                                                                                                                                                                                                                                                 | Global    | Yes          |
| **[!UICONTROL User Name]**               | User Name associated with user                                                                                                                                                                                                                                          | Global    | Yes          |
| **[!UICONTROL First Name]**              | First Name associated with user                                                                                                                                                                                                                                         | Global    | No           |
| **[!UICONTROL Last Name]**               | Last Name associated with user                                                                                                                                                                                                                                          | Global    | No           |
| **[!UICONTROL Role]**                    | Role associated with the user                                                                                                                                                                                                                                           | Global    | No           |
| **[!UICONTROL Access to all locations]** | Assign users access to all stores, or select stores individually.                                                                                                                                                                                                       | Global    | No           |
| **Interface Locale**                     | If your store has multiple languages, set Interface Locale to the language to be used for the Admin interface.                                                                                                                                                          | Global    | No           |
| **Active From**                          | To set a starting date, select the calendar icon.                                                                                                                                                                                                                       | Global    | No           |
| **Active To**                            | Set the Expiration Date by selecting the calendar icon. Setting an expiration date is useful to set up temporary user or role assignments. After the expiration date, the user account status changes to `Inactive`, but the account can still be updated if necessary. | Global    | No           |
