---
title: "Publish a Web Service"
description: Explains how to publish page, query, and codeunits as web services.
ms.custom: na
author: jswymer
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
translation.priority.ht: 
  - da-dk
  - de-at
  - de-ch
  - de-de
  - en-au
  - en-ca
  - en-gb
  - en-in
  - en-nz
  - es-es
  - es-mx
  - fi-fi
  - fr-be
  - fr-ca
  - fr-ch
  - fr-fr
  - is-is
  - it-ch
  - it-it
  - nb-no
  - nl-be
  - nl-nl
  - ru-ru
  - sv-se
---

# Publishing a Web Service in Business Central

Users discover web services by pointing a browser at the computer that is running [!INCLUDE[server](../developer/includes/server.md)] and requesting a list of available services. When you publish a web service, it's immediately available over the network for authenticated users. All authorized users have access to metadata for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web services, but only users who have sufficient [!INCLUDE[prod_short](../developer/includes/prod_short.md)] permissions can access actual data.  

Depending on the type of web service (API, OData, or SOAP), the web service might need to be published to be available for users.

## Publishing a API Web Service

If the API stack has been enabled for the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment, then no additional setup is needed to make an API web service available.  

The API stack is enabled by default in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online. For more information on how to enable APIs for on-premises environments, please visit [Enabling the APIs for Dynamics 365 Business Central](../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).  

## Creating and Publishing an OData or SOAP Web Service

You can set up a SOAP or OData based web service in the client. You must then publish the web service so that it's available to service requests over the network. 


The following steps explain how to create and publish a web service.  
  
1. Open the client, such as a browser at [https://businesscentral.dynamics.com/?](https://businesscentral.dynamics.com/?).  
  
2. Choose the ![Lightbulb that opens the Tell Me feature.](../media/search_small.png "Search for Page or Report icon") icon, enter **Web Services**, and then choose the related link.
  
3. In the **Web Services** page, choose **New**.  
  
4. In the **Object Type** column, select **Codeunit**, **Page**, or **Query**.  
  
   > [!NOTE] 
   > **Codeunit** and **Page** are valid types for SOAP web services. 
   > 
   > **Page** and **Query** are valid types for OData web services.  
  
5. In the **Object ID** column, select the object ID of the object that you want to expose. For example, to expose the customer card as a web service, enter **21**.  
  
   If the database contains multiple companies, you can choose an object ID that is specific to one of the companies.  
  
6. In the **Service Name** field, assign a name to the web service. For example, if you expose the customer card as a web service, enter **Customers**.  
  
    - **Codeunit** and **Page** are valid types for SOAP web services. **Page** and **Query** are valid types for OData web services.
    - If the database contains multiple companies, you can choose an object ID that is specific to one of the companies.
    - The service name is visible to consumers of your web service. It's the basis for identifying and distinguishing web services, so you should make the name meaningful.
    - If you're setting up integration with Microsoft Outlook using codeunit 5313, then you must use **DynamicsNAVsynchOutlook** as the service name.  
  
7. Select the check box in the **Published** column.  
  
     When you publish the web service, you see the URLs that are generated for the web service in the **OData URL** and **SOAP URL** fields. You can test the web service immediately by choosing the links in the **OData URL** and **SOAP URL** fields. Optionally, copy the value of the field and save it for later use.  
  
After you publish a web service, it's available on the [!INCLUDE[server](../developer/includes/server.md)] computer that you were connected to when you published. The web service is available across all [!INCLUDE[server](../developer/includes/server.md)] instances running on the server computer.  
  
You can verify the availability of that web service by using a browser. Or choose the link in the **OData URL** and **SOAP URL** fields in the **Web Services** page. The following procedure illustrates how you can verify the availability of the web service for later use.

> [!NOTE]
> For page objects published as OData, there are two extra settings: **Exclude Non-Editable FlowFields** and **Exclude Fields Outside of the Repeater**. These settings exclude non-editable FlowFields and fields outside of the page's repeater control from eTag calculations. Excluding these fields can prevent problems when users edit multiple lines, for example, in Excel. The settings are hidden on the **Web Services** page by default. To show them, use [personalization](/dynamics365/business-central/ui-personalization-user). 
  
## Verify the availability of a web service  
  
1.  In your browser, enter the relevant URL. The following table illustrates the types of URLs that you can enter. For SOAP web services, use the following format for your URI.  
  
    |Web service type|Syntax|Example|  
    |----------------------|------------|-------------|  
    |API| See [Endpoints for the APIs for Dynamics 365 Business Central On-Premises and Online](../api-reference/v2.0/endpoints-apis-for-dynamics.md)| 
    |OData|https://*Server*:*ODataWebServicePort*/*ServerInstance*/OData/Company\('*CompanyName*'\)|https://localhost:7048/[!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]/OData/Company\('CRONUS International Ltd.'\)|  
    |SOAP|https://*Server*:*SOAPWebServicePort*/*ServerInstance*/WS/*CompanyName*/services/|https://localhost:7047/[!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]/WS/CRONUS International Ltd./services/| 

     The company name is case-sensitive.  

  
2.  Review the information that is displayed in the browser. Verify that you can see the name of the web service that you've created.  
  
When you access a web service, and you want to write data back to [!INCLUDE[prod_short](../developer/includes/prod_short.md)], you must specify the company name. You can specify the company as part of the URI as shown in the examples. Or you can specify the company as part of the query parameters. For example, the following URIs point to the same OData web service and are both valid URIs.  
  
```  
https://localhost:7048/<serverinstance>/OData/Company('CRONUS International Ltd.')/Customer  
```  
  
```  
https://localhost:7048/<serverinstance>/OData/Customer?company='CRONUS International Ltd.'  
```  

## Unpublishing an OData or SOAP web service

To unpublish a webs service, clear the **Published** check box. This step will make the web service inaccessible.

> [!IMPORTANT]
> When you unpublish a web service that is marked for **All Tenants**, other web services that use the same object will be automatically unpublished, even though the **Published** check box is still selected for these web services.

## Tips for UI pages exposed as OData or SOAP web services

### Use API pages/queries instead

Avoid using standard UI pages to expose as web service endpoints. Many things, such as fact boxes, aren't returned in web service results, but use resources to prepare. Instead, define and use API pages/queries for your web service integrations. 

For more information, see [Web services performance](web-service-performance.md).

### Need a unique row identifier?

Should you need a unique row identifier in your OData or SOAP web service endpoint, then consider adding the SystemId field to the page. The SystemId field is a GUID data type field that specifies a unique, immutable (read-only) identifier for records in the table. 

For more information, see [System Fields](../developer/devenv-table-system-fields.md).


## See Also

[Web Services](web-services.md)   
[Web Service Publish Failure Telemetry](web-service-telemetry.md#web-service-publish-failure-telemetry)
