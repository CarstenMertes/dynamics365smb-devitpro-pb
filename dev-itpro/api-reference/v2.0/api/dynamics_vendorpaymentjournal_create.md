---
title: CREATE vendorPaymentJournals  
description: Creates a vendorPaymentJournal object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create vendorPaymentJournals

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a vendorPaymentJournal object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/vendorPaymentJournals
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **vendorPaymentJournal**, the **vendorPaymentJournal** will not be updated. |

## Request body
In the request body, supply a JSON representation of **vendorPaymentJournals** object.

## Response
If successful, this method returns ```201 Created``` response code and a **vendorPaymentJournals** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/vendorPaymentJournals
Content-type: application/json

{
  "code": "OTTER",
  "displayName": "Otter cash receipts and payments",
  "balancingAccountId": "021c2ed0-021d-ed11-9db9-000d3aa935da"
}
```

**Response**

Here is an example of the response. 

```json
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "1377cc08-eb23-ed11-88e7-f2834877f72d",
  "code": "OTTER",
  "displayName": "Otter cash receipts and payments",
  "balancingAccountId": "021c2ed0-021d-ed11-9db9-000d3aa935da",
  "balancingAccountNumber": "10700",
  "lastModifiedDateTime": "2022-08-24T20:26:30.03Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)     
[vendorPaymentJournal](../resources/dynamics_vendorPaymentJournal.md)  
[Get vendorPaymentJournal](dynamics_vendorPaymentJournal_Get.md)   
[Delete vendorPaymentJournal](dynamics_vendorPaymentJournal_Delete.md)   
[Update vendorPaymentJournal](dynamics_vendorPaymentJournal_Update.md)   
