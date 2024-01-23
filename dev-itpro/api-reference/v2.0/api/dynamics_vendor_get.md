---
title: Get vendors  
description: Gets a vendor object in Dynamics 365 Business Central. 
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get vendors

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a vendor object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].


## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/vendors({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **vendors** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/vendors({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "f7a5738a-44e3-ea11-bb43-000d3a2feca1",
    "number": "10000",
    "displayName": "Fabrikam, Inc.",
    "addressLine1": "10 North Lake Avenue",
    "addressLine2": "",
    "city": "Atlanta",
    "state": "GA",
    "country": "US",
    "postalCode": "31772",
    "phoneNumber": "4255550101",
    "email": "krystal.york@contoso.com",
    "website": "www.royalmail.co.uk",
    "taxRegistrationNumber": "",
    "currencyId": "00000000-0000-0000-0000-000000000000",
    "currencyCode": "USD",
    "irs1099Code": "",
    "paymentTermsId": "0aa5738a-44e3-ea11-bb43-000d3a2feca1",
    "paymentMethodId": "3b196a90-44e3-ea11-bb43-000d3a2feca1",
    "taxLiable": true,
    "blocked": " ",
    "balance": 2071.13,
    "lastModifiedDateTime": "2020-08-21T07:38:46.53Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[vendor](../resources/dynamics_vendor.md)    
[Delete vendor](dynamics_vendor_Delete.md)    
[Create vendor](dynamics_vendor_Create.md)    
[Update vendor](dynamics_vendor_Update.md)    
