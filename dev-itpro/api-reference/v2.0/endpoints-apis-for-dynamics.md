---
title: "Endpoints for the APIs for Microsoft Dynamics NAV and Microsoft Dynamics 365 Business Central"
description: "Describing the steps you must go through to enable access to the APIs in on-prem and cloud product versions."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 01/08/2024
ms.reviewer: na
ms.topic: article
ms.assetid: a0ac492d-e3c8-4a76-87b4-b469e08c58e7
ms.author: solsen
---

# Endpoints for the APIs for Dynamics 365 Business Central On-Premises and Online

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

[!INCLUDE[prod_short](../../includes/prod_short.md)] on-premises and online expose an API that makes it possible to integrate with other services. To enable integration with these APIs, you must go through a few steps to enable the access first. For more information about these steps, see [Enabling APIs for Dynamics 365 Business Central](enabling-apis-for-dynamics-nav.md).

## Accessing the endpoints

Once you have the API access enabled, you can write code that integrates your web service or SaaS solution with [!INCLUDE[prod_short](../../includes/prod_short.md)]. Creating your integration through an API provides simple access to the supported functionality in a single endpoint, giving you a simplified experience for creating a single app with integrations across multiple Microsoft products.

> [!IMPORTANT]  
> With the introduction of multiple [!INCLUDE[prod_short](../../includes/prod_short.md)] environments, the name of the environment being connected to needs to go into the URI.  To learn how to get a list of environments deployed on the tenant, see [Getting a List of Environments](../../webservices/api-get-environments.md).

### [!INCLUDE[prod_short](../../includes/prod_short.md)]

|**Means of connection**|**Microsoft Graph**|**Common endpoint service**|**Direct tenant**|
|--|--|--|--|
|**Usage**|Production|Production|Production|
|**Endpoint**|`https://`<br>`graph.microsoft.com`<br>`/beta/financials/`| `https://`<br>`api.businesscentral.dynamics.com/`<br> `v2.0/<environment name>/api/v2.0`  <br><br>  Example:<br> `https://`<br>`api.businesscentral.dynamics.com/`<br> `v2.0/production/api/v2.0` |`https://`<br>`api.businesscentral.dynamics.com/`<br>`v2.0/<user domain name>/<environment name>/api/v2.0`<br><br> Example:<br> `https://`<br>`api.businesscentral.dynamics.com/`<br> `v2.0/cronus.com/sandbox/api/v2.0`|
|**Availability**|Always enabled|Always enabled|Always enabled|
|**Authentication**|Microsoft Entra ID<br>|Microsoft Entra ID<br>|Microsoft Entra ID<br>|
|**API/Data access**|Based on user's<br> [permissions](../../developer/devenv-permissions-on-database-objects.md)|Based on user's<br> [permissions](../../developer/devenv-permissions-on-database-objects.md)|Based on user's<br> [permissions](../../developer/devenv-permissions-on-database-objects.md)|
|**API update cycle**|Monthly|Monthly|Monthly|
|**Development instance**|Sign up for a [tenant](https://go.microsoft.com/fwlink/?linkid=847861)|Sign up for a [tenant](https://go.microsoft.com/fwlink/?linkid=847861)|Sign up for a [tenant](https://go.microsoft.com/fwlink/?linkid=847861)|

### [!INCLUDE[prod_short](../../includes/prod_short.md)] On-Prem

|**Means of connection**|**Direct installation**|
|-----------------------|-----------------------|
|**Usage**|Production|
|**Endpoint**|OData base URL in installation: <br> `https://`<br>`<base URL>:<port>/<serverInstance>/api/<API version>/` <br> Example: `https://`<br>`nav.contoso.com:7048/`<br>`bc/api/v2.0` <br> Must be exposed through a firewall.<br><br>Extension APIs:<br>`https://<base URL>:<port>/<serverinstance>/api/<API publisher>/<API group>/<API version>`|
|**Availability**|Disabled by default.<br> Must be enabled by the administrator.|
|**Authentication**|Basic authentication.<br> Username and [web service<br> access key](../../developer/devenv-develop-connect-apps.md) as password. Your solution must be configured to use **NavUserPassword** or **AccessControlService** authentication in order to configure Dynamics NAV user accounts to include an access key.|
|**API/Data access**|Based on user's<br> [permissions](../../developer/devenv-permissions-on-database-objects.md)|
|**API update cycle**|Hotfixes installed by partner|
|**Development instance**|Get [Docker](https://aka.ms/navdeveloperpreview) instance|

## Which IP addresses or ranges does my environment's API use?

When you exchange data through the API, you might have to safelist the IP addresses. 

For more information, see [FAQ: IP addresses or ranges for the Business Central service](../../faq.yml#which-ip-addresses-or-ranges-does-my-environment-s-api-use)


## See Also

[Developing Connect Apps for Dynamics 365 Business Central](../../developer/devenv-develop-connect-apps.md)  
[Microsoft Web Services Overview](../../webservices/web-services.md)  
[OpenAPI Specification](dynamics-open-api.md)  
