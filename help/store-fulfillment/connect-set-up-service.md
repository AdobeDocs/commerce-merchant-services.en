---
title: Connect the Store Fulfillment Solution
description: Establish the connections between Adobe Commerce and the Store Fulfillment solution by creating and authorizing an Adobe Commerce integration and adding the Store Fulfillment account credentials to the Adobe Commerce service configuration.
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
---
# Connect the Store Fulfillment Solution

Establish the connection between Adobe Commerce and Store Fulfillment services by configuring the required authentication credentials and connection data from the Admin.

- **[Configure [!DNL Commerce integration settings]](#create-the-commerce-integration)**–Create an Adobe Commerce integration for Store Fulfillment services and generate the access tokens to authenticate incoming requests from the Store Fulfillment servers.

- **[Configure account credentials for Store Fulfillment Services](#configure-store-fulfillment-account-credentials)**–Add your credentials to connect Adobe Commerce to your Store Fulfillment account.

>[!NOTE]
>
>Complete the connection configuration and validate the connection successfully before you begin testing.

## Create an Adobe Commerce integration

To integrate Adobe Commerce with Store Fulfillment services, you create a Commerce integration and generate access tokens that can be used to authenticate requests from Store Fulfillment servers.

1. From the Admin, create the Integration for Store Fulfillment.

   - Name the extension
   - Enter your email address
   - Enter your Admin account password

1. Configure [!UICONTROL API Resource Access permissions] for the integration—select `[!UICONTROL All]`

1. Generate the access tokens for authentication by saving and activating the integration. 

1. Copy and save the access tokens to a secure, encrypted location.

1. Work with your Account Manager to complete the configuration on the Store Fulfillment side and to authorize the integration.

1. Set Allow OAuth Access Tokens to be used as standalone Bearer tokens to Yes in Stores → Configuration → Services → OAuth → Consumer Settings. Leaving this to No will result in a 401 response: `The consumer isn't authorized to access %resources.`


>[!NOTE]
>
>For detailed instructions, see [Integrations](https://docs.magento.com/user-guide/system/integrations.html) in the _Adobe Commerce User Guide_.

>[!IMPORTANT]
>
> If restoring environments database with a different environments source data, E.g., production data to staging or vice versa, ensure to not overwrite the integration token details. This can be addressed by excluding the `oauth_token` table when creating your database export. 


## Configure Store Fulfillment account credentials

After you complete the intake form, a Walmart Store Fulfillment account is created for you. You will receive the following credentials when they are available:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (usually the same as above configuration)

These credentials are required to configure and use Store Fulfillment.

  >[!NOTE]
  >
  >The account creation process can take some time to complete. While you wait for credentials, [review amd configure other settings for the  Store Fulfillment solution](service-config-settings-overview.md).

### Add credentials to connect to Store Fulfillment

1. Configure [account credentials](enable-general.md) for the Production and Sandbox environments.

1. From the Admin, go to **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Enter the account credentials provided for the **[!UICONTROL Production environment]**. All fields are required.

1. Select **[!UICONTROL Save Config]**.

1. Test the connection by selecting **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>If the credentials are invalid, verify that you entered the correct values for each environment and revalidate. Contact your account representative if you still have problems connecting.
