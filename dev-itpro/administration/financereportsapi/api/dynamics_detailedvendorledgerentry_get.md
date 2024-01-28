---
title: Get detailedVendorLedgerEntries
description: Gets a detailed vendor ledger entry object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 08/11/2022
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get detailedVendorLedgerEntries (Beta)

Retrieves the properties and relationships of a detailed vendor ledger entry object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../../api-reference/v2.0/endpoints-apis-for-dynamics.md).
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different -->
```
GET businesscentralPrefix/companies({id})/detailedVendorLedgerEntries({id})
```
<!-- END>EDIT_IS_REQUIRED -->
## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **detailedVendorLedgerEntry** object in the response body.

## Example

**Request**

Here is an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different -->
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/detailedVendorLedgerEntries({id})
```
<!-- END>EDIT_IS_REQUIRED -->
**Response**

Here is an example of the response.

<!-- START>EDIT_IS_REQUIRED. Fill in values for properties -->
```json
{
    "entryNumber" : "",
    "entryType" : "",
    "vendorNumber" : "",
    "amount" : "",
    "debitAmount" : "",
    "creditAmount" : "",
    "amountLocalCurrency" : "",
    "debitAmountLocalCurrency" : "",
    "creditAmountLocalCurrency" : "",
    "initialEntryGLobalDim1" : "",
    "initialEntryGLobalDim2" : "",
    "postingDate" : "",
    "currencyCode" : "",
    "lastModifiedDateTime" : ""
}
```
<!-- END>EDIT_IS_REQUIRED -->
## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[detailedVendorLedgerEntry](../resources/dynamics_detailedVendorLedgerEntry.md)  
