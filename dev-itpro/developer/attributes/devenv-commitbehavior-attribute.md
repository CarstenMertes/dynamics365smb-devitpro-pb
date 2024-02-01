---
title: "CommitBehavior Attribute"
description: "Specifies the behavior of a commit call inside the method scope."
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

# CommitBehavior Attribute
> **Version**: _Available or changed with runtime version 6.0._

Specifies the behavior of a commit call inside the method scope.


## Applies To

- Method


## Syntax

```AL
[CommitBehavior(Behavior: CommitBehavior)]
```

### Arguments
*Behavior*  
&emsp;Type: [CommitBehavior](../methods-auto/commitbehavior/commitbehavior-option.md)  
Specifies if a commit must be ignored or throw an error. The options are: Ignored or Error.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks

- It's only possible to assign a more restrictive commit behavior. That is, if `CommitBehavior::Ignore` is attempted on a method scope, but the method calling the current method, for example, the parent method is actually running with `CommitBehavior::Error`, then the current method will continue running with `CommitBehavior::Error`, even though the `Ignore` attribute was specified.

- The `CommitBehavior` only lasts for the method scope. Regardless of whether the method finishes successfully or if an error causes the method to exit prematurely, the `CommitBehavior` reverts to the standard behavior, where `commit` statements will commit to the database.

- The `CommitBehavior` only applies to explicit commits, not implicit commits done as part of [Codeunit.Run](../methods-auto/codeunit/codeunit-run-method.md). 

## Example - local method

The example shown below illustrates how the attribute is used on a local method; it can also be applied on a global method.

```AL
codeunit 50100 MyCodeunit
{
    trigger OnRun()
    var
    begin
        FunctionAllowCommit();
    end;

    local procedure FunctionAllowCommit()
    begin
        FunctionIgnoreCommit();
        commit; // This is valid, and commit call will be executed.
    end;

    [CommitBehavior(CommitBehavior::Ignore)]
    local procedure FunctionIgnoreCommit()
    begin
        TryFunctionErrorCommit();
        commit; // This call will be silently ignored.
    end;

    [CommitBehavior(CommitBehavior::Error)]
    [TryFunction]
    local procedure TryFunctionErrorCommit()
    begin
        commit; // This will throw an error. No further code will be executed and the user will see a dialog to contact the system administrator.
    end;

    var
        myInt: Integer;
}
```

## Example - event subscriber

This example illustrates how you can protect your code from commits happening in event subscriber code; typically written by a third party.

```AL
codeunit 50102 MyPublishingCodeunit
{
    // by stating CommitBehavior::Ignore here, any subscribers attempt to commit will be ignored
    [CommitBehavior(CommitBehavior::Ignore)]
    [IntegrationEvent(true, false)]
    procedure OnSomethingChangedEvent()
    begin
        // this part of ImportantAtomicOperation is extensible
    end;

    procedure Validate() result: Boolean
    begin
        // validation code 
    end;

    procedure DoImportantAtomicOperation()
    begin
        // do work
        OnSomethingChangedEvent();
        // do more work

        if Validate() then Commit() else Error('Validation failed');
    end;

}

codeunit 50103 MySubscribingCodeunit
{
    [EventSubscriber(ObjectType::Codeunit, Codeunit::MyPublishingCodeunit, 'OnSomethingChangedEvent', '', true, true)]
    local procedure SubcribeToOnAddressLineChangedEvent(sender: Codeunit MyPublishingCodeunit)
    begin
        // subscriber code
        Commit();
    end;

```

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  