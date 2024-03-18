---
title: "Database.HasTableConnection(TableConnectionType, Text) Method"
description: "Verifies if a connection to an external database exists based on the specified name."
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
# Database.HasTableConnection(TableConnectionType, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Verifies if a connection to an external database exists based on the specified name.


## Syntax
```AL
Ok :=   Database.HasTableConnection(Type: TableConnectionType, Name: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Type*  
&emsp;Type: [TableConnectionType](../tableconnectiontype/tableconnectiontype-option.md)  
Specifies the type of table connection as defined in the TableType property.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the external table connection. You must already have registered a table connection with this name.  


## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if a connection to an external database exists for the specified name, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)