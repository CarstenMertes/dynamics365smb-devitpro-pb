---
title: "Report.ExcelLayout(Integer, InStream) Method"
description: "Gets the Excel layout that is used on a report and returns it as a data stream."
ms.author: solsen
ms.custom: na
ms.date: 10/11/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Report.ExcelLayout(Integer, InStream) Method
> **Version**: _Available or changed with runtime version 9.0._

Gets the Excel layout that is used on a report and returns it as a data stream.


## Syntax
```AL
[Ok := ]  Report.ExcelLayout(Number: Integer, InStream: InStream)
```
## Parameters
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the report object for which you want to get the Excel layout.  

*InStream*  
&emsp;Type: [InStream](../instream/instream-data-type.md)  
The variable in which to return the Excel layout.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Using the return value is optional. When you use the return value, if the Excel layout can't be retrieved at runtime, then the system returns **false** and no error is recorded. When you omit the return value, if the Excel layout can't be retrieved at runtime, then an error occurs, which states that the layout couldn't be retrieved. 

## Example

The `Report.ExcelLayout` method will throw a runtime error if the operation fails, either if no object exists with that object ID or if no Excel layout exists for that report. This code example shows how to write robust AL code to handle possible failures.

```AL
var
    layoutAsStream: InStream;
    result: Boolean;
begin
    result := Report.ExcelLayout(ObjectId, layoutAsStream);
    if result then begin
        // use the layout that now is available in the stream
    end
    else
        // handle that no object exists with that id or that no Excel layout exists for that report
    ;
end;
```

## See also

[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)