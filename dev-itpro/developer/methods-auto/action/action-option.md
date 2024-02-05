---
title: "Action System Option"
description: "Represents the action that the user took on the page."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Action Option Type
> **Version**: _Available or changed with runtime version 1.0._

Represents the action that the user took on the page.

## Members
|  Member  |  Description  |
|----------------|---------------|
|None|Represents the result of running a page.|
|OK|Represents the result of the user closing a page window by performing one of the following actions:<br/>      - Chooses the **OK** button.<br/>      - Chooses the **X** button when there was no **Cancel** button on the window.<br/>      - Presses the Esc key when there is no **Cancel** button on the window.|
|Cancel|Represents the result of the user closing a page window by performing one of the following actions:<br/>      - Chooses the **Cancel** button.<br/>      - Chooses the **X** button when there is a **Cancel** button on the window.<br/>      - Presses the Esc key when there is a **Cancel** button on the window|
|LookupOK|Represents the result of the user closing a lookup window by performing one of the following actions:<br/>      - Chooses the **OK** button.<br/>      - Chooses an item in the Lookup window.|
|LookupCancel|Represents the result of the user closing a lookup window by choosing the **Cancel** button.|
|Yes|Represents the result of the user closing a confirmation window by choosing the **Yes** button.|
|No|Represents the result of the user closing a confirmation window by performing one of the following actions:<br/>      - Chooses the No button.<br/>      - Chooses the X button.<br/>      - Presses the Esc key.|
|RunObject|Represents the result of the user selecting an option that ran another object.|
|RunSystem|Represents the result of the user selecting an option that ran an external program.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  