---
title: "System.ImportStreamWithUrlAccess(InStream, Text [, Integer]) Method"
description: "Imports an object into a media container to be used in a temporary URL with a default expiration time."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# System.ImportStreamWithUrlAccess(InStream, Text [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Imports an object into a media container to be used in a temporary URL with a default expiration time.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
ID :=   System.ImportStreamWithUrlAccess(InStream: InStream, Filename: Text [, MinutesToExpire: Integer])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*InStream*  
&emsp;Type: [InStream](../instream/instream-data-type.md)  
Input stream that contains the object to store as a media object.  

*Filename*  
&emsp;Type: [Text](../text/text-data-type.md)  
File name to associate with the created media object.  

*[Optional] MinutesToExpire*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Number of minutes after which the object will expire.  


## Return Value
*ID*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The ID of the media container, if the import is successful.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)