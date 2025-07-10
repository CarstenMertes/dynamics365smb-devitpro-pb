---
title: (v1.0) Enabling APIs for Microsoft Dynamics NAV
description: (v1.0) Describing the steps you must go through to enable access to the APIs.
author: SusanneWindfeldPedersen
ms.custom: evergreen
ms.date: 05/01/2024
ms.update-cycle: 1095-days
ms.topic: how-to
ms.author: solsen
ms.reviewer: solsen
---

# Enabling the APIs for Dynamics 365 Business Central (v1.0)

[!INCLUDE[prod_short](../../includes/prod_short.md)] exposes an API that makes it possible to integrate with other services. To enable integration with these APIs, you must go through a few steps to enable the access for [!INCLUDE[prod_short](../../includes/prod_short.md)].

> [!IMPORTANT]  
> REST programming is not natively supported in C/SIDE. In order to run the APIs you must add the REST dependent types manually. Existing W1 objects can compile and load, but some .NET types cannot be loaded into the C/SIDE Development environment variable editor due to missing server dependencies.

## Enable access to the APIs

1. Open the [Business Central Administration tool](../../administration/administration-tool.md).
1. Expand the **OData Services** tab, and select the **Enable OData Services** checkbox first, then select the **Enable API Services** checkbox.
1. Check that the values for the **OData Base URL** and **Port** are entered correctly.  
    When exposing a web service, you must open the port for other consumers of your web service to access it. You can have your system administrator add the port through Windows Firewall on the computer running [!INCLUDE[prod_short](../../includes/prod_short.md)] server. The default port for OData web services is 7048.
1. In [!INCLUDE[prod_short](../../includes/prod_short.md)], search for **API Setup** and then choose the related link.
1. On the **API Setup** page, choose the **Integrate APIs** button.  
    This will start a process of populating all the integration tables with records for all APIs. The process can take several minutes.

Depending on where you want to access the APIs from, you must specify the correct endpoint. For more information, see [Endpoints for APIs](endpoints-apis-for-dynamics.md).

[!INCLUDE[on-prem-ws-off-405-note](../../includes/include-on-prem-ws-off-405-note.md)]

## Related information

[Developing connect apps for Dynamics 365 Business Central](../../developer/devenv-develop-connect-apps.md)  
[Microsoft web services overview](../../webservices/web-services.md)  
[OpenAPI specification](dynamics-open-api.md)  
