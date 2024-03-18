---
title: "Calling External Web Services"
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
ms.assetid: ef7ae394-7cae-4eb4-a9a4-75b39ca1a2b6
caps.latest.revision: 4
---
# Calling External Web Services
In [!INCLUDE[prod_short](../developer/includes/prod_short.md)], you can use the Windows Communication Foundation, which provides a set of reliable objects for calling web services to use with .NET Framework interoperability.  
  
## Example  
 The following code example uses a proxy web service class and calls a `Read` method from the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web service. To set up this example, you expose page 42 as a web service in the **Web Service** table and then generate and compile the proxy class. For more information, see [Working with Web Services](/previous-versions/dynamicsnav-2016/dd355036(v=nav.90)) in the MSDN Library.  
  
 The example requires the following variables.  
  
|Variable name|DataType|SubType|Length|  
|-------------------|--------------|-------------|------------|  
|navBinding|DotNet|'System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.System.ServiceModel.BasicHttpBinding||  
|address|text||256|  
|salesOrderService|DotNet|'SalesOrderService, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.NAV.SalesOrderService.SalesOrder\_PortClient||  
|endpointAddress|DotNet|'System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.System.ServiceModel.EndpointAddress||  
|salesOrder|DotNet|'SalesOrderService, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.NAV.SalesOrderService.SalesOrder||  
  
```  
navBinding := navBinding.BasicHttpBinding;  
  
// Set security mode to BasicHttpSecurityMode.TransportCredentialOnly  
navBinding.Security.Mode := 4;   
address :=   
    'https://localhost:7047/DynamicsNAV70/WS/CRONUS%20International%20Ltd./Page/SalesOrder';  
  
// Set client credential type to HttpClientCredentialType.Windows  
navBinding.Security.Transport.ClientCredentialType := 4;  
salesOrderService := salesOrderService.SalesOrder_PortClient(navBinding,  
    endpointAddress.EndpointAddress(address);  
  
// Set impersonation level to System.Security.Principal.TokenImpersonationLevel.Delegation  
salesOrderService.ClientCredentials.Windows.AllowedImpersonationLevel := 4;  
  
// Include the sales order ID to be read.  
salesOrder := salesOrderService.Read('10000');  
  
```
## See Also  
 [Basic Page Operations](Basic-Page-Operations.md)
