---
title: (v1.0) Delete timeRegistrationEntries
description: (v1.0) Deletes a timeRegistrationEntry object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Delete timeRegistrationEntries (v1.0)
Delete a timeRegistrationEntry from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/timeRegistrationEntries({timeregistrationId})
```

## Request headers (v1.0)

|Header         |Value                     |
|---------------|--------------------------|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **timeRegistrationEntries**, the **timeRegistrationEntries** will not be updated. |

## Request body (v1.0)

Do not supply a request body for this method.

## Response (v1.0)

If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v1.0/companies({id})/timeRegistrationEntries({timeregistrationId})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[Error Codes](../dynamics_error_codes.md)  
[timeRegistrationEntries](../resources/dynamics_timeRegistrationEntry.md)  
[Get timeRegistrationEntries](../api/dynamics_timeRegistrationEntry_get.md)  
[Post timeRegistrationEntries](../api/dynamics_timeRegistrationEntry_create.md)  
[Patch timeRegistrationEntries](../api/dynamics_timeRegistrationEntry_update.md)  
[Delete timeRegistrationEntries](../api/dynamics_timeRegistrationEntry_delete.md)  
