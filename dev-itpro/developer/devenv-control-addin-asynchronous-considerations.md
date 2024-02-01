---
title: "Asynchronous considerations for control add-ins"
ms.custom: na
ms.date: 12/29/2023
ms.reviewer: na
ms.topic: conceptual
ms.assetid: 6c90376e-b86e-406d-880d-3cc905bf6527
author: SusanneWindfeldPedersen
description: Learn about asynchronous communication limitations in Dynamics 365 Business Central server and how to effectively write control add-ins for all display targets.
---

# Asynchronous considerations
When writing control add-ins that work on all display targets, you have to consider some limitations regarding asynchronous communication. The limitations come from the nature of the asynchronous communication between the clients and the [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] server. All calls between the AL code running on the [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] server and the script method running in the Web browser are asynchronous. This means that methods in the control add-in interface must be of type void and property methods shouldn't be used.  
  
- To transfer a result from an AL trigger to the calling script method, just add a method to the control add-in interface that the AL trigger can invoke to send the result to the script.  
  
- To transfer a result from a script method to an AL trigger, just add an event to the control add-in interface that the script method can use to invoke an AL trigger that receives the result.  


<!--
The methods from the "See Also" section are not auto-generated as they come from the .NET assemblies in the platform. When the old methods folder will be deprecated, remember to not remove these methods. 
-->
  
## See also  

[InvokeExtensibilityMethod Method](methods/devenv-invokeextensibility-method.md)   
[GetImageResource Method](methods/devenv-getimageresource-method.md)  
[GetEnvironment Method](methods/devenv-getenvironment-method.md)    
[Control Add-in Best Practices](devenv-control-addin-bestpractices.md)    
[OpenWindow Method](methods/devenv-openwindow-method.md)  
