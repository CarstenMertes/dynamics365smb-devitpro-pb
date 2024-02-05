---
title: "InStream.Position([BigInteger]) Method"
description: "Get or set the current stream position in seekable streams."
ms.author: solsen
ms.custom: na
ms.date: 02/27/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# InStream.Position([BigInteger]) Method
> **Version**: _Available or changed with runtime version 11.0._

Get or set the current stream position in seekable streams.


## Syntax
```AL
[StreamPosition := ]  InStream.Position([Length: BigInteger])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*InStream*  
&emsp;Type: [InStream](instream-data-type.md)  
An instance of the [InStream](instream-data-type.md) data type.  

*[Optional] Length*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
The stream position to set between 1 and length.  


## Return Value
*[Optional] StreamPosition*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
The current stream position or -1 if the stream is not seekable. The actual position will be a positive number from 1 to length.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

With [!INCLUDE [prod_short](../../includes/prod_short.md)] 2023 release wave 1, the `Position` method allows you to get the position within the current stream. Use the [InStream.Length() Method](instream-length-method.md) to get the position within the current stream.


## See Also
[InStream Data Type](instream-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)