---
title: GET salesShipmentLines  
description: Gets a salesShipmentLine object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

# Get salesShipmentLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a salesShipmentLine object for [!INCLUDE[prod_short](../../../includes/prod_short.md)]. 

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/salesShipments({id})/salesShipmentLines({salesShipmentLineId})
GET businesscentralPrefix/companies({id})/salesShipmentLines({salesShipmentLineId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Don't supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and an **salesShipmentLines** object in the response body.

## Example

**Request**

Here's an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/salesShipments({id})/salesShipmentLines({salesShipmentLineId})
```

**Response**

Here's an example of the response. 

```json
{
   "id": "238cb9c0-44e3-ea11-bb43-000d3a2feca1",
   "documentId": "9e0f5c9c-44e3-ea11-bb43-000d3a2feca1",
   "documentNo": "829482",
   "sequence": 10000,
   "lineType": "NAV.salesLineType",
   "lineObjectNumber": "1928-S",
   "description": "AMSTERDAM Lamp",
   "unitOfMeasureCode": "PCS",
   "unitPrice":  54.9,
   "quantity": 3,
   "discountPercent": 0,
   "taxPercent": 20,
   "shipmentDate": "2020-08-21"
}
```


## Related information
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[salesShipmentLine](../resources/dynamics_salesShipmentLine.md)  

