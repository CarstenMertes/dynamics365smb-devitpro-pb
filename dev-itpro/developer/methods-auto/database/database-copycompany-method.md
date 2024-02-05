---
title: "Database.CopyCompany(Text, Text) Method"
description: "Creates a new company and copies all data from an existing company in the same database."
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
# Database.CopyCompany(Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a new company and copies all data from an existing company in the same database.


## Syntax
```AL
[Ok := ]  Database.CopyCompany(SourceName: Text, DestinationName: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*SourceName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the company that you want to copy data from.  

*DestinationName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the company that you want to create and copy data to. The company name can have a maximum of 30 characters. If the database collation is case-sensitive, you can have one company called COMPANY and another called Company. However, if the database is case-insensitive, you cannot create companies with names that differ only by case.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Links and notes on records are not copied to the new company.

With versions 17.5 and later, errors in COPYCOMPANY can't be trapped. This change prevents a company from being partially copied when an error occurs and it's followed by a COMMIT(). Any error in COPYCOMPANY ends the execution flow, even with statements like: `IF NOT CopyCompany(.., ..) THEN`. Also, any COMMIT() in triggers or event subscribers is ignored.

## Example

The following example is based on the **Copy Company** batch job, which is part of the [!INCLUDE[demo](../../includes/demo_md.md)]. The batch job takes the Company system table as a data item and uses the **Name** field as the value of the *SourceName* parameter. The value of the *DestinationName* parameter is specified in the **New Company Name** field in the request page, which is represented by the `NewCompanyName` variable.  

```al
CopyCompany(Name, NewCompanyName);  
```  

## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)