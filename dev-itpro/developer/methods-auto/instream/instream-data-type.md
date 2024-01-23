---
title: "InStream Data Type"
description: "Is a generic stream object that you can use to read from or write to files and BLOBs."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# InStream Data Type
> **Version**: _Available or changed with runtime version 1.0._

Is a generic stream object that you can use to read from or write to files and BLOBs. You can define the internal structure of a stream as a flat stream of bytes. You can assign one stream to another. Reading from and writing to a stream occurs sequentially.



## Instance methods
The following methods are available on instances of the InStream data type.

|Method name|Description|
|-----------|-----------|
|[EOS()](instream-eos-method.md)|Indicates whether an input stream has reached End of Stream (EOS).|
|[Length()](instream-length-method.md)|Gets the stream length.|
|[Position([BigInteger])](instream-position-method.md)|Get or set the current stream position in seekable streams.|
|[Read(var Boolean [, Integer])](instream-read-boolean-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Byte [, Integer])](instream-read-byte-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Char [, Integer])](instream-read-char-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Integer [, Integer])](instream-read-integer-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var BigInteger [, Integer])](instream-read-biginteger-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Decimal [, Integer])](instream-read-decimal-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Guid [, Integer])](instream-read-guid-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Text [, Integer])](instream-read-string-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[Read(var Any [, Integer])](instream-read-joker-integer-method.md)|Reads a specified number of bytes from an InStream object. Data is read in binary format.|
|[ReadText(var Text [, Integer])](instream-readtext-method.md)|Reads text from an InStream object.|
|[ResetPosition()](instream-resetposition-method.md)|Resets the stream position on an InStream object.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  