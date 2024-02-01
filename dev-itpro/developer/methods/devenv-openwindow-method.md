---
title: "OpenWindow Method"
description: "The OpenWindow method in control add-in for Business Central"
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
author: solsen
---

# OpenWindow Method
Opens a new browser window which navigates to the specified URL. The benefit of using this function instead of using the native browser function, is that this function also works when using the control add-in in an app, for example on a phone. If you are using the native browser function in an app, the behavior varies between the different platforms (Windows, iOS, Android).

## Method signature  
`void Microsoft.Dynamics.NAV.OpenWindow(url)`  
  
## Parameters  
  
|Parameter|Description|  
|---------|-----------|  
|url      |Type: String <br /><br /> A string that contains the URL for the new browser window to navigate to.|  
  
  
## See Also

[AL Method Reference](../methods-auto/library.md)  
[GetEnvironment Method](devenv-getenvironment-method.md)  
[GetImageResource Method](devenv-getimageresource-method.md)   
[InvokeExtensibilityMethod Method](devenv-invokeextensibility-method.md)   
[Asynchronous Considerations](../devenv-control-addin-asynchronous-considerations.md)