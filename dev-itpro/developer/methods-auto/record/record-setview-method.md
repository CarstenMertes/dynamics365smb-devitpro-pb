---
title: "Record.SetView(Text) Method"
description: "Sets the current sort order, key, and filters on a table."
ms.author: solsen
ms.custom: na
ms.date: 08/11/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.SetView(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the current sort order, key, and filters on a table.


## Syntax
```AL
 Record.SetView(String: Text)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the sort order, key, and filter to set. The string format is the same as the SourceTableView Property on pages.
          



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
The value of the *String* parameter can be returned by the [GetView Method \(Record\)](record-getview-method.md) with the UseNames parameter explicitly set to *false*.

If the SetView method is executed with an empty string, all the filters are removed and the primary key is used.

If no table is selected, the SetView method fails.

This method works the same as the [SetView Method \(RecordRef\)](../recordref/recordref-setview-method.md).           


## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
