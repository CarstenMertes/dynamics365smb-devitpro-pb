---
title: "ExternalType property"
description: "Specifies the type of the original table field in the external database."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ExternalType Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the type of the original table field in the external database.

Specify this property if the original type is different from the type that you specify in the Type property. This means that you can use a different type for the table.

## Applies to
-   Table field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Value

- String  
- Picklist

> [!NOTE]  
> The field values are dependent on the providers for the TableType to interpret the process. The different providers use it differently. For example, MicrosoftGraph vs CDS. 

## Syntax

```AL
ExternalType = 'String';
```

## Remarks

This property is used when you specify **CDS**, **MicrosoftGraph** or **ExternalSQL** in the **TableType** property. These tables use a different SQL Server connection than the normal tables in the [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] and [!INCLUDE[navnow_md](../includes/navnow_md.md)] database.  

## Related information

[TableType Property](devenv-tabletype-property.md)  
[ExternalSchema Property](devenv-externalschema-property.md)  
[Name Property](./devenv-properties.md)  
[Properties](devenv-properties.md)