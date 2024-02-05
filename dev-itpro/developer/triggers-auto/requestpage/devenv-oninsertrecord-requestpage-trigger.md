---
title: "OnInsertRecord (Request Page) Trigger"
description: "Runs before a new record is inserted into the table."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnInsertRecord (Request Page) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs before a new record is inserted into the table.


## Syntax
```AL
trigger OnInsertRecord(BelowxRec: Boolean): Ok
begin
    ...
end;
```

### Parameters

*BelowxRec*  
&emsp;Type: [Boolean](../../methods-auto/boolean/boolean-data-type.md)  
This return value indicates whether the new record is to be inserted after the last record in the table (xRec). If false, the record is to be inserted between an existing record and the last record. If true, the record is to be inserted below the last record in the table (xRec).  


## Return Value

*Ok*  
&emsp;Type: [Boolean](../../methods-auto/boolean/boolean-data-type.md)  
**true** if the record was inserted, otherwise **false**. The return value is checked after each call. The default value is **true**.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

If an error occurs in the trigger code, the action is canceled, but the page is not closed. The user cannot enter any new data and an error is shown in the message bar.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnInsertRecord (Page) Trigger](../page/devenv-oninsertrecord-page-trigger.md)  
[OnInsertRecord (Request Page Extension) Trigger](../requestpageextension/devenv-oninsertrecord-requestpageextension-trigger.md)  
[OnInsertRecord (Page Extension) Trigger](../pageextension/devenv-oninsertrecord-pageextension-trigger.md)
