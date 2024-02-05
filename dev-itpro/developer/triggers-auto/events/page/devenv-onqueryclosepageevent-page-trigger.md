---
title: "OnQueryClosePageEvent (Page) Trigger Event"
description: "Executed after the OnQueryClosePage trigger, which is called as a page closes and before the OnClosePage trigger executes."
ms.author: solsen
ms.custom: na
ms.date: 01/20/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnQueryClosePageEvent (Page) Trigger Event
> **Version**: _Available or changed with runtime version 1.0._

Executed after the OnQueryClosePage trigger, which is called as a page closes and before the OnClosePage trigger executes.


## Syntax
```AL
[EventSubscriber(ObjectType::Page, Page::<Page Name>, 'OnQueryClosePageEvent', '', <SkipOnMissingLicense>, <SkipOnMissingPermission>)]
local procedure MyProcedure(var Rec: Record; var AllowClose: Boolean)
begin
    ...
end;
```

### Parameters

*Rec*  
&emsp;Type: [Record](../../../methods-auto/record/record-data-type.md)  
The table that raises the event.  

*AllowClose*  
&emsp;Type: [Boolean](../../../methods-auto/boolean/boolean-data-type.md)  
Specifies whether to the page can close. If this parameter is true, the code will be executed. If this parameter is false, then the code is not executed.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../../devenv-get-started.md)  
[Developing Extensions](../../../devenv-dev-overview.md)   