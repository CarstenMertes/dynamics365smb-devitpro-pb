---
title: contact resource type  
description: A contact object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/28/2025
ms.author: solsen
ms.reviewer: solsen
---

# contact resource type

Represents a contact in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET contact](../api/dynamics_contact_get.md)|contact|Gets a contact object.|
|[DELETE contact](../api/dynamics_contact_delete.md)|none|Deletes a contact object.|
|[POST contact](../api/dynamics_contact_create.md)|contact|Creates a contact object.|
|[PATCH contact](../api/dynamics_contact_update.md)|contact|Updates a contact object.|

## Navigation

| Navigation |Return Type| Description |
|:----------|:----------|:-----------------|
|[contactInformation](dynamics_contactinformation.md)|contactInformation |Gets the contactinformation of the contact.|
|[picture](dynamics_picture.md)|picture |Gets the picture of the contact.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the contact. Non-editable.|
|number|string|Specifies the number of the contact.|
|type|NAV.contactType|Specifies the type of contact, can be "Company" or "Person".|
|displayName|string|Specifies the contact's name. This name will appear on all sales documents for the contact.|
|jobTitle|string|The job title of the contact.|
|companyNumber|string|The number of the company.|
|companyName|string|The name of the company.|
|contactBusinessRelation|NAV.contactBusinessRelation||
|addressLine1|string|Specifies the contact's address. This address will appear on all sales documents for the contact.|
|addressLine2|string|Specifies the contact's address. This address will appear on all sales documents for the contact.|
|city|string|Specifies the contact's city.|
|state|string|Specifies the contact's state.|
|country|string|Specifies the contact's country.|
|postalCode|string|Specifies the contact's postal code.|
|phoneNumber|string|Specifies the contact's telephone number.|
|mobilePhoneNumber|string|The mobile phone number.|
|email|string|Specifies the contact's email address.|
|website|string|Specifies the contact's home page address.|
|searchName|string|The name used for searching.|
|privacyBlocked|boolean|Specifies whether the privacy of the contact is blocked.|
|taxRegistrationNumber|string|Specified the tax registration number of the contact.|
|lastInteractionDate|date|The date of the last interaction with the contact.|
|lastModifiedDateTime|datetime|The last datetime the contact was modified. Read-Only.|

## JSON representation

Here's a JSON representation of the contact resource.


```json
{
    "id": "GUID",
    "number": "string",
    "type": "NAV.contactType",
    "displayName": "string",
    "jobTitle": "string",
    "companyNumber": "string",
    "companyName": "string",
    "contactBusinessRelation": "NAV.contactBusinessRelation",
    "addressLine1": "string",
    "addressLine2": "string",
    "city": "string",
    "state": "string",
    "country": "string",
    "postalCode": "string",
    "phoneNumber": "string",
    "mobilePhoneNumber": "string",
    "email": "string",
    "website": "string",
    "searchName": "string",
    "privacyBlocked": "boolean",
    "taxRegistrationNumber": "string",
    "lastInteractionDate": "date",
    "lastModifiedDateTime": "datetime"
}
```

## Remarks

This resource type requires [!INCLUDE[prod_short](../../../includes/prod_short.md)] version 18.0.

## Related information

[GET contact](../api/dynamics_contact_get.md)  
[DELETE contact](../api/dynamics_contact_delete.md)  
[POST contact](../api/dynamics_contact_create.md)  
[PATCH contact](../api/dynamics_contact_update.md)  
