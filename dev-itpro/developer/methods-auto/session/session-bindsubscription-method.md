---
title: "Session.BindSubscription(Codeunit) Method"
description: "Binds the event subscriber methods in the codeunit to the current codeunit instance for handling the events that they subscribe to."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Session.BindSubscription(Codeunit) Method
> **Version**: _Available or changed with runtime version 1.0._

Binds the event subscriber methods in the codeunit to the current codeunit instance for handling the events that they subscribe to. This essentially activates the subscriber functions for the codeunit instance.


## Syntax
```AL
[Ok := ]  Session.BindSubscription(Codeunit: Codeunit)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Codeunit*  
&emsp;Type: [Codeunit](../codeunit/codeunit-data-type.md)  
The codeunit that contains the event subscribers.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the event subscriber methods bind successfully to the codeunit instance and no errors occurred, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 You can only call this method on codeunits that have the [EventSubscriberInstance Property](../../properties/devenv-eventsubscriberinstance-property.md) set to **Manual**.  
  
The codeunit instance that event subscribers are bound to will be this exact instance. Events will be raised on this instance. You can't bind the same instance more than once, but you can bind multiple instances of the same codeunit. This condition will result in an event subscriber call on each bound instance when a given event is raised.  
  
## Example  
 
The following sample code illustrates a typical use of the BindSubscription method.  
  
```al
procedure MyFunction()
var  
    Subscriber: Codeunit Subscriber;  
begin
    // Set global information on the subscriber codeunit if required  
    // You can rely on the instance being the same as the one receiving the event subscriber call  
  
    Subscriber.MySetGlobalInfo(123); //info you can later test in the subscriber event method
    BindSubscription(Subscriber);  
    DoSomething();  // After binding, all subscriptions on Subscriber are "active".  
end; // Notice, that when Subscriber goes out of scope, all bindings are removed.  
  
```  
  

## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
