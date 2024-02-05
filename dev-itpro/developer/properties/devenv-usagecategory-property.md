---
title: "UsageCategory Property"
description: "Sets the department column for a searched page, report, or query in the web client."
ms.author: solsen
ms.custom: na
ms.date: 09/06/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# UsageCategory Property
> **Version**: _Available or changed with runtime version 12.0._

Sets the department column for a searched page, report, or query in the web client.

## Applies to
-   Query
-   Page
-   Report

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**None**|runtime version 1.0|The page, report or query is not included in a search.|
|**Lists**|runtime version 1.0|The page, report or query is listed as **Lists** under the **Pages and Tasks** category.|
|**Tasks**|runtime version 1.0|The page, report or query is listed as **Tasks** under the **Pages and Tasks** category.|
|**ReportsAndAnalysis**|runtime version 1.0|The page, report or query is listed as **Reports and Analysis** under the **Reports and Analysis** category.|
|**Documents**|runtime version 1.0|The page, report or query is listed as **Documents** under the **Reports and Analysis** category.|
|**History**|runtime version 1.0|The page, report or query is listed as **Archive** under the **Reports and Analysis** category.|
|**Administration**|runtime version 1.0|The query is listed as **Administration** under the **Pages and Tasks** category.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks

If the **UsageCategory** is set to **None**, or if you don't specify **UsageCategory**:

- The page or report won't show up when you use the search functionality.  
- Users won't be able to bookmark a link to the page or report object from the user interface.

The **UsageCategory** is also used to categorize pages and reports shown in the role explorer of the client. The role explorer includes two actions: **Reports and Analysis** and **Administration**. Pages and reports set to **ReportsAndAnalysis** will show when the **Reports and Analysis** action is selected. Pages and reports set to **Administration** will show when the **Administration** action is selected. For more information, see [Finding Pages with the Role Explorer](/dynamics365/business-central/ui-role-explorer).

## Syntax

```AL
UsageCategory = ReportsAndAnalysis;  
```

## Dependent Properties

The [AccessByPermission property](devenv-accessbypermission-property.md) and [ApplicationArea Property](devenv-applicationarea-property.md) are optional properties, which can be applied to set restrictions on an object accessibility, when you add the **UsageCategory** property. 

## See Also

[Add pages and reports to Tell me](../devenv-al-menusuite-functionality.md)  
[Properties](devenv-properties.md)  
[Page Object](../devenv-page-object.md)  
[Report Object](../devenv-report-object.md)  
