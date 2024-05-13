---
title: Web Service Telemetry
description: Learn about how Business Central emits telemetry about web service requests
author: KennieNP
ms.custom: bap-template
ms.reviewer: jswymer

ms.topic: conceptual
ms.author: kepontop
ms.date: 06/13/2023
---

# Web Service Telemetry 

All calls to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web services are logged to partner telemetry. Telemetry enables you to monitor which endpoints are being used and the category of the web service, like SOAP, OData, or API. You can also see possible failures, which are tracked in the HTTP status codes for the calls.

## Incoming web service telemetry

Web services telemetry gathers data about SOAP, OData, and API requests through the service. It provides information like the request's endpoint, time to complete, the SQL statements run, and more.  

[!INCLUDE[who_is_calling](../includes/include-webservices-telemetry-who-is-calling.md)]

For more information, go to [Analyzing Incoming Web Services Request Telemetry](../administration/telemetry-webservices-trace.md).

## Web service access key telemetry

The [!INCLUDE[prod_short](../developer/includes/prod_short.md)] emits telemetry data about the success or failure of authenticating web service access keys on web service requests.

[!INCLUDE[webservice_key_deprecated](../includes/web-service-key-deprecated.md)]

As a partner or customer, this data lets you monitor the use of web service access keys on your environments in preparation for the deprecation of the feature.

For more information, go to [Analyzing Web Service Access Key Telemetry](../administration/telemetry-webservices-access-key-trace.md).

## Web service publish failure telemetry

If a web service couldn't be published or a published web service isn't working, most often it's due to an error in creating metadata for the web service. All metadata creation failures along with stack trace of the element responsible for breaking web service metadata are available in partner telemetry. 

For more information, go to [Analyzing Web Service Publish Failure Telemetry](../administration/telemetry-webservices-publish-failure-trace.md).

## See also

[Web Services Overview](web-services.md)  
[Web Services Best Practices](Web-Services-Best-Practices.md)  
[Analyzing Incoming Web Services Request Telemetry](../administration/telemetry-webservices-trace.md)  
[Analyzing Web Service Access Key Telemetry](../administration/telemetry-webservices-access-key-trace.md)  
[Configuring Business Central Server](../administration/configure-server-instance.md)  
