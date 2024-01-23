---
title: Interfaces in AL
description: Interfaces in AL are syntactical contracts that can be implemented by a non-abstract method.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 02/24/2023
ms.reviewer: na
ms.topic: conceptual
ms.author: solsen
ms.collection: get-started
---

# Interfaces in AL

[!INCLUDE[2020_releasewave1](../includes/2020_releasewave1.md)]

An interface in AL is similar to an interface in any other programming language; it's a syntactical contract that can be implemented by a non-abstract method. The interface is used to define which capabilities must be available for an object, while allowing actual implementations to differ, as long as they comply with the defined interface.

This allows for writing code that reduces the dependency on implementation details, makes it easier to reuse code, and supports a polymorphic way of calling object methods, which again can be used for substituting business logic.

The interface declares an interface name along with its methods, and codeunits that implement the interface methods, must use the `implements` keyword along with the interface name(s). The interface itself doesn't contain any code, only signatures, and can't itself be called from code, but must be implemented by other objects.
 
The AL compiler checks to ensure that implementations adhere to assigned interfaces.

You can declare variables as a given interface to allow passing objects that implement the interface, and then call interface implementations on the passed object in a polymorphic manner.

> [!NOTE]  
> With [!INCLUDE [prod_short](includes/prod_short.md)] 2023 release wave 1, you can use the **Go to Implementations** option in the Visual Studio Code context menu (or press <kbd>Ctrl+F12</kbd>) on an interface to view all the implementations within scope for that interface. This is supported on interfaces, and on codeunits and enums, which implement an interface, as well as on their procedures if they map to a procedure on an interface. It's also supported on codeunit variables of type interface to jump to other implementations of that specific interface.

## Snippet support

Typing the shortcut `tinterface` creates the basic layout for an interface object when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.


## Interface example

The following example defines an interface `IAddressProvider`, which has one method `getAddress` with a certain signature. The codeunits `CompanyAddressProvider` and `PrivateAddressProvider` both implement the `IAddressProvider` interface, and each define a different implementation of the `getAddress` method; in this case a simple variation of address value.

The `MyAddressPage` is a simple page with an action that captures the choice of address and calls, based on that choice, an implementation of the `IAddressProvider` interface.

```AL
interface "IAddressProvider"
{
    procedure GetAddress(): Text
}

codeunit 50200 CompanyAddressProvider implements IAddressProvider
{

    procedure GetAddress(): Text;
    var
        ExampleAddressLbl: Label 'Company address \ Denmark 2800';
        
    begin
        exit(ExampleAddressLbl);
    end;
}

codeunit 50201 PrivateAddressProvider implements IAddressProvider
{

    procedure GetAddress(): Text;
    var
        ExampleAddressLbl: Label 'My Home address \ Denmark 2800';

    begin
        exit(ExampleAddressLbl);
    end;
}

enum 50200 SendTo implements IAddressProvider
{
    Extensible = true;

    value(0; Company)
    {
        Implementation = IAddressProvider = CompanyAddressProvider;
    }

    value(1; Private)
    {
        Implementation = IAddressProvider = PrivateAddressProvider;
    }
}

page 50200 MyAddressPage
{
    PageType = Card;
    ApplicationArea = All;
    UsageCategory = Administration;

    layout
    {
        area(Content)
        {
            group(MyGroup)
            {
            }
        }
    }

    actions
    {
        area(Processing)
        {
            action(GetAddress)
            {
                ApplicationArea = All;

                trigger OnAction()
                var
                    AddressProvider: Interface IAddressProvider;
                begin
                    AddressproviderFactory(AddressProvider);
                    Message(AddressProvider.GetAddress());
                end;
            }

            action(SendToHome)
            {
                ApplicationArea = All;

                trigger OnAction()
                begin
                    sendTo := sendTo::Private;
                end;
            }

            action(SendToWork)
            {
                ApplicationArea = All;

                trigger OnAction()
                begin
                    sendTo := sendTo::Company;
                end;
            }
        }
    }

    local procedure AddressproviderFactory(var iAddressProvider: Interface IAddressProvider)
    begin
        iAddressProvider := sendTo;
    end;

    var
        sendTo: enum SendTo;
}
```

## See Also

[Codeunit Object](devenv-codeunit-object.md)  
[Extensible Enums](devenv-extensible-enums.md)  
