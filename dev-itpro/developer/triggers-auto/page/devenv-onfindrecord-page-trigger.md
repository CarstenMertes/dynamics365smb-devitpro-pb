---
title: "OnFindRecord (Page) Trigger"
description: "Overrides the default page behavior and enables you to specify which record you want to display when the page opens."
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

# OnFindRecord (Page) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Overrides the default page behavior and enables you to specify which record you want to display when the page opens.


## Syntax
```AL
trigger OnFindRecord(Which: Text): Ok
begin
    ...
end;
```

### Parameters

*Which*  
&emsp;Type: [Text](../../methods-auto/text/text-data-type.md)  
Text or code value with the following options:
- (a dash): First record,
+ (a plus sign): Last record,
=\<\>: Record defined in the Rec variable or the closest match.  


## Return Value

*Ok*  
&emsp;Type: [Boolean](../../methods-auto/boolean/boolean-data-type.md)  
**true** if the specified record was found, otherwise, **false**.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

By default, open pages display the last record shown when the user exited the page. Use this trigger to override the default behavior and display the first record, last record, or a specific record as defined in the `Rec` variable.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnFindRecord (Request Page) Trigger](../requestpage/devenv-onfindrecord-requestpage-trigger.md)
