---
title: Business Central Admin Center API - App Management
description: Learn about using the Business Central admin center API to manage apps.
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.reviewer: solsen
ms.search.keywords: administration, tenant, admin, environment, telemetry
ms.date: 02/24/2023
---

# App Management

[!INCLUDE[2020_releasewave1](../includes/2020_releasewave1.md)]

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

Manage the apps that are installed on the environment.

## Important Information before you get started

### <a name="eula"></a>End-User License Agreement and Terms of Use for Installing an App 

When you install an app from AppSource, you're shown a page for accepting the end-user license agreement, terms of use, and privacy policy. This isn't the case when you install an app using the API, because there's currently no user-interface with the feature. Instead, to install an app using the API, you must set the `"acceptIsvEula":` property in the request body, which is used for agreeing to the same terms as would when you install from AppSource. For more information, see [acceptIsvEula](#acceptisveula).

<!--
By setting this parameter to `true`, you accept the following terms:

> - I give Microsoft permission to use or share my account information so that the provider or Microsoft can contact me regarding this product and related products
>- Microsoft may share contact, usage, and transactional information for support, billing, and other transactional activities.
>- I agree to the provider's terms of use and privacy policy<sup>2</sup>.
>- I understand that the rights to use this product do not come from Microsoft, unless Microsoft is the provider. Use of AppSource is governed by separate [terms](https://azure.microsoft.com/support/legal/marketplace-terms/) and [privacy](https://privacy.microsoft.com/privacystatement).

<sup>2</sup> You should be able to find the terms of use and privacy policy from the app's download page on AppSource. Links to these documents are typically under **Details + Support** > **Legal**. Or, if can't find this information, contact the provider.

-->
### Required In-Product Permissions for Installing and Uninstalling Apps

To use the `install` and `uninstall` endpoints, you must have the following permission sets assigned to your Business Central user account or authorized Microsoft Entra app:

|Business Central version|Permission set|
|------------------------|---------------|
|version 18 and later|Exten. Mgt. - Admin|
|version 17 and earlier|"D365 EXTENSION MGT" or "Exten. Mgt. - Admin"|

> [!NOTE]
> These permissions sets are the same permission sets that allow you to use **Extension** Management page in tenant. Other  App management endpoints, like `update` or `availableupdates`, don't require these permission sets. 

## Install an App

**INTRODUCED IN:** API version 2.6

Installs an app on an environment.

```
Content-Type: application/json
POST /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/{appId}/install 
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

`appId` - ID of the targeted app.

### Body

```
{ 
  "targetVersion": "1.2.3.4", // Optional. If not provided, latest version will be installed. Required if "allowPreviewVersion": true 
  "useEnvironmentUpdateWindow": false/true, // If true, the operation will be executed only in the environment update window. It will appear as "scheduled" before it runs in the window. 
  "allowPreviewVersion": false/true, // If "allowPreviewVersion": true, targetVersion is required 
  "installOrUpdateNeededDependencies": false/true, // Value indicating whether any other app dependencies should be installed or updated; otherwise, information about missing app dependencies will be returned as error details 
  "acceptIsvEula": false/true, // Must be true for installation to proceed. Setting this to true means you agree to the terms described in the acceptIsvEula section that follows.
  "languageId": "en-US" // Optional. Specifies locale ID language code, for example, "en-US". This setting corresponds to what the user can set in Extension Management page in tenant.Full list of values can be found in /openspecs/office_standards/ms-oe376/6c085406-a698-4e12-9d4d-c3b0ee3dbc4a under BCP 47 Code column 
} 
```

#### acceptIsvEula

> [!IMPORTANT]
> By setting the `acceptIsvEula` property to `true`, you not only agree with ISV's end-user license terms (EULA) but also with these terms:
>
> **I give Microsoft permission to use or share my account information so that the provider or Microsoft can contact me regarding this product and related products and Microsoft may share contact, usage, and transactional information for support, billing, and other transactional activities. I agree to the provider's terms of use and privacy policy<sup>2</sup> and understand that the rights to use this product do not come from Microsoft, unless Microsoft is the provider. Use of AppSource is governed by separate [terms](https://azure.microsoft.com/support/legal/marketplace-terms/) and [privacy](https://privacy.microsoft.com/privacystatement).** 

<sup>2</sup> You should be able to find the terms of use and privacy policy from the app's download page on AppSource. Links to these documents are typically under **Details + Support** > **Legal**. Or, if you can't find this information, contact the provider.

### Response

Example `200 OK` response with body:

```
{ 
  "id": "35601559-224a-47d5-8089-86ac88b2b995", // ID of the operation used for tracking the update request 
  "type": "install", // Type of the operation, for this endpoint, it's "install" 
  "sourceAppVersion": "", // Current version of app on the tenant. In case of Install, it is always empty as no version is installed 
  "targetAppVersion": "1.2.3.4", // Version of app that will be installed. 
  "status": "scheduled", // An enum that indicates the status. Values include: "scheduled", "running", "succeeded", "failed", "canceled", "skipped" 
  "createdOn": "2021-03-22T15:44:57.9067589Z", // Date and time the request was created 
  "errorMessage": "" // Error message for failed operations 
} 
```

Example `400 Bad Request` response when dependent apps need to be installed first:

```
{ 
  "code": "EntityValidationFailed", // Error code 
  "message": "Error details", // Detailed error message 
  "data": { // Any additional data for the error. For example, when "installOrUpdateNeededDependencies" in the request body was set to false, and there are dependencies that must be first installed or updated. 
    "requirements": [ // List of requirements you need to fulfil before you can run the request 
      { 
        "appId": "1ed76016-b288-401c-92e1-75b2d47ff223", 
        "name": "Contoso App", 
        "publisher": "Contoso", 
        "version": "16.0.32.0", 
        "type": "install" // enum | "install", "update", "uninstall") 
      } 
    ] 
  } 
} 
```

## Uninstall an App

**INTRODUCED IN:** API version 2.6

Uninstalls an app from an environment.

```
Content-Type: application/json
POST /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/{appId}/uninstall  
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

`appId` - ID of the targeted app.

### Body

```
{ 
  "useEnvironmentUpdateWindow": false/true, // If set to true, the operation will be executed only in the environment update window. It will appear as "scheduled" before it runs in the window. 
  "uninstallDependents": false/true // Value indicating whether any other dependent apps should be uninstalled, otherwise information about dependent apps will be returned in error details 
  "deleteData": false/true // Deletes data and syncs clean the extension. Exactly the same as deleting data in Extension Management page in tenant. 
} 
```

### Response

Example `200 OK` response with body:

```
{
  "id": "35601559-224a-47d5-8089-86ac88b2b995", // ID of the operation used for tracking the update request 
  "type": "uninstall", // Type of the operation. For this endpoint, it's "uninstall".
  "sourceAppVersion": "1.2.3.4", // Current version of app on the tenant. 
  "targetAppVersion": "", // Target version of the app on the tenant. For uninstall, it will be always empty. 
  "status": "scheduled", // An enum that indicates the status. Values include: "scheduled", "running", "succeeded", "failed", "canceled", "skipped"  
  "createdOn": "2021-03-22T15:44:57.9067589Z", // Date and time the request was created 
  "errorMessage": ""  // Error message for failed operations 
} 
```

Example `400 Bad Request` response when dependent apps need to be uninstalled first: 

```
{ 
  "code": "EntityValidationFailed", // Error Code 
  "message": "Error details", // Detailed error message 
  "data": { // Any additional data for the error. For example, when "uninstallDependents" in the request body was set to false, and there are existing dependent apps that need to be uninstalled first. The list of requirements is all apps that depend on app 35601559-224a-47d5-8089-86ac88b2b995. 
    "requirements": [ // List of requirements you need to fulfil before you can run the request 
      { 
        "appId": "1ed76016-b288-401c-92e1-75b2d47ff223", 
        "name": "Contoso App", 
        "publisher": "Contoso", 
        "version": "16.0.32.0", 
        "type": "uninstall" // (enum | "install", "update", "uninstall") 
      } 
    ] 
  } 
}
```

## Get Installed Apps 

Get information about apps that are installed on the environment.

```
GET /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

### Response
Returns information about the apps installed on the environment.

```
{
  "value":
  [
    { 
      "id": Guid, // Id of the installed app 
      "name": string, // Name of the installed app 
      "publisher": string, // Publisher of the installed app 
      "version": string, // Version of the installed app
      "state": string, // (enum | "Installed", "UpdatePending", "Updating")
      "lastOperationId": Guid, // Id of the last update operation that was performed for this app
      "lastUpdateAttemptResult": string // (enum | "Failed", "Succeeded", "Canceled", "Skipped")
    }
  ]
}
```

## Get Available App Updates 

Get information about new app versions that are available for apps currently installed on the environment.

```
GET /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/availableUpdates
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

### Response

```
{
  "value":
  [ 
    { 
      "id": Guid, // Id of the app 
      "name": string, // Name of the app 
      "publisher": string, // Publisher of the app 
      "version": string, // New version available of the app
      "requirements": // List of other apps that need to be installed or updated before this app can be updated
      [
        { 
          "id": Guid, // Id of the app
          "name": string, // Name of the app 
          "publisher": string, // Publisher of the app 
          "version": string, // Version the required app needs to be updated to or installed
          "type": string // (enum | "Install", "Update") 
        }
      ] 
    }
  ] 
}
```

## Update an App

Updates an app using an existing endpoint, but when new parameters in the request body are available.

```
Content-Type: application/json
POST /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/{appId}/update
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

`appId` - ID of the targeted app.

### Body

```
{ 
  "useEnvironmentUpdateWindow": false/true, // If set to true, the operation will be executed only in the environment update window. It will appear as "scheduled" before it runs in the window.
  "targetVersion": "1.2.3.4", // Always required. There's no option to update to the latest. You have to first do a "availableAppUpdates", call then use the version here.
  "allowPreviewVersion": false/true,  
  "installOrUpdateNeededDependencies": false/true, // Value indicating whether any other app dependencies should be installed or updated; otherwise, information about missing app dependencies will be returned as error details
}
```

### Responses (app operation) 

200 OK, with Body, example:

```
{ 
  "id": "35601559-224a-47d5-8089-86ac88b2b995", // ID of the operation used for tracking the update request
  "type": "update", // Type of the operation. For this endpoint, it's "update".
  "sourceAppVersion": "1.2.3.0", // Current version of app on the tenant.
  "targetAppVersion": "1.2.3.4", // Target version of the app on the tenant that will be installed during update.
  "status": "scheduled", // An enum that indicates the status. Values include: "scheduled", "running", "succeeded", "failed", "canceled", "skipped"
  "createdOn": "2021-03-22T15:44:57.9067589Z", // Date and time the request was created
  "errorMessage": "", // Error message for failed operations
  "createdBy": "", // Email address if authenticated as user, App ID if authenticated as app
  "canceledBy: "" // Empty value
}
```
  
Example `400 Bad Request` response when dependent apps need to be updated first:

```
{ 
  "code": "EntityValidationFailed", // Error Code 
  "message": "Error details", // Detailed error message 
  "data": { // Any additional data for the error. For example, when when "installOrUpdateNeededDependencies" in the request body was set to false, and dependencies need to be installed or updated.  
    "requirements": [ // List of requirements you need to fulfil before you can run the request 
      { 
        "appId": "1ed76016-b288-401c-92e1-75b2d47ff223", 
        "name": "Contoso App", 
        "publisher": "Contoso", 
        "version": "16.0.32.0", 
        "type": "install" // (enum | "install", "update", "uninstall") 
      }
    ]
  }
}
```

## Cancel a scheduled app update

Cancels an app update in scheduled state.

```
Content-Type: application/json
POST /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/{appId}/update/cancel
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

`appId` - ID of the targeted app.

### Body

```
{ 
  "ScheduledOperationId": guid // Obtained when scheduling an update or by getting app operations for the environment
}
```

### Responses (app operation) 

200 OK, with Body, example:

```
{ 
  "id": "35601559-224a-47d5-8089-86ac88b2b995", // ID of the operation used for tracking the update request
  "type": "update", // Type of the operation. For this endpoint, it's "update".
  "sourceAppVersion": "1.2.3.0", // Current version of app on the tenant.
  "targetAppVersion": "1.2.3.4", // Target version of the app on the tenant that will be installed during update.
  "status": "canceled", // An enum that indicates the status. Values include: "scheduled", "running", "succeeded", "failed", "canceled", "skipped"
  "createdOn": "2021-03-22T15:44:57.9067589Z", // Date and time the request was created
  "errorMessage": "", // Error message for failed operations
  "createdBy": "", // Email address if authenticated as user, App ID if authenticated as app
  "canceledBy: "" // Email address if authenticated as user, App ID if authenticated as app
}
```

## Get App Operations

Gets information about app install, uninstall, and update operations for the specified app.

```
GET /admin/v2.19/applications/{applicationFamily}/environments/{environmentName}/apps/{appId}/operations/[{operationId}]
```

### Route Parameters

`applicationFamily` - Family of the environment's application (for example, "BusinessCentral")

`environmentName` - Name of the targeted environment.

`appId` - Id of the targeted app.

`operationId` - Id of the app update operation. Used for getting information about a specific operation.

### Response

Returns the list of app update operations for the specified app.
*Note*: `operationId` is provided, the single operation is returned instead.

```
{
  "value":
  [
    {
      "id": Guid,  // Id of the operation
      "createdOn": string, // Date and time the request was created
      "startedOn": string, // Date and time the installation process started
      "completedOn": string, // Date and time the installation process completed
      "status": string, // (enum | "Scheduled", "Running", "Succeeded", "Failed", "Canceled", "Skipped")
      "sourceVersion": string, // Version of the app that was installed before the installation process started
      "targetVersion": string, // Version the installed app will be updated to
      "type": string, // The type of app operation
      "errorMessage": string // The error message provided when update installation fails
    }
  ]
}
```

## Create alerts using Azure Logic Apps and Power Automate

[Azure Logic Apps](/azure/logic-apps/logic-apps-overview) and [Power Automate](https://powerautomate.microsoft.com) have built-in connectors that can be used to query the admin center API by using HTTP and service-to-service (S2S) authentication. Use this capability to set up custom notifications or to automate certain actions.

> [!NOTE]
> Samples of custom notifications and automations are shared by Microsoft and third parties in the [Business Central BCTech repository on GitHub](https://github.com/microsoft/BCTech/tree/master/samples/AppInsights/Alerts). You can also share your Application Insights alerts and automations with the community on GitHub.

The sample below can help getting started with alerting in Microsoft Teams when app updates are available for an environment. When updates are available, an adaptive card will be created in a Teams channel, which allows for the automation of app updates by using S2S authentication that targets the admin center API.

### Example - Run a recurrent alerting API query that sends a Teams notification when app updates are available

This Logic App runs a specified number of times a day (parameter in deployment pipeline) and lists all app updates made available for selected environment (parameter in deployment pipeline).

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FBCTech%2Fmaster%2Fsamples%2FAppInsights%2FAlerts%2FAlertingLogicAppTemplates%2FS2SAppsEnvironmentAppUpdateAdaptiveCard.json)

### Prerequisites

Business Central admin center API is configured for S2S authentication of Microsoft Entra apps. For more information, go to [Authenticate using service-to-service AAD Apps](administration-center-api.md#authenticate-using-service-to-service-microsoft-entra-apps-client-credentials-flow).

### Preparation

You'll need the following information about Business Central and your Teams service to deploy the Logic App:

|Service|Information|
|-|-|
|Business Central|<ul><li>The Microsoft Entra tenant ID for Business Central</li><li>The application (client) ID of the registered application in Azure used for S2S authentication</li><li>The client secret of the registered application in Azure used for S2S authentication</li></ul>|
|Teams|<ul><li>The group ID of the team in Teams that you want to send the alerts to</li><li>The ID of the channel in Teams that you want to send the alerts to</li></ul> |

> [!IMPORTANT]
> Deploying a Logic App to Azure also creates the API connection resources necessary to authenticate certain actions in the Logic Apps. In this example, the deployment will create a connection resource for the Teams API.
>
> If you already have an API connection resource for Teams in your resource group, you can reuse the existing connection resource by providing its name during deployment.

### Deploy the Logic App

1. Select the **Deploy to Azure** button above and sign in to Azure portal when prompted.

2. Fill in the required fields on the **Custom deployment** page.

   In the **Teams Connection Name** field, specify a name for the new connection resource to be added for the Teams API. If you want to reuse the existing connection resource for the Teams API, entering the name of the existing connection resource.

3. Select **Review + create** to complete the deployment.

4. When deployment is done, authorize the connection to Teams API using your Teams credentials:

    1. Select **Go to resource group**.
    2. Select the resource for the Teams API connection to open it.
    3. Select **Edit API connection** > **Authorize**, then sign in with your credentials.

## See Also

[The Business Central Administration Center API](administration-center-api.md)  
[Manage Apps](tenant-admin-center-manage-apps.md)  
[Microsoft Dynamics 365 Business Central Server Administration Tool](administration-tool.md)  
