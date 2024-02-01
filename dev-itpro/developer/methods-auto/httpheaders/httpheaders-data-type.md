---
title: "HttpHeaders Data Type"
description: "Is a collection of headers and their values."
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
# HttpHeaders Data Type
> **Version**: _Available or changed with runtime version 1.0._

Is a collection of headers and their values.



## Instance methods
The following methods are available on instances of the HttpHeaders data type.

|Method name|Description|
|-----------|-----------|
|[Add(Text, Text)](httpheaders-add-string-string-method.md)|Adds the specified header and its value into the HttpHeaders collection. Validates the provided value.|
|[Add(Text, SecretText)](httpheaders-add-string-secrettext-method.md)|Adds the specified secret header and its value into the HttpHeaders collection. Validates the provided value.|
|[Clear()](httpheaders-clear-method.md)|Sets the HttpHeaders variable to the default value.|
|[Contains(Text)](httpheaders-contains-method.md)|Checks if the specified header exists in the HttpHeaders collection.|
|[ContainsSecret(Text)](httpheaders-containssecret-method.md)|Returns if the header for the given key has a secret value.|
|[GetSecretValues(Text, Array of [SecretText])](httpheaders-getsecretvalues-string-secrettext-method.md)|Gets the secret values for the specified key.|
|[GetSecretValues(Text, List of [SecretText])](httpheaders-getsecretvalues-string-list[secrettext]-method.md)|Gets the secret values for the specified key.|
|[GetValues(Text, Array of [Text])](httpheaders-getvalues-string-text-method.md)|Gets the values for the specified key.|
|[GetValues(Text, List of [Text])](httpheaders-getvalues-string-list[text]-method.md)|Gets the values for the specified key.|
|[Keys()](httpheaders-keys-method.md)|Gets the key name of all the headers|
|[Remove(Text)](httpheaders-remove-method.md)|Removes the specified header from the HttpHeaders collection.|
|[TryAddWithoutValidation(Text, Text)](httpheaders-tryaddwithoutvalidation-string-string-method.md)|Adds the specified header and its value into the HttpHeaders collection. Doesn't validate the provided value.|
|[TryAddWithoutValidation(Text, SecretText)](httpheaders-tryaddwithoutvalidation-string-secrettext-method.md)|Adds the specified secret header and its value into the HttpHeaders collection. Doesn't validate the provided value.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  