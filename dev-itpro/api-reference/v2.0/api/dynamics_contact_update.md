---
title: Update contacts  
description: Updates a  contact object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Update contacts

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Updates the properties of a contact object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different or there might be more than one-->
```
PATCH businesscentralPrefix/companies({id})/contacts({id})
```
<!-- END>EDIT_IS_REQUIRED-->
## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **contact**, the **contact** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **contact** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/contacts({id})
Content-type: application/json
{
    "id" : "5d115c9c-44e3-ea11-bb43-000d3a2feca1",
    "number" : "108001"
}
```

**Response**
Here is an example of the response.

```json
HTTP/1.1 200 OK
Content-type: application/json
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

## See Also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[contact](../resources/dynamics_contact.md)  
[GET contact](dynamics_contact_get.md)  
[DELETE contact](dynamics_contact_delete.md)  
[POST contact](dynamics_contact_create.md)  
