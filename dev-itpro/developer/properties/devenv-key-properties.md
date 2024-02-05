---
title: "Key Properties"
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Key Properties

The keys associated with a table have properties that describe their behavior, just as tables and fields do. When you create a key, [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] automatically suggests a number of default values for these properties. Depending on the purpose of the key, you will sometimes want to change these default values.  

[!INCLUDE[properties_note](../includes/properties_note.md)]

|Property Name|Use|  
|-------------------|---------|  
|[Enabled](devenv-enabled-property.md)|Determines whether the system will maintain any indexes for the key. You cannot use a key unless it is enabled.|  
|[Key](./devenv-properties.md)|Defines the key name and fields.|  
|[SumIndexFields](devenv-sumindexfields-property.md)|Determines the fields for which the system will maintain a SumIndex.|  
|[MaintainSQLIndex](./devenv-maintainsqlindex-property.md)|Determines whether a SQL Server index corresponding to the fields in the key should be created.|  
|[MaintainSIFTIndex](./devenv-maintainsiftindex-property.md)|Determines whether SIFT indexes (indexed views) structures should be created in SQL Server to support the corresponding SumIndexFields for the [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] key.|  
|[Clustered](devenv-clustered-property.md)|Sets a value that indicates whether the key defines the clustered index for the table.|  
|[SQLIndex](./devenv-sqlindex-property.md)|Sets the actual fields and field order that are used in the corresponding index on SQL Server.|  
|[Unique](devenv-unique-property.md)|Sets whether the value of a key must be unique.| 

## See Also  

[Table Keys](../devenv-table-keys.md)