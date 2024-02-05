---
title: CREATE shipmentMethods  
description: Creates a shipmentMethod object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create shipmentMethods

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a shipment method object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/shipmentMethods
```
## Optional query parameters

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **shipmentMethod**, the **shipmentMethod** will not be updated. |


## Request body
In the request body, supply a JSON representation of a **shipmentMethods** object.

## Response
If successful, this method returns ```201 Created``` response code and a **shipmentMethods** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/shipmentMethods
Content-type: application/json

{
    "id": "87a5738a-44e3-ea11-bb43-000d3a2feca1",
    "code": "CFR",
    "displayName": "Cost and Freight",
    "lastModifiedDateTime": "2020-08-21T00:24:14.287Z"
}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "87a5738a-44e3-ea11-bb43-000d3a2feca1",
    "code": "CFR",
    "displayName": "Cost and Freight",
    "lastModifiedDateTime": "2020-08-21T00:24:14.287Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[shipmentmethod](../resources/dynamics_shipmentmethod.md)    
[Get shipmentmethod](dynamics_shipmentmethod_Get.md)    
[Delete shipmentmethod](dynamics_shipmentmethod_Delete.md)    
[Update shipmentmethod](dynamics_shipmentmethod_Update.md)    
