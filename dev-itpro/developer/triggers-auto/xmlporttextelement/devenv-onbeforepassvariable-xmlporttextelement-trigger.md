---
title: "OnBeforePassVariable (Xml Port Text Element) Trigger"
description: "Runs after the source expression has been formatted into a text variable and before the text variable is passed to the XML document."
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

# OnBeforePassVariable (Xml Port Text Element) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs after the source expression has been formatted into a text variable and before the text variable is passed to the XML document.


## Syntax
```AL
trigger OnBeforePassVariable()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This trigger is only used to export data and is typically used to manipulate the text variable.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnBeforePassVariable (Xml Port Text Attribute) Trigger](../xmlporttextattribute/devenv-onbeforepassvariable-xmlporttextattribute-trigger.md)
