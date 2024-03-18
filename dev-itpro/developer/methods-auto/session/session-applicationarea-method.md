---
title: "Session.ApplicationArea([Text]) Method"
description: "Gets or sets the application areas for the current session."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Session.ApplicationArea([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the application areas for the current session.


## Syntax
```AL
[ApplicationArea := ]  Session.ApplicationArea([ApplicationArea: Text])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*[Optional] ApplicationArea*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new application areas for the current session.  


## Return Value
*[Optional] ApplicationArea*  
&emsp;Type: [Text](../text/text-data-type.md)  
The application areas for the current session.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This method lets you hide certain user interface elements (including page fields and actions, and report request page options) based on the application area to which they belong. Controls that define these items can be tagged with one or more application areas by setting the ApplicationArea property. When the ApplicationArea method is called in a client session, only those controls that are tagged with the application areas set by the method will be appear in the user interface.  
  
> [!NOTE]  
>  Currently, this functionality is intended for the application areas that are defined in **table 9178 Application Area Setup**. You can define your own application areas but be aware that the implementation might change in future release.  

## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)