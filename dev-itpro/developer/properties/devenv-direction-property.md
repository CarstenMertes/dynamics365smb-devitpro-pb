---
title: "Direction Property"
description: "Sets the XmlPort to import, export, or import and export data in XML format."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Direction Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the XmlPort to import, export, or import and export data in XML format.

## Applies to
-   Xml Port

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Import**|runtime version 1.0|The XMLPort only imports data.|
|**Export**|runtime version 1.0|The XMLPort only exports data.|
|**Both**|runtime version 1.0|The XMLPort can import and export data.<br /><br /> If the XMLPort uses a request page, as specified by the **UseRequestPage Property**, then an option appears on the request page that enables the users to choose to import or export data. This is the default value.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


> [!NOTE]  
> Request pages show when the XMLport is run from an action page or the `Run` method in AL code. Request pages do not show with Export or Import methods<br /><br /> If the XMLPort does not use a request, then XMLPort defaults to **Import**, unless you specify the direction by Import parameter of the `Run` method.|  
 
## Syntax

```AL
Direction = Import;
```

## See Also  

[Properties](devenv-properties.md)