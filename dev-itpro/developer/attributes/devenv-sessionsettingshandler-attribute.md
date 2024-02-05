---
title: "SessionSettingsHandler Attribute"
description: "Specifies a SessionSettingsHandler method, which handles RequestSessionUpdate statements."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# SessionSettingsHandler Attribute
> **Version**: _Available or changed with runtime version 3.0._

Specifies a SessionSettingsHandler method, which handles RequestSessionUpdate statements.


## Applies To

- Method

> [!NOTE]
> The **SessionSettingsHandler** attribute can only be set inside codeunits with the **SubType property** set to **Test**.

## Syntax


> **Version**: _Available or changed with runtime version 3.0._
```AL
[SessionSettingsHandler]
procedure SessionSettingsHandler(var SessionSettings: SessionSettings) : Boolean;
```
> [!IMPORTANT]
> The above signature requires the SessionSettingsHandler method to be *global*. For more information, see [Local and global scope in AL methods](../devenv-al-methods.md%23local-and-global-scope).

### Arguments
*SessionSettings*  
&emsp;Type: [SessionSettings](../methods-auto/sessionsettings/sessionsettings-data-type.md)  
Session settings object to be populated  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Remarks

The **SessionSettingsHandler** method is called when SessionSetting is updated. 

You use handler methods to automate tests by handling instances when user interaction is required by the code that is being tested by the test method. In these instances, the handler method is run instead of the requested user interface. The handler method should simulate the user interaction for the test case, such as validating messages, making selections, or entering values. You declare a handler type attribute on the method. For more information about handler methods, see [Create Handler Methods](../devenv-creating-handler-methods.md).

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Method Attributes](devenv-method-attributes.md)  
[Test Codeunits and Test Functions](../devenv-test-codeunits-and-test-methods.md)