---
title: (v1.0) Get purchaseInvoice pdfDocument
description: (v1.0) Gets a PDF document on a purchaseInvoice in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen
ms.custom: evergreen
ms.topic: reference
ms.devlang: al
ms.date: 05/01/2024
ms.update-cycle: 1095-days
ms.author: solsen
ms.reviewer: solsen
---

# Get purchaseInvoice pdfDocument (v1.0)
Retrieve a PDF print-out of the corresponding document as binary content for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> To generate a document in the supported local language, you must specify `Accept-Language` in the Request header, for example `Accept-Language: nl-NL` for Dutch.

## HTTP request (v1.0)
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
The following example gets a link to the content of the PDF:

```
GET businesscentralPrefix/api/v1.0/companies({id})/purchaseInvoices({invoiceid})/pdfDocument
```

## Request headers (v1.0)

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and a link to the PDF document in the response body.

## Example (v1.0)

**Request**
Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/purchaseInvoices({invoiceid})/pdfDocument
```

**Response**
Here is an example of the response.

> [!NOTE]  
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{

    "@odata.context":"https://api.businesscentral.dynamics.com/v1.0/api/v1.0/$metadata#companies('CRONUS%20International%20Ltd.')/purchaseInvoices(94913756-80e9-47bc-995a-048a655b8cdd)/pdfDocument",
    "value":
    [
        {
            "@odata.etag":"W/\"JzQ0O0tQNUdjaUtZcU8rcUNCQTdXOUxIZVEwalA0clhjSmlXU1pqWjQ4RFczd2s9MTswMDsn\"",
            "id":"94913756-80e9-47bc-995a-048a655b8cdd",
            "content@odata.mediaReadLink":"https:// api.businesscentral.dynamics.com/v1.0/pi/v1.0/companies(name='CRONUS%20International%20Ltd.')/purchaseInvoices(94913756-80e9-47bc-995a-048a655b8cdd)/pdfDocument(94913756-80e9-47bc-995a-048a655b8cdd)/content"
        }
    ]
}
```

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
The following example gets the actual PDF document:
`GET businesscentralPrefix/api/v1.0/companies({companyid})/purchaseInvoices({invoiceid})/pdfDocument({id})/content`

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body 
Do not supply a request body for this method.

## Response
If successful, this method returns a `200 OK` response code and the PDF document in the response body.

## Example

**Request**
Here is an example of the request.

```
GET https://{businesscentralPrefix}/api/v1.0/companies({companyid})/purchaseInvoices({invoiceid})/pdfDocument({id})/content
```

**Response** 
The PDF document in binary format.

## Remarks

The pdfDocument is not supported for unposted purchase invoices. The purchase invoice must be posted before it is printed; if it is not posted, the response will return an error.

## Related information
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  


[Error Codes](../dynamics_error_codes.md)  
