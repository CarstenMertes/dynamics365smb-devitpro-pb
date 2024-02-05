---
title: "DataItemTableView Property"
description: "Sets the key on which to sort, the sort order, and the filters for the data item."
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
# DataItemTableView Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the key on which to sort, the sort order, and the filters for the data item.

## Applies to
-   Report Data Item

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Examples

In the following example, the **DataItemView** property is used to sort a table view based on the `"Entry No."` field.

```AL
DataItemTableView = SORTING ("Entry No.");
```

This code sample shows how the same property can be used to apply filters on a table view.

```AL
DataItemTableView = WHERE("Document Type" = FILTER(Payment | Invoice | "Credit Memo"), Open= CONST(true));
```
  
## Remarks  

- If you set a key, then the data item does not have a FastTab on the request page and the end users cannot select a key for sorting, sort order, or filters for the data item.  
  
- If you set a sort order, then this sort order is used for the report, regardless of the sort order that the end user selects on the request page.  
  
- If you set a filter, then this filter is not displayed on the request page but it is used along with any filters that the end user specifies on the request page.  
  
- Setting a sort order, a filter, or both does not prevent end users from selecting a sort field on the request page. The default sort field that is displayed in the request page is the primary key. The list of fields on which you can sort includes all keys for the data item. To add fields to the list, you must add keys to the table.

## See Also

[Request Pages](../devenv-request-pages.md)