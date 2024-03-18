---
title: "Database.UnregisterTableConnection(TableConnectionType, Text) Method"
description: "Unregisters a table connection to an external database."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Database.UnregisterTableConnection(TableConnectionType, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Unregisters a table connection to an external database.


## Syntax
```AL
 Database.UnregisterTableConnection(Type: TableConnectionType, Name: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Type*  
&emsp;Type: [TableConnectionType](../tableconnectiontype/tableconnectiontype-option.md)  
Specifies the type of table connection as defined in the TableType property. If the table is of type ExternalSQL, UNREGISTERTABLECONNECTION rolls back the current transaction.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the name of the connection in your code, or the name of the primary key field on the table.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)