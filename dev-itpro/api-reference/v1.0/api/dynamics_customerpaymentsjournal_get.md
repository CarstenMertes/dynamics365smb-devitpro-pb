---
title: (v1.0) Get customerPaymentsJournals
description: (v1.0) Gets a customer payment journal in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Get customerPaymentsJournals (v1.0)
Retrieve the properties and relationships of a customer payment journal object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/customerPaymentJournals({id})
```

## Request headers (v1.0)

|Header       |Value                     |
|-------------|--------------------------|
|Authorization|Bearer {token}. Required. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and a **customerPaymentJournals** object in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/customerPaymentJournals({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
  "id": "id-value",
  "code": "DEFAULT",
  "displayName": "Default Journal Batch",
  "lastModifiedDateTime": "2017-05-17T11:30:01.313Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[Microsoft Graph Reference](../api/dynamics_graph_reference.md)  
[Error Codes](../dynamics_error_codes.md)  
[Customer Payments Journal](../resources/dynamics_customerpaymentsjournal.md)  
[Get Customer Payments Journal](dynamics_customerpaymentsjournal_get.md)  
[Patch Customer Payments Journal](dynamics_customerpaymentsjournal_update.md)  
[Delete Customer Payments Journal](dynamics_customerpaymentsjournal_delete.md)  
