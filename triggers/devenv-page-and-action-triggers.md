---
title: "Page and Action Triggers"
description: "Page and action triggers in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Page and Action Triggers

Page triggers allow you to use AL code to control the behavior of the system as a result of an event on the page, such as a page opening or a field changing its value. You typically use page triggers for advanced validation and logic.  

 Page triggers can be divided into three categories:  

- General page triggers that apply to the entire page  

- Field page triggers that apply to a field control on a page  

- Action triggers that apply to an action on a page.  

> [!IMPORTANT]  
> If you define two methods that have the same name, one defined in a page and the other in a table that is referenced by the page, you cannot invoke the method defined in the page directly. By default, a call to the method invokes the method that is defined in the table. This behavior occurs when the method is called from a source expression or a trigger.  

## General Triggers

The following table lists triggers that apply to the entire page.  

|Page trigger name|Runs|  
|-----------------------|--------------|  
|[OnInit Trigger](triggers-auto/page/devenv-oninit-page-trigger.md)|When the page is loaded, but before the controls are available.|  
|[OnOpenPage Trigger](triggers-auto/page/devenv-onopenpage-page-trigger.md)|When the page is initialized and the controls are available.|  
|[OnClosePage Trigger](triggers-auto/page/devenv-onclosepage-page-trigger.md)|When the page about to close and after [OnQueryClosePage Trigger](triggers-auto/page/devenv-onqueryclosepage-page-trigger.md) trigger.|  
|[OnFindRecord Trigger](triggers-auto/page/devenv-onfindrecord-page-trigger.md)|When the page is opened and a record is retrieved from a table.|  
|[OnNextRecord Trigger](triggers-auto/page/devenv-onnextrecord-page-Trigger.md)|When the page changes from displaying one record to another record in a table. For example, on a Customer card page, this happens when a user selects **Next** (Ctrl+Page Down) or **Previous** (Ctrl+Page Up).|  
|[OnAfterGetCurrRecord Trigger](triggers-auto/page/devenv-onaftergetcurrrecord-page-trigger.md)|After the record has been selected as the current record in the page.| 
|[OnAfterGetRecord Trigger](triggers-auto/page/devenv-onaftergetrecord-page-trigger.md)|When a record has been retrieved but not yet displayed.|  
|[OnNewRecord Trigger](triggers-auto/page/devenv-onnewrecord-page-trigger.md)|When a new record has been initialized but not yet displayed.|  
|[OnInsertRecord Trigger](triggers-auto/page/devenv-oninsertrecord-page-trigger.md)|When a new record is about to be inserted in the table.|  
|[OnModifyRecord Trigger](triggers-auto/page/devenv-onmodifyrecord-page-trigger.md)|When a record is about to be modified in the table.|  
|[OnDeleteRecord Trigger](triggers-auto/page/devenv-ondeleterecord-page-trigger.md)|When a record is about to be deleted from the table.|  
|[OnQueryClosePage Trigger](triggers-auto/page/devenv-onqueryclosepage-page-trigger.md)|When the page is about to close, but before the [OnClosePage Trigger](triggers-auto/page/devenv-onclosepage-page-trigger.md).|  

## Field Triggers

The following table describes the triggers that are available on field controls.  

|Control trigger|Runs|  
|---------------------|--------------|  
|[OnValidate (Page fields) Trigger](triggers-auto/pagefield/devenv-onvalidate-pagefield-trigger.md)|When the user changes the value in a field and then selects away from the field so that the field loses focus.|  
|[OnLookup (Page fields) Trigger](triggers-auto/pagefield/devenv-onlookup-pagefield-trigger.md)|When the user requests a lookup by clicking a field's lookup button or pressing F4.|  
|[OnDrillDown Trigger](triggers-auto/pagefield/devenv-ondrilldown-pagefield-trigger.md)|When the user requests a drill-down by choosing the field's drill-down button or pressing Shift+F8.|  
|[OnAssistEdit Trigger](triggers-auto/pagefield/devenv-onassistedit-pagefield-trigger.md)|When the user requests assist-edit by choosing an AssistEdit button or by pressing Shift+F4.|  

<!--NAV |[OnControlAddin Trigger](devenv-oncontroladdin-trigger.md)|When a control add-in is initiated on a page.| -->

## Action Triggers

The following table lists triggers that apply to actions on a page.  

|Triggers|Runs|  
|--------------|--------------|  
|[OnAction Trigger](triggers-auto/action/devenv-onaction-action-trigger.md)|When an action is initiated on a page.|  


## Page Background Triggers

The following table lists triggers that apply to page background tasks. For more information, see [Page Background Tasks](devenv-page-background-tasks.md).

|Triggers|Runs|
|--------|-----|
|[OnPageBackgroundTaskCompleted](triggers-auto/page/devenv-onpagebackgroundtaskcompleted-page-trigger.md)|Runs after a page background task has successfully completed.|
|[OnPageBackgroundTaskError](triggers-auto/page/devenv-onpagebackgroundtaskerror-page-trigger.md)|Runs when an error occurs in a page background task.|

## See Also

[Triggers](triggers-auto/devenv-triggers.md)
