---
title: "ExternalName Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---

# ExternalName Property

Specifies the name of the original table in the external database.  

Specify this property if the original name is different from the name that you specify in the **Name** property. This means that you can use a different name for the table in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)].  

## Applies to  

- Tables  

## Property Value  
The name of the table in the external database.  

## Syntax

```AL
ExternalName = 'organization';
```

## Remarks

This property appears when you specify **CDS** or **ExternalSQL** in the **TableType** property. These tables use a different SQL Server connection than the normal tables in the [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] database.  

## See Also

[TableType Property](devenv-tabletype-property.md)   
[ExternalSchema Property](devenv-externalschema-property.md)   
[Name Property](devenv-name-property.md)   
[Properties](devenv-properties.md)   