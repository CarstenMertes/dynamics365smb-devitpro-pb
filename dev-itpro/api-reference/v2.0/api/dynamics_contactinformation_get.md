---
title: Get contactsInformation  
description: Gets a contact information object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

# Get contactInformation

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieves the properties and relationships of a contact information object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/vendors({id})/contactsInformation
GET businesscentralPrefix/companies({id})/customers({id})/contactsInformation
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/contactsInformation$filter=relatedId eq {bankAccountId} and relatedType eq 'Bank Account'
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/contactsInformation$filter=relatedId eq {employeeId} and relatedType eq 'Employee'
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **contactsInformation** object in the response body.

## Example

**Request**

Here's an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/customers({id})/contactsInformation
```

**Response**
Here's an example of the response.

```json
{
    {
        "contactId": "8f253caa-82de-ed11-884e-6045bdac97e2",
        "contactNumber": "CT000001",
        "contactName": "Adatum Corporation",
        "contactType": "Company",
        "relatedId": "8e253caa-82de-ed11-884e-6045bdac97e2",
        "relatedType": "Customer"
    },
    {
        "contactId": "91253caa-82de-ed11-884e-6045bdac97e2",
        "contactNumber": "CT000002",
        "contactName": "Robert Townes",
        "contactType": "Person",
        "relatedId": "8e253caa-82de-ed11-884e-6045bdac97e2",
        "relatedType": "Customer"
    }
}
```

## Remarks

This resource type requires [!INCLUDE[prod_short](../../../includes/prod_short.md)] version 18.0.

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[contactInformation](../resources/dynamics_contactInformation.md)  
