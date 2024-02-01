---
title: "OnControlAddIn (Page Field) Trigger"
description: "Executed when a control add-in on the client sends event information to the server-side business logic."
ms.author: solsen
ms.custom: na
ms.date: 07/05/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnControlAddIn (Page Field) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Executed when a control add-in on the client sends event information to the server-side business logic.


## Syntax
```AL
trigger OnControlAddIn(Index: Integer; Data: Text)
begin
    ...
end;
```

### Parameters

*Index*  
&emsp;Type: [Integer](../../methods-auto/integer/integer-data-type.md)  
Specifies an integer identifier that a control add-in sends with the event.  

*Data*  
&emsp;Type: [Text](../../methods-auto/text/text-data-type.md)  
Specifies a text string that a control add-in sends with an event.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
