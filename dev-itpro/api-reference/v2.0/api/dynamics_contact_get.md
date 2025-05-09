---
title: Get contacts  
description: Gets a contact object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

# Get contacts

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieves the properties and relationships of a contact object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/contacts({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **contact** object in the response body.

## Example

**Request**

Here's an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/contacts({id})
```

**Response**
Here's an example of the response.


```json
{
    "id" : "5d115c9c-44e3-ea11-bb43-000d3a2feca1",
    "number" : "108001",
    "type" : "Company",
    "displayName": "CRONUS USA, Inc.",
    "companyNumber" : "17806",
    "companyName" : "CRONUS US",
    "businessRelation" : "Vendor",
    "addressLine1": "7122 South Ashford Street",
    "addressLine2": "Westminster",
    "city": "Atlanta",
    "state": "GA",
    "country": "US",
    "postalCode": "31772",
    "phoneNumber": "+1 425 555 0100",
    "mobilePhoneNumber" : "",
    "email" : "ah@contoso.com",
    "website" : "",
    "searchName" : "",
    "privacyBlocked" : true,
    "lastInteractionDate" : "2021-06-01",
    "lastModifiedDateTime" : "2021-06-01"
}
```

## Remarks

This resource type requires [!INCLUDE[prod_short](../../../includes/prod_short.md)] version 18.0.

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[contact](../resources/dynamics_contact.md)  
[DELETE contact](dynamics_contact_delete.md)  
[POST contact](dynamics_contact_create.md)  
[PATCH contact](dynamics_contact_update.md)  
