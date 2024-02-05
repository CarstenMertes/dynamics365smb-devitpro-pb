---
title: "Enabling APIs for Microsoft Dynamics NAV"
description: "Describing the steps you must go through to enable access to the APIs."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: article
ms.author: solsen
---

# Enabling the APIs for Dynamics 365 Business Central

[!INCLUDE[on_prem_only_v2](../../developer/includes/on_prem_only_v2.md)]

[!INCLUDE[prod_short](../../includes/prod_short.md)] exposes an API that makes it possible to integrate with other services. To enable integration with these APIs, you must go through a few steps to enable the access for [!INCLUDE[prod_short](../../includes/prod_short.md)].

## Enable access to the APIs

1. Open the [!INCLUDE[adminshell](../../developer/includes/adminshell.md)].

   [!INCLUDE[open-admin-shell](../../developer/includes/open-admin-shell.md)]
1. Run the [Set-NAVServerConfiguration](/powershell/module/microsoft.dynamics.nav.management/set-navserverconfiguration) cmdlet to enable OData services.

   ```powershell
   Set-NAVServerConfiguration <BC server instance name> -KeyName ODataServicesEnabled -KeyValue true
   ```
1. Run the Set-NAVServerConfiguration cmdlet to enable API Services.

   ```powershell
   Set-NAVServerConfiguration <BC server instance name> -KeyName ApiServicesEnabled -KeyValue true
   ```
1. Check that the values for the `PublicODataBaseUrl` and `ODataServicesPort` parameters are correct.  
    When exposing a web service, you must open the port for other consumers of your web service to access it. You can have your system administrator add the port through Windows Firewall on the computer running [!INCLUDE[prod_short](../../includes/prod_short.md)] server. The default port for OData web services is 7048.

   You can verify these settings by running the [Get-NAVServerConfiguration](/powershell/module/microsoft.dynamics.nav.management/get-navserverconfiguration):

   ```powershell
   Get-NAVServerConfiguration <BC server instance name>
   ```
1. In [!INCLUDE[prod_short](../../includes/prod_short.md)], search for **API Setup** and then choose the related link.
1. On the **API Setup** page, choose the **Integrate APIs** button.  
    This will start a process of populating all the integration tables with records for all APIs. The process can take several minutes.

Depending on where you want to access the APIs from, you must specify the correct endpoint. For more information, see [Endpoints for APIs](endpoints-apis-for-dynamics.md).

[!INCLUDE[on-prem-ws-off-405-note](../../includes/include-on-prem-ws-off-405-note.md)]

## See Also

[Developing Connect Apps for Dynamics 365 Business Central](../../developer/devenv-develop-connect-apps.md)  
[Microsoft Web Services Overview](../../webservices/web-services.md)  
[OpenAPI Specification](dynamics-open-api.md)  