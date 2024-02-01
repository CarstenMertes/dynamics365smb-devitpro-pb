---
title: "Database.ImportData(Boolean, var Text [, Boolean] [, Boolean] [, Record]) Method"
description: "Imports data from a file that has been exported from a database."
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
# Database.ImportData(Boolean, var Text [, Boolean] [, Boolean] [, Record]) Method
> **Version**: _Available or changed with runtime version 1.0._

Imports data from a file that has been exported from a database.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Ok := ]  Database.ImportData(ShowDialog: Boolean, var FileName: Text [, IncludeApplicationData: Boolean] [, IncludeGlobalData: Boolean] [, CompanyRecord: Record])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*ShowDialog*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if you want to display a dialog box where the user can confirm the action.  

*FileName*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the name and location of the file that must be imported. The file must have been exported from a database
      .  

*[Optional] IncludeApplicationData*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if you want to import the data that defines the application in the database. This includes the permissions, permission sets, profiles, and style sheets.
Create a variable of type Boolean to specify this parameter.
To import application objects, you must use the Import-NAVData Windows PowerShell cmdlet.  

*[Optional] IncludeGlobalData*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if you want to import global, non-company specific data.
Create a variable of type Boolean to specify this parameter.  

*[Optional] CompanyRecord*  
&emsp;Type: [Record](../record/record-data-type.md)  
Specifies the company or companies that must be imported.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)