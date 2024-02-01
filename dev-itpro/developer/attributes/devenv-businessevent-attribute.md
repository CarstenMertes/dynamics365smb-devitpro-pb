---
title: "BusinessEvent Attribute"
description: "Specifies that the method is published as a business type event."
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

# BusinessEvent Attribute
> **Version**: _Available or changed with runtime version 1.0._

Specifies that the method is published as a business type event.


## Applies To

- Method


## Syntax

```AL
[BusinessEvent(IncludeSender: Boolean [, Isolated: Boolean])]
```

### Arguments
*IncludeSender*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
Specifies that the firing instance of the object is available as a parameter to subscribers of that event.  

*[Optional] Isolated*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
Specifies if event subscribers should be invoked in an isolated transaction.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Snippet support
Typing the shortcut `teventbus` will create the basic BusinessEvent attribute syntax when using the [!INCLUDE[d365al_ext_md](../../includes/d365al_ext_md.md)] in Visual Studio Code.

## Remarks
For more information about the different event types, see [Event Types](../devenv-event-types.md).

When you set the *IncludeSender* argument to **true**, the signature of event subscriber methods that subscribe to the published event automatically include a VAR parameter for the published event object, as shown in the following example:

```AL
codeunit 50100 MyPublishingCodeunit
{
    [BusinessEvent(true)]
    procedure MyBusinessEvent()
    begin
    end;
}

codeunit 50101 MySubscribingCodeunit
{
    [EventSubscriber(ObjectType::Codeunit, Codeunit::MyPublishingCodeunit, 'MyBusinessEvent', '', true, true)]
    local procedure MySubscriber(sender: Codeunit MyPublishingCodeunit)
    begin
        // My subscriber code
    end;
}
```

For more information about isolated events, see [Isolated Events](../devenv-events-isolated.md).

## Example

This example publishes a business type event by using the `OnAddressLineChanged` method. The method takes a single text data type parameter. The IncludeSender argument is set to **false**.

```AL
[BusinessEvent(false)] 
procedure OnAddressLineChanged(line : Text[100]);
begin    
end;
```  

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Events in AL](../devenv-events-in-al.md)  
[Publishing Events](../devenv-publishing-events.md)   
[Raising Events](../devenv-raising-events.md)   
[Subscribing to Events](../devenv-subscribing-to-events.md)   
[Isolated Events](../devenv-events-isolated.md)  
[Method Attributes](devenv-method-attributes.md)