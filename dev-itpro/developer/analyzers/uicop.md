---
title: "UICop Analyzer"
description: "UICop is an analyzer that enforces rules that must be respected by extensions meant to customize the Web Client."
ms.author: solsen
ms.custom: na
ms.date: 10/25/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# UICop Analyzer Rules
UICop is an analyzer that enforces rules that must be respected by extensions meant to customize the Web Client.

## Rules

|Id|Title|Category|Default Severity|
|--|-----------|--------|----------------|
|[AW0001](uicop-aw0001.md)|The Web client does not support displaying the Request page of XMLPorts.|WebClient|Warning|
|[AW0002](uicop-aw0002.md)|The Web client does not support displaying both Actions and Fields in Cue Groups. Only Fields will be displayed.|WebClient|Warning|
|[AW0003](uicop-aw0003.md)|The Web client does not support displaying Repeater controls containing Parts.|WebClient|Warning|
|[AW0004](uicop-aw0004.md)|A Blob cannot be used as a source expression for a page field.|WebClient|Warning|
|[AW0005](uicop-aw0005.md)|Actions should use the Image property.|WebClient|Info|
|[AW0006](uicop-aw0006.md)|Pages and reports should use the UsageCategory and ApplicationArea properties to be searchable.|WebClient|Info|
|[AW0007](uicop-aw0007.md)|The Web client does not support displaying Repeater controls that contain FlowFilter fields.|WebClient|Error|
|[AW0008](uicop-aw0008.md)|The Web client only supports displaying Repeater controls in pages of type List, ListPart, and Worksheet.|WebClient|Warning|
|[AW0009](uicop-aw0009.md)|Using a Blob with subtype Bitmap on a page field is deprecated. Instead use the Media/MediaSet data types.|WebClient|Warning|
|[AW0010](uicop-aw0010.md)|A Repeater control used on a List page must be defined at the beginning of the area(Content) section.|WebClient|Warning|
|[AW0011](uicop-aw0011.md)|Add PromotedOnly="true" to some or all promoted actions to avoid identical actions from appearing in both the promoted and default sections of the command bar.|WebClient|Info|
|[AW0012](uicop-aw0012.md)|The Web client does not support properties for teaching tips in certain contexts.|WebClient|Warning|
|[AW0013](uicop-aw0013.md)|Groups containing promoted actions should not be hidden.|WebClient|Warning|
|[AW0014](uicop-aw0014.md)|Groups containing ActionRef targets should not be hidden.|WebClient|Warning|
|[AW0015](uicop-aw0015.md)|Actions with scope repeater must be promoted.|WebClient|Warning|
|[AW0016](uicop-aw0016.md)|Rich Text Editor fields are only allowed while alone in a FastTab group.|WebClient|Warning|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Using the Code Analysis Tool](../devenv-using-code-analysis-tool.md)  
[Ruleset for the Code Analysis Tool](../devenv-rule-set-syntax-for-code-analysis-tools.md)  
[Using the Code Analysis Tools with the Ruleset](../devenv-using-code-analysis-tool-with-rule-set.md)