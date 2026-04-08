---
title: Get externalBusinessEventDefinitions
description: Retrieve the properties of external business event definition objects in Dynamics 365 Business Central using the GET method.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Get externalBusinessEventDefinitions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of an external business event definition object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/externalBusinessEventDefinitions
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and an **externalBusinessEventDefinitions** object in the response body.

**Request**

Here's an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/externalBusinessEventDefinitions
```

**Response**

Here's an example of the response.

> [!NOTE]
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "appId": "00000000-0000-0000-0000-000000000000",
    "name": "SalesOrderPosted",
    "eventVersion": "1.0",
    "payload": "string",
    "displayName": "Sales order posted",
    "description": "Triggered when a sales order is posted.",
    "category": "Sales",
    "appName": "Base Application",
    "appPublisher": "Microsoft",
    "appVersion": "25.0.0.0"
}
```

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[externalBusinessEventDefinitions](../resources/dynamics_externalbusinesseventdefinitions.md)
