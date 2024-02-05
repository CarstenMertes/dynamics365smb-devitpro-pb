---
title: "HandlerFunctions Attribute"
description: "Specifies the handler methods that are used by the test method."
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

# HandlerFunctions Attribute
> **Version**: _Available or changed with runtime version 1.0._

Specifies the handler methods that are used by the test method.


## Applies To

- Method

> [!NOTE]
> The **HandlerFunctions** attribute can only be set inside codeunits with the **SubType property** set to **Test**.

## Syntax

```AL
[HandlerFunctions(HandlerNames: Text)]
```

### Arguments
*HandlerNames*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
The names of the handler methods used by the test method.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

> [!NOTE]  
> If the test method uses more than one handler method, then you should separate the handler method names by a comma.  
  
## Remarks

You use test codeunits and test methods to test your application. A handler method allows you to automate tests by handling instances when user interaction is required by the code that is being tested. In these instances, the test method calls the handler method, which is run instead of the user interface.  
  
The following is some important information about handler methods:  
  
- To be a handler method, the method must have set to one of the attributes:  
  [MessageHandler](devenv-messagehandler-attribute.md)  
  [ConfirmHandler](devenv-confirmhandler-attribute.md)  
  [StrMenuHandler](devenv-strmenuhandler-attribute.md)  
  [PageHandler](devenv-pagehandler-attribute.md)  
  [ModalPageHandler](devenv-modalpagehandler-attribute.md)  
  [ReportHandler](devenv-reporthandler-attribute.md)  
  [RequestPageHandler](devenv-requestpagehandler-attribute.md)  
  [SendNotificationHandler](devenv-sendnotificationhandler-attribute.md)  
  [HyperLinkHandler](devenv-hyperlinkhandler-attribute.md)  
  [RecallNotificationHandler](devenv-recallnotificationhandler-attribute.md)  
  [SessionSettingsHandler](devenv-sessionsettingshandler-attribute.md)  
  [FilterPageHandler](devenv-filterpagehandler-attribute.md)
  
- A test method can only call handler methods that are defined in the same test codeunit as the test method.  
  
- A test method can call **MessageHandler**, **ConfirmHandler**, and **StrMenuHandler** type handlers only once. It can call **PageHandler**, **ModalPageHandler**, **ReportHandler**, **RequestPageHandler**, or **FilterPageHandler** type handlers multiple times but only once per application object ID.  
  
- Every handler method that you enter in the **HandlerFunctions** attribute must be called at least once in the test method. If you execute a test method that has a handler method listed that is not called, then the test fails.  

You use handler methods to automate tests by handling instances when user interaction is required by the code that is being tested by the test method. In these instances, the handler method is run instead of the requested user interface. The handler method should simulate the user interaction for the test case, such as validating messages, making selections, or entering values. You declare a handler type attribute on the method. For more information about handler methods, see [Create Handler Methods](../devenv-creating-handler-methods.md).

## Example

```AL
[Test]
[HandlerFunctions('SendNotificationHandler,MessageHandler')]
procedure MyTestFunction();
begin
    ...
end
```

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)