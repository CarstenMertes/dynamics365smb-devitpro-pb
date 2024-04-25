---
title: Application Access Management API
description: Learn about the Application Access Management API.
author: jswymer
ms.author: jswymer
ms.topic: conceptual

ms.custom: bap-template
ms.reviewer: jswymer
ms.search.keywords: application, tenant, management, access, API
ms.date: 08/24/2023
---
# Application Access Management API

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

As a **Delegated Global Administrator** or as a **Delegated Dynamics 365 Administrator**, you can manage access to application families available in the service. The application family is [!INCLUDE[prod_short](../developer/includes/prod_short.md)] or [!INCLUDE[embedapp](../developer/includes/embedapp.md)] applications that may be provisioned through the service. 

> [!NOTE]
> This API endpoint can only be used by delegated administrators. Guest users in the customer tenant can't use this API endpoint, even if they are also a delegated administrator. Service-to-service authentication using a Microsot Entra app authorized in the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] isn't supported.


You can get the list of applications that are available to the customer tenant. From this list you can determine, by setting the access property, for which applications an environment may be created on the tenant.

## Get List Of Manageable Applications

Returns a list of manageable applications by family and country code.

```
GET /admin/v2.15/manageableapplications
```

#### Response

Returns a wrapped array of applications.

```
{
  "value": [
    {
      "applicationFamily":  string, // The name of the family for a given Business Central offered application. (Typically this will just be "BusinessCentral") 
      "access":  boolean, // Indicates if the tenant has access to the application family/country code combination
      "countryCode": string, // The country code of the application.
    }
  ]
}
```
#### Example (PowerShell)

```
$url = "https://api.businesscentral.dynamics.com/admin/v2.3" 
$result = Invoke-WebRequest -Uri "$($url)/manageableapplications" -Headers @{"Authorization" = "Bearer $token"} | ConvertFrom-Json
Write-Host $($result.value | ConvertTo-Json)
```

## Control the access to Applications

Pass the application family name in the URL and a boolean in the body. 
- True - enables the access.
- False - disables the access.

```
Content-Type: application/json
PUT /admin/v2.15/manageableapplications/{applicationFamily}/countries/{countryCode}
```

#### Route Parameters

`applicationFamily` - The name of the family for a given Business Central offered application. (Typically this value will just be "BusinessCentral")

`countryCode` - Country code for the targeted application.

#### Body

```
{
  <boolean> // Desired access state
}
```

> [!NOTE]  
> It is not possible to disable the access to an application family for the Microsoft Entra tenant which already has an environment created in that family.

#### Expected Error Codes

`invalidInput` - the targeted property in invalid in some way

   - target: {targeted tenant's Id} - attempt to remove access to an application but the targeted tenant already has an environment in that application

`resourceDoesNotExist` - couldn't find the targeted application

#### Example (PowerShell)

```
$url = "https://api.businesscentral.dynamics.com/admin/v2.3" 
$country = 'DK'
$applicationFamily = 'frentals'
$access = "true"
Invoke-WebRequest -Uri "$($url)/manageableapplications/$($applicationFamily)/countries/$($country)"  -Headers @{"Authorization" = "Bearer $token"} -Body $access -Method Put -ContentType "application/json"
```

## See Also

[Application Access Management](../embedapps/embed-app-application-access-management.md)  
[Using Application Family](../deployment/embed-app-using-application-family.md)  
