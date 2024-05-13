---
title: GET vendorPaymentJournals  
description: Gets a vendorPaymentJournal object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get vendorPaymentJournals

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a vendorPaymentJournal object for [!INCLUDE[prod_short](../../../includes/prod_short.md)]. 

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/vendorPaymentJournals({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and an **vendorPaymentJournals** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/vendorPaymentJournals({id})
```

**Response**

Here is an example of the response. 

```json
{
  "id": "dbe826d6-021d-ed11-9db9-000d3aa935da",
  "code": "CASH",
  "displayName": "Cash receipts and payments",
  "balancingAccountId": "00000000-0000-0000-0000-000000000000",
  "balancingAccountNumber": "10100",
  "lastModifiedDateTime": "2022-08-16T01:29:56.15Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[vendorPaymentJournal](../resources/dynamics_vendorPaymentJournal.md)  
[Delete vendorPaymentJournal](dynamics_vendorPaymentJournal_Delete.md)   
[Create vendorPaymentJournal](dynamics_vendorPaymentJournal_Create.md)   
[Update vendorPaymentJournal](dynamics_vendorPaymentJournal_Update.md)   

