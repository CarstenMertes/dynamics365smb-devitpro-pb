---
title: UPDATE vendorPaymentJournals   
description: Updates a vendorPaymentJournal object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Update vendorPaymentJournals

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of a vendorPaymentJournal object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
PATCH businesscentralPrefix/companies({id})/vendorPaymentJournals({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization |Bearer {token}. Required.|
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **vendorPaymentJournal**, the **vendorPaymentJournal** will not be updated. |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response
If successful, this method returns a ```200 OK``` response code and an updated **vendorPaymentJournals** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/vendorPaymentJournals({id})
Content-type: application/json

{
  "code": "COMMON",
  "displayName": "COMMON"
}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "1377cc08-eb23-ed11-88e7-f2834877f72d",
  "code": "COMMON",
  "displayName": "COMMON",
  "balancingAccountId": "021c2ed0-021d-ed11-9db9-000d3aa935da",
  "balancingAccountNumber": "10700",
  "lastModifiedDateTime": "2022-08-24T20:37:54.867Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)   
[vendorPaymentJournal](../resources/dynamics_vendorPaymentJournal.md)  
[Get vendorPaymentJournal](dynamics_vendorPaymentJournal_Get.md)   
[Delete vendorPaymentJournal](dynamics_vendorPaymentJournal_Delete.md)   
[Create vendorPaymentJournal](dynamics_vendorPaymentJournal_Create.md)   
