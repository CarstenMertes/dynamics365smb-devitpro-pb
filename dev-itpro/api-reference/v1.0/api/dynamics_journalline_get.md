---
title: (v1.0) Get journalLines
description: (v1.0) Gets a journal line object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Get journalLines (v1.0)
Retrieve the properties and relationships of a journal line object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> Get journalLines will only return lines where documentType is not specified and where accountType is either of type `"G/L Account"` or `"Bank Account"`.

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/journals({id})/journalLines({id})
```

## Request headers (v1.0)

|Header       |Value                     |
|-------------|--------------------------|
|Authorization|Bearer {token}. Required. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and a **journalLines** object in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/journals({id})/journalLines({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
  "id": "id-value",
  "journalDisplayName": "DEFAULT",
  "lineNumber": 10000,
  "accountId": "id-value",
  "accountNumber": "10400",
  "postingDate": "2015-12-31",
  "documentNumber": "1234",
  "externalDocumentNumber": "",
  "amount": 1500,
  "description": "Accounts Receivable",
  "comment": "",
  "lastModifiedDateTime": "2017-03-17T19:02:22.043Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Journal Line](../resources/dynamics_journalline.md)  
[Create Journal Line](../api/dynamics_create_journalline.md)  
[Update Journal Line](../api/dynamics_journalline_update.md)  
[Delete Journal Line](../api/dynamics_journalline_delete.md)  