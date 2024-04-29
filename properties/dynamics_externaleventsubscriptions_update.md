---
title: Update externaleventsubscriptions
description: Updates an  externaleventsubscriptions object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 02/06/2023
ms.author: solsen
---

# Update externaleventsubscriptions

Updates the properties of an external event subscription object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/externaleventsubscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **externaleventsubscriptions**, the **externaleventsubscriptions** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **externaleventsubscriptions** object in the response body.

## Example

**Request**

Here is an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different. Fill in the property values) -->
```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/externaleventsubscriptions({id})
Content-type: application/json
{
    "id" : ,
    "timestamp" :
}
```
<!-- END>EDIT_IS_REQUIRED -->
**Response**

Here is an example of the response.

<!-- START>EDIT_IS_REQUIRED. Fill in values for properties -->
```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id" : ,
    "timestamp" : ,
    "appId" : ,
    "eventName" : ,
    "companyName" : ,
    "userId" : ,
    "notificationUrl" : ,
    "lastModifiedDateTime" : ,
    "clientState" : ,
    "subscriptionType" : ,
    "systemCreatedAt" : ,
    "systemCreatedBy" : ,
    "systemModifiedAt" : ,
    "systemModifiedBy" :
}
```
## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[External event subscriptions](../resources/dynamics_externaleventsubscriptions.md)  
[GET external event subscriptions](dynamics_externaleventsubscriptions_get.md)  
[DELETE external event subscriptions](dynamics_externaleventsubscriptions_delete.md)  
[POST external event subscriptions](dynamics_externaleventsubscriptions_create.md)  
