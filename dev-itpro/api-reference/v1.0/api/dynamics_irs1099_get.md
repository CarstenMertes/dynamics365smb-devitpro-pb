---
title: (v1.0) Get irs1099Codes
description: (v1.0) Gets an IRS 1099 code object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Get irs1099Codes (v1.0)
Retrieve the properties and relationships of an IRS 1099 codes object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/irs1099Codes({id})
```

## Request headers (v1.0)

|Header       |Value                    |
|-------------|-------------------------|
|Authorization|Bearer {token}. Required.|

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and an **irs1099Codes** object in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/irs1099Codes({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
  "id": "id-value",
  "code": "R-10",
  "displayName": "State income tax withheld",
  "minimumReportable": 0,
  "lastModifiedDateTime": "0001-01-01T00:00:00Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  



[Error Codes](../dynamics_error_codes.md)  
[IRS 1099](../resources/dynamics_irs1099.md)  
[Post IRS 1099](../api/dynamics_create_irs1099.md)  
[Patch IRS 1099](../api/dynamics_irs1099_update.md)  
[Delete IRS 1099](../api/dynamics_irs1099_delete.md)  