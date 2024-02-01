---
title: "OnClosePageEvent (Page) Trigger Event"
description: "Executed after the OnClosePage trigger, which is called when page closes after the OnQueryClosePage trigger is executed."
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

# OnClosePageEvent (Page) Trigger Event
> **Version**: _Available or changed with runtime version 1.0._

Executed after the OnClosePage trigger, which is called when page closes after the OnQueryClosePage trigger is executed.


## Syntax
```AL
[EventSubscriber(ObjectType::Page, Page::<Page Name>, 'OnClosePageEvent', '', <SkipOnMissingLicense>, <SkipOnMissingPermission>)]
local procedure MyProcedure(var Rec: Record)
begin
    ...
end;
```

### Parameters

*Rec*  
&emsp;Type: [Record](../../../methods-auto/record/record-data-type.md)  
The table that raises the event.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../../devenv-get-started.md)  
[Developing Extensions](../../../devenv-dev-overview.md)   