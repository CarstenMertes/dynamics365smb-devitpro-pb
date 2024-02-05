---
title: "WebServiceActionContext.SetResultCode(WebServiceActionResultCode) Method"
description: "Sets the web service action result status code."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# WebServiceActionContext.SetResultCode(WebServiceActionResultCode) Method
> **Version**: _Available or changed with runtime version 2.0._

Sets the web service action result status code.


## Syntax
```AL
 WebServiceActionContext.SetResultCode(ResultCode: WebServiceActionResultCode)
```
## Parameters
*WebServiceActionContext*  
&emsp;Type: [WebServiceActionContext](webserviceactioncontext-data-type.md)  
An instance of the [WebServiceActionContext](webserviceactioncontext-data-type.md) data type.  

*ResultCode*  
&emsp;Type: [WebServiceActionResultCode](../webserviceactionresultcode/webserviceactionresultcode-option.md)  
The new web service action result status code.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
...
// Set the result code to inform the caller that an item was created.
actionContext.SetResultCode(WebServiceActionResultCode::Created);
...
```
For a complete code example, see [Creating and Interacting with an OData V4 Bound Action](../../devenv-creating-and-interacting-with-odatav4-bound-action.md).

## See Also
[WebServiceActionContext Data Type](webserviceactioncontext-data-type.md)  
[Creating and Interacting with an OData V4 Bound Action](../../devenv-creating-and-interacting-with-odatav4-bound-action.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)