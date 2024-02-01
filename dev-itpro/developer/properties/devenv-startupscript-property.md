---
title: "StartupScript Property"
description: "Specifies the script which is invoked when web page with the control add-in is loaded."
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
# StartupScript Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the script which is invoked when web page with the control add-in is loaded.

## Applies to
-   Control Add In

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Values

A path to a single script file. The default is blank, with no script being specified. 

## Remarks 

This property is typically JavaScript representing the main body of the control add-in. The script is invoked when the page that hosts the control add-in has loaded and after other scripts referenced by the [Scripts](devenv-scripts-property.md) property have loaded. 
Although this property is optional, the control add-in must either specify the StartupScript property or specify one or more scripts.
The script is embedded within the extension and must be added to the extension project folder in Visual Studio Code and referenced using a relative path. 

## Example

```AL
StartupScript = 'js/chart.js';
```

## See Also

[Properties](devenv-properties.md)   
[Control Add-In Object](../devenv-control-addin-object.md)   