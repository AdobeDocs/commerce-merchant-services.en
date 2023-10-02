---
title: Integrate the Adobe Experience Platform Mobile SDK with Commerce
description: Learn how to use the Adobe Experience Platform Mobile SDK with your headless or custom Commerce storefront.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
---
# Integrate the Adobe Experience Platform Mobile SDK with Commerce

>[!IMPORTANT]
>
>The Adobe Experience Platform Mobile SDK for iOS supports iOS 11 or later.

Integrating the [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/) with the Commerce mobile app allows merchants to send Commerce  [event data](events.md) to the Experience Platform edge.

When Commerce event data is available at the edge, it can be accessed by other Adobe Experience Cloud applications. For example, you can use the data to build audiences in Real-Time CDP then [use those audiences](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) to personalize your Commerce mobile app.

## Configuration

To get started using the Adobe Experience Platform Mobile SDK with Commerce, install and configure the SDK in the Experience Platform. Then, finalize your configuration in Commerce.

### Experience Platform

1. Learn about mobile app capabilities by reviewing the [Adobe Experience Cloud in mobile apps tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Install and configure](https://developer.adobe.com/client-sdks/documentation/getting-started/) the SDK in Experience Platform.

    >[!NOTE]
    >
    >The schema you create and configure in the Experience Platform is the same schema you use in the application code in your Commerce mobile app. 

### Commerce

After you complete the SDK configuration for the Experience platform, add the SDK configuration to Commerce.

1. To send Commerce event data to the Experience Platform via the SDK, you must provide an XDM schema in the application code. This schema must match the schema [configured](https://developer.adobe.com/client-sdks/documentation/getting-started/set-up-schemas-and-datasets/) for the SDK in the Experience Platform.

    The following example shows how to track the `web.webpagedetails.pageViews` event and set the `identityMap` using the email field.

    ```swift
    let stateName = "luma: content: ios: us: en: home"
    var xdmData: [String: Any] = [
        "eventType": "web.webpagedetails.pageViews",
        "web": [
            "webPageDetails": [
                "pageViews": [
                    "value": 1
                ],
                "name": "Home page"
            ]
        ]
    ]

    let experienceEvent = ExperienceEvent(xdm: xdmData)
    Edge.sendEvent(experienceEvent: experienceEvent)
        
    // Adobe Experience Platform - Update Identity

    let emailLabel = "mobileuser@example.com"

    let identityMap: IdentityMap = IdentityMap()
    identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
    Identity.updateIdentities(with: identityMap)
    ```

1. Connect to the Commerce Cloud environment.

    In your project's build settings, add the URL to the Commerce GraphQL endpoint. Such as:

    - Debug: http://_debug_.commercesite.cloud/graphql/
    - Release: http://_release_.commercesite.cloud/graphql/
    
1. To retrieve data from the Commerce GraphQL endpoints, first generate the necessary files and directories in your project using the [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

    1. From your project directory, [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.
    
    1. [Initialize](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) the Apollo Codegen CLI.
    
        This creates an `apollo-codegen-configuration.json` file.
        
    1. Generate the necessary GraphQL files and directories in your project by replacing the contents of the `apollo-codegen-configuration.json` file with the following:

        ```json
        {
        "schemaName" : "MagentoAPI",
        "input" : {
            "operationSearchPaths" : [
            "**/*.graphql"
            ],
            "schemaSearchPaths" : [
            "**/*.graphqls"
            ]
        },
        "output" : {
            "testMocks" : {
            "none" : {
            }
            },
            "schemaTypes" : {
            "path" : "../MagentoAPI",
            "moduleType" : {
                "swiftPackageManager" : {
                }
            }
            },
            "operations" : {
            "inSchemaModule" : {
            }
            }
        },
        "schemaDownloadConfiguration": {
            "downloadMethod": {
                "introspection": {
                    "endpointURL": "http://magento24.com/graphql/",
                    "httpMethod": {
                        "POST": {}
                    },
                    "includeDeprecatedInputValues": false,
                    "outputFormat": "SDL"
                }
            },
            "downloadTimeout": 60,
            "headers": [],
            "outputPath": "magento.graphqls"
        }
        }
        ```
        
    1. [Fetch](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) the Commerce GraphQL schema.
    
        Ensure that the path is to the `./apollo-codegen-config.json` file, which contains the reference to the Commerce GraphQL schema.

    1. [Generate](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) the source code.
    
        Ensure that the path is to the `./apollo-codegen-config.json` file, which contains the configuration information to generate the necessary files and directories.

    1. Inside the newly created **GraphQLGenerated** folder, add or edit GraphQL types. For example, you can add a `DynamicBlocks.graphql` type with the following content:

        ```graphql
        query dynamicBlocks($input: DynamicBlocksFilterInput){
            dynamicBlocks(input: $input)
            {
                items {
                    content {
                        html
                    }
                }
            }
        }
        ```

    You have now integrated the Adobe Experience Platform Mobile SDK with your Commerce mobile app. Event data flows from your app to the Experience Platform edge.

To learn how to retrieve Real-Time CDP audiences from your mobile Commerce app to inform cart price rules and dynamic blocks, see [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html).
