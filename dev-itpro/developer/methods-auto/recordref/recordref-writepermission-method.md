---
title: "RecordRef.WritePermission() Method"
description: "Determines if you can write to a table."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# RecordRef.WritePermission() Method
> **Version**: _Available or changed with runtime version 1.0._

Determines if you can write to a table.


## Syntax
```AL
Ok :=   RecordRef.WritePermission()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if you have permission to write to the table


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This method can test for both full write permission and a partial write permission that has been granted with a security filter. A write permission consists of Insert, Delete, and Modify permissions.  
  
 This method uses the filter that is currently applied to the *RecordRef* to determine whether you have write permission. If no filter is applied, the method tests for full write permission. If a filter has been set, the method only tests for write permission in the range of the filter.  
  
 To determine whether the user has partial write permission, because a security filter has been applied, view the **Permissions** page. <!--Links For more information, see [How to: Set Security Filters](How-to-Set-Security-Filters.md).-->  
  
 If you do not have permission to write to a table and you attempt to write, a run-time error occurs. This method lets you determine in advance if you have write permission. When the permissions are checked, the combination of permissions in the license file and the user's permissions in the Permission table is considered.  
  
 This method works the same as the [WritePermission Method \(Record\)](../record/record-writepermission-method.md).  
  
## Example  
 The following example opens table 18 \(Customer\) and creates a RecordRef variable that is named MyRecordRef for the table. The WritePermission method determines whether the table has write permission and stores the return value in the varHasWritePerm variable. The Customer table has write permission, so the message displays **Yes**. You can initialize the varTableNo variable with any table number. 
  
```al
var
    MyRecordRef: RecordRef;
    varTableNo: Integer;
    varHasWritePerm: Boolean;
    Text000: Label 'Does the %1 table have write permission? %2';
begin  
    varTableNo := 18;  
    MyRecordRef.Open(varTableNo);  
    varHasWritePerm := MyRecordRef.WritePermission;  
    Message(Text000, MyRecordRef.Name, varHasWritePerm);  
end;
```  
  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)