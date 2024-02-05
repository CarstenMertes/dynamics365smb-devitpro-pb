---
title: (v1.0) Create salesInvoiceLines
description: (v1.0) Creates a sales invoice line object in Dynamics 365 Business Central. 
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Create salesInvoiceLines (v1.0)
Create a sales invoice line object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request (v1.0)
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/salesInvoices({id})/salesInvoiceLines
```

## Request headers (v1.0)

|Header        |Value                      |
|--------------|---------------------------|
|Authorization |Bearer {token}. Required.  |
|Content-Type  |application/json           |

## Request body (v1.0)
In the request body, supply a JSON representation of a **salesInvoiceLines** object.
## Response (v1.0)
If successful, this method returns ```201 Created``` response code and a **salesInvoiceLines** object in the response body.

## Example (v1.0)

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v1.0/companies({id})/salesInvoices({id})/salesInvoiceLines
Content-type: application/json

{
"itemId": "id-value",
"lineType": "Item",
"quantity": 9
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Sales Invoice Line](../resources/dynamics_salesinvoiceline.md)  
[Get Sales Invoice Line](../api/dynamics_salesinvoiceline_get.md)  
[Update Sales Invoice Line](../api/dynamics_salesinvoiceline_update.md)  
[Delete Sales Invoice Line](../api/dynamics_salesinvoiceline_delete.md)  