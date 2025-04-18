---
title: "TableSeparator property"
description: "Specifies the table separator for a table."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TableSeparator Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the table separator for a table.

## Applies to
-   Xml Port

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
TableSeparator = '<NewLine>';
```
  
## Remarks  

**TableSeparator** property is only used if the **Format Property** is set to **Variable Text** or **Fixed Text**. Otherwise, the setting is ignored.  
 
This property specifies how tables should be separated. The default value is (two newlines) \(**\<NewLine>\<NewLine>**\). 

The strings in the preceding table must be entered literally, that is, the **<** and **>** characters must be entered. These special strings can be combined and can be mixed with other characters.  

CR refers to the character with ASCII value 13.  
  
LF refers to the character with ASCII value 10.  
  
You can set the table separator in AL code so that the XMLport can import and export tables with different separators. For example, if your XMLport must import from a file or stream where one table uses a single **NewLine** elements and another uses two **NewLine** elements, you can change the table separator at runtime.  
  
## Related information  

[Properties](devenv-properties.md)  
[XmlPort object](../devenv-xmlport-object.md)  