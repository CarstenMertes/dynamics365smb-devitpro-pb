---
title: paymentTerm resource type  
description: A payment term object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# paymentTerm resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents a payment term in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET paymentTerm](../api/dynamics_paymentterm_get.md)|paymentTerm|Gets a payment term object.|
|[DELETE paymentTerm](../api/dynamics_paymentterm_delete.md)|none|Deletes a payment term object.|
|[POST paymentTerm](../api/dynamics_paymentterm_create.md)|paymentTerm|Creates a payment term object.|
|[PATCH paymentTerm](../api/dynamics_paymentterm_update.md)|paymentTerm|Updates a payment term object.|



## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the payment term. Non-editable.|
|code|string|The code of the payment term.|
|displayName|string|Specifies the payment term's name. This name will appear on all sales documents for the payment term.|
|dueDateCalculation|string|Specifies the formula that is used to calculate the date that a payment must be made.|
|discountDateCalculation|string|Specifies the formula that is used to calculate the date that a payment must be made in order to obtain a discount.|
|discountPercent|decimal|The line discount percent.    |
|calculateDiscountOnCreditMemos|boolean|Specifies if the discount should be applied to payment term. **True** indicates a discount will be given, **false** indicates a discount will not be given.|
|lastModifiedDateTime|datetime|The last datetime the payment term was modified. Read-Only.|

## JSON representation

Here is a JSON representation of the paymentTerm resource.


```json
{
    "id": "GUID",
    "code": "string",
    "displayName": "string",
    "dueDateCalculation": "string",
    "discountDateCalculation": "string",
    "discountPercent": "decimal",
    "calculateDiscountOnCreditMemos": "boolean",
    "lastModifiedDateTime": "datetime"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->



## See Also
[GET paymentTerm](../api/dynamics_paymentTerm_Get.md)  
[DELETE paymentTerm](../api/dynamics_paymentTerm_Delete.md)  
[POST paymentTerm](../api/dynamics_paymentTerm_Create.md)  
[PATCH paymentTerm](../api/dynamics_paymentTerm_Update.md)
