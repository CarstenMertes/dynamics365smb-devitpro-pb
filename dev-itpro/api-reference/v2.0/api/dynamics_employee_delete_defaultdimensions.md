---
title: Delete employee defaultDimensions  
description: Deletes the default dimensions of the employee in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete employee defaultDimensions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Deletes the default dimensions of the employee in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({companyId})/employees({employeeId})/defaultDimensions({employeeId},{dimensionId})
```

## Request headers

|Header         |Value                     |
|---------------|--------------------------|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **employees**, the **employees** will not be updated. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```204 No Content``` response code and it deletes the default dimensions for the employee and corresponding dimension.

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({companyId})/employees({employeeId})/defaultDimensions({employeeId},{dimensionId})
```

**Response** 

No Content.

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Employee](../resources/dynamics_employee.md)  
[Create employee defaultDimensions](dynamics_employee_create_defaultdimensions.md)  
[Update employee defaultDimensions](dynamics_employee_update_defaultdimensions.md)  
[Get employee defaultDimensions](dynamics_employee_get_defaultdimensions.md)  
