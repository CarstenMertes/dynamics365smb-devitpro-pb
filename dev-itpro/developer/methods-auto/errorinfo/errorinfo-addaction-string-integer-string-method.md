---
title: "ErrorInfo.AddAction(Text, Integer, Text) Method"
description: "Specifies an action for the error."
ms.author: solsen
ms.custom: na
ms.date: 08/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ErrorInfo.AddAction(Text, Integer, Text) Method
> **Version**: _Available or changed with runtime version 11.0._

Specifies an action for the error.


## Syntax
```AL
 ErrorInfo.AddAction(Caption: Text, CodeunitID: Integer, MethodName: Text)
```
## Parameters
*ErrorInfo*  
&emsp;Type: [ErrorInfo](errorinfo-data-type.md)  
An instance of the [ErrorInfo](errorinfo-data-type.md) data type.  

*Caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text string that appears as the caption of the action in the error UI. The string can be a label that is enabled for multilanguage functionality.  

*CodeunitID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the Codeunit to run when the action is initiated from the error UI. The codeunit should contain at least one global method to be called by the error action. The global method must have an ErrorInfo data type parameter for accepting the ErrorInfo object.  

*MethodName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the method in the Codeunit, which is specified by the CodeunitID parameter, that you want to run for the action.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The **AddAction** method accepts four parameters:

- **Caption**, which is the text string that appears as the caption of the action in the error UI.
- **CodeunitID**, which is the ID of the codeunit to run when the action is initiated from the error UI. The codeunit should contain at least one global method to be called by the error action. The global method must have an ErrorInfo data type parameter for accepting the ErrorInfo object.
- **Method Name**, which is the name of the method in the codeunit specified by the CodeunitID parameter, that you want to run for the action.
- **Tooltip**, which is the text string that appears as the tooltip of the action in the error UI.

If you call `ErrorInfo.AddAction` and codeunit exists with the provided *CodeunitID* or no method called *MethodName* exists in that codeunit, then a runtime error occurs.

If possible, call `ErrorInfo.AddAction` using Codeunit::CodeunitName and not the literal integer for the object ID of the codeunit. If there is a renumbering of the codeunit or if the codeunit was removed, then you get a compile-time error and not a runtime error.

## Example

In the following example from the [!INCLUDE[prod_short](../../../includes/prod_short.md)] base app, you can see how an error message can be annotated with actions that the user can do to get unblocked.

```AL
 procedure PreventModifyRecIfOpenApprovalEntryExistForCurrentUser(Variant: Variant)
    var
        WorkflowWebhookMgt: Codeunit "Workflow Webhook Management";
        RecRef: RecordRef;
        ErrInfo: ErrorInfo;
        RejectApprovalRequestLbl: Label 'Reject approval';
        ShowCommentsLbl: Label 'Show comments';
        RejectApprovalRequestToolTipLbl: Label 'Reject approval request';
        ShowCommentsToolTipLbl: Label 'Show approval comments';
    begin
        RecRef.GetTable(Variant);
        if HasOpenApprovalEntriesForCurrentUser(RecRef.RecordId) or WorkflowWebhookMgt.HasPendingWorkflowWebhookEntryByRecordId(RecRef.RecordId) then begin
            ErrInfo.ErrorType(ErrorType::Client);
            ErrInfo.Verbosity(Verbosity::Error);
            ErrInfo.Message(PreventModifyRecordWithOpenApprovalEntryMsg);
            ErrInfo.TableId(RecRef.Number);
            ErrInfo.RecordId(RecRef.RecordId);
            ErrInfo.AddAction(RejectApprovalRequestLbl, Codeunit::"Approvals Mgmt.", 'RejectApprovalRequest', RejectApprovalRequestToolTipLbl);
            ErrInfo.AddAction(ShowCommentsLbl, Codeunit::"Approvals Mgmt.", 'ShowApprovalCommentLinesForJournal', ShowCommentsToolTipLbl);
            Error(ErrInfo);
        end;
    end;
```

To see a different code example with an error dialog with a Fix-it action, see [Error messages with Show-it actions](../../devenv-actionable-errors.md#show-it-actions).

## See Also

[ErrorInfo Data Type](errorinfo-data-type.md)  
[Actionable errors](../../devenv-actionable-errors.md)  
[Error handling](../../devenv-al-error-handling.md)   
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)