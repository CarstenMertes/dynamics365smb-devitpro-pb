---
title: "Database.GetDefaultTableConnection(TableConnectionType) Method"
description: "Gets the default table connection based on the specified connection type."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Database.GetDefaultTableConnection(TableConnectionType) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the default table connection based on the specified connection type. You must already have registered a table connection of this type.


## Syntax
```AL
Name :=   Database.GetDefaultTableConnection(Type: TableConnectionType)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Type*  
&emsp;Type: [TableConnectionType](../tableconnectiontype/tableconnectiontype-option.md)  
The type of table connection as defined in the TableType property.  


## Return Value
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)