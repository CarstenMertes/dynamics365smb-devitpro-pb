---
title: "SOAP Web Service URIs"
description: Explains how SOAP URIs looks for on-premises Business Central installations.
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
---
# SOAP Web Service URIs

Web service users can discover published web services by pointing a browser or a tool such as the Web Services Discovery Tool at the computer running [!INCLUDE[server](../developer/includes/server.md)] and getting a list of available services. For SOAP web services, you typically enter a URI in a browser to view a list of available [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web services or to view a schema for a particular web service.  

[!INCLUDE[on-prem-ws-off-405-note](../includes/include-on-prem-ws-off-405-note.md)]

[!INCLUDE[soap_deprecation](../includes/soap_deprecation_note.md)]

## URIs for SOAP Web Services (for on-premises)
To display all published SOAP web services that are exposed by a [!INCLUDE[server](../developer/includes/server.md)] instance, use a URI of the following type:  
  
```  
https://<Server>:<Port>/<ServerInstance>/WS/<CompanyName>/services  
```  
  
 The following example displays all published SOAP web services that are exposed for the [!INCLUDE[demolong](../developer/includes/demolong_md.md)].  
  
```  
https://localhost:7047/BC130/WS/CRONUS%20International%20Ltd/services  
```  
  
 To view the schema for a particular service, use a URI of the following type:  
  
```  
https://<Server>:<Port>/<ServerInstance>/WS/<CompanyName>/Page/<servicename>  
```  
  
 The following example displays the schema for the Customer service for the [!INCLUDE[demolong](../developer/includes/demolong_md.md)].  
  
```  
https://localhost:7047/BC130/WS/CRONUS%20International%20Ltd/Page/Customer  
```  
  
You can also use a URI for a codeunit web service, as shown in the following example:  
  
```  
https://localhost:7047/BC130/WS/CRONUS%20International%20Ltd/Codeunit/Letters  
```  
  
## See Also  

[Web service performance](web-service-performance.md)   
[Troubleshoot web service errors](web-service-troubleshooting.md)   
[Web service telemetry](web-service-telemetry.md)   
[SOAP Web Services](soap-web-services.md)  