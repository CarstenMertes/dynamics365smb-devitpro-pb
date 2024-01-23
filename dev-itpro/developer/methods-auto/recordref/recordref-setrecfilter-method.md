---
title: "RecordRef.SetRecFilter() Method"
description: "Sets a filter on a record that is referred to by a RecordRef."
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
# RecordRef.SetRecFilter() Method
> **Version**: _Available or changed with runtime version 1.0._

Sets a filter on a record that is referred to by a RecordRef.


## Syntax
```AL
 RecordRef.SetRecFilter()
```

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This method works the same as the [SetRecFilter Method \(Record\)](../record/record-setrecfilter-method.md).  

## Example  

The following example opens the Customer table as a RecordRef variable that is named MyRecordRef. The SetRecFilter method sets the values in the current key of the current record as a record filter. The [GetFilters Method \(RecordRef\)](recordref-getfilters-method.md) retrieves the filters that have been set and displays them in a message box. No. is displayed because the filter is set on the No. field, which is the current key. 
 
```al
var
    MyRecordRef: RecordRef;
    varFilters: Text;
    Text000: Label 'The filter is set on the %1 field.';
begin 
    MyRecordRef.Open(Database::Customer);  
    MyRecordRef.SetRecFilter;  
    varFilters := MyRecordRef.GetFilters;  
    Message(Text000, varFilters);  
end;
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)