---
title: System requirements for Business Central 2023 release Wave 1
description: This article provides the specifications of minimum hardware and software requirements to install and run Business Central version 22 on-premises.
ms.custom: bap-template
ms.service: dynamics-365-op
ms.topic: overview
ms.date: 02/28/2023
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer
---
# System requirements for Business Central 2023 release wave 1

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

The following sections list the minimum hardware and software requirements to install and run [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises (version 22). **Minimum** means that later versions \(such as SP1, SP2, or R2 versions\) of a required software product are also supported.  

> [!NOTE]  
> [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs some software if it's not already present in the target computer. For more information, see the "Additional Information" section for each component.  

## CLIENT COMPONENTS

## <a name="WebClient"></a> Web client

The following table shows the minimum system requirements for the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web client on-premises.

|Specification|Requirement|
|------|-----|  
|Supported browsers|<ul><li>New Microsoft Edge, latest version</li><li>Google Chrome for Windows, latest version</li><li>Mozilla Firefox for Windows, latest version</li><li>Safari for macOS, latest version</li></ul>Cookies and JavaScript must be enabled in the browser.|
|Additional information|We recommend that you use a stable channel version of a web browser as it's the most reliable and stable version that has undergone extensive testing and bug fixing. This ensures that you have the best experience and are less likely to encounter any issues while using the web client.| 

##  <a name="DynNAVApp"></a> [!INCLUDE[nav_uni_app_md](../developer/includes/nav_uni_app_md.md)]

The following table shows the minimum system requirements for the [!INCLUDE[nav_uni_app](../developer/includes/nav_uni_app_md.md)].  

For the latest information, see the app in the App Store or Google Play.  
[![App Store.](../developer/media/install-mobile-app/appstore.png)](https://go.microsoft.com/fwlink/?LinkId=734847) [![Google Play](../developer/media/install-mobile-app/googleplay.png)](https://go.microsoft.com/fwlink/?LinkId=734849)  

|Specification|Requirement|  
|------|-----|
|[!INCLUDE[nav_uni_app](../developer/includes/nav_uni_app_md.md)] version|<ul><li>3.7 or later</li></ul>|  
|Supported operating systems|<ul><li>Android (tablet and phone): The latest three major versions and their updates.</li><li> iOS (iPad and iPhone): The latest three major versions and their updates.</li></ul>|  
|Additional hardware|<ul><li>1-GB RAM for Android and Windows.</li></ul>|  
|Additional information|<ul><li>Device diagonal screen size 7" for tablets.</li><li>Screen resolution 960 × 510 for tablets.</li><li>Device diagonal screen size 4" for phones.</li><li>Screen resolution 854 x 480 for phones.</li></ul>| 

## <a name="desktop"></a> Business Central desktop app

The following table shows the minimum system requirements for the [Business Central Desktop App](/dynamics365/business-central/install-desktop-app).

|Specification|Requirement|
|------|-----|  
|Supported browsers|<ul><li>New Microsoft Edge, latest version</li><li>Google Chrome for Windows, latest version</li><li>Mozilla Firefox for Windows, latest version</li><li>Safari for macOS, latest version</li></ul>Cookies and JavaScript must be enabled in the browser.|
|Additional information|[!INCLUDE[webserver](../developer/includes/webserver.md)] configured for HTTPS. | 

## <a name="Office"></a> Microsoft Office applications

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises offers various features that require Office apps to be available on client devices. The following table shows the minimum system requirements for the features. 

|Specification|Requirement|  
|------|-----|  
|Excel|<ul><li>Sending data to Excel requires Excel 2019, Excel on the web, or Excel mobile app for iOS or Android&trade;.</li><li>Editing in Excel using the Excel Add-In requires Microsoft Office 2019 or Excel on the web.</li></ul> **IMPORTANT:** Starting with Business Central 2021 release wave 2, the Edit Add-in will only support Excel version 2019 or later.|  
|Word|<ul><li>Microsoft Office 2019, Word for the web, or Word mobile app for iOS or Android&trade;.</li></ul>|
|Outlook|See [Business Inbox in Microsoft Outlook](system-requirements-business-central-v18.md#BusInboxOutlook).|  
|Additional software|<ul><li>A third-party telephony or VoIP app such as Microsoft Teams is required for placing calls from [!INCLUDE[prod_short](../developer/includes/prod_short.md)].|  

## AL development

The following table shows the minimum system requirements for customizing or extending [!INCLUDE[prod_short](../developer/includes/prod_short.md)] using the AL language in Visual Studio Code.

|Specification|Requirement|
|-----|-----|
|Supported operating systems|<ul><li>Windows Server 2022</li><li>Windows Server 2019</li><li>Windows 11</li><li>Windows 10</li></ul>For information about the supported versions and their lifecycles, see [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).|
|Required software|<ul><li>[Visual Studio Code](https://code.visualstudio.com/Download)</li><li>[AL language extension](https://marketplace.visualstudio.com/items?itemName=ms-dynamics-smb.al)</li></ul>|
|Hardware resources|<ul><li>Hard disk space: 500 MB.</li><li>CPU: four cores minimum</li><li>Memory:<br />16 GB for development only. <br />16 GB for developing and locally deploying small extensions (<1000 objects).<br />32-64 GB for developing and locally deploying large extensions (>1000 objects).</li></ul>|
|Reports|<ul><li>For creating and editing RDL report layouts:<ul><li>Report Builder for SQL Server 2019, or</li><li>Visual Studio 2019 with [Microsoft Rdlc Report Designer for Visual Studio](https://go.microsoft.com/fwlink/?linkid=857038) installed.</li></ul></li><li>For creating and editing Word report layouts:<ul><li>Word 2019 or later</li></ul></li></ul>|  

For more information, see [Get Started with AL](../developer/devenv-get-started.md).

## SERVER COMPONENTS

## <a name="NavServerReqs"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] server

The following table shows the minimum system requirements for [!INCLUDE[server](../developer/includes/server.md)].  

|Specification|Requirement|  
|-----|-----|  
|Supported operating systems|<ul><li>Windows 11 Pro, Enterprise, or Education \(64-bit edition\)</li><li>Windows 10 Pro, Enterprise, or Education \(64-bit edition\)</li><li>Windows Server 2022 (Datacenter, Standard)</li><li>Windows Server 2019 (Datacenter, Standard)</li></ul>For information about the supported versions and their lifecycles, see [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).|
|Hardware resources|<ul><li>Hard disk space: 2 GB</li><li>Memory:<br /> 8 GB for running application only<br />16 GB for publishing small extensions (<1000 objects) to server<br />32-64 GB for publishing large extensions (>1000 objects) to server</li>**Note** The memory for publishing extensions is recommended to ensure extensions publish in a reasonable amount of time. Publishing extensions with less memory is possible but it takes longer.</ul>|  
|[!INCLUDE[crm](../developer/includes/crm_md.md)] integration|<ul><li>Windows Identity Foundation.<br />For a list of supported [!INCLUDE[crm](../developer/includes/crm_md.md)] versions, see [Microsoft Dynamics 365 for Sales Integration Requirements](system-requirement-business-central.md#CRM).|  
|Additional software|<ul><li>Microsoft .NET 6.0</li><li>Microsoft .NET Framework 4.8 (required for report rendering and [!INCLUDE[adminshell](../developer/includes/adminshell.md)])</li></ul>.|  
|Additional information|<ul><li>[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer:<ul><li>Microsoft .NET Windows Server Hosting 6.0.15</li><li>Microsoft .NET 6.0</li><li>Microsoft .NET Framework 4.8</li><li>Windows Identity Foundation*.</li><li>Report Builder for SQL Server 2019.<br><br> If Report Builder for SQL Server 2016 is already installed, it is updated to Report Builder for SQL Server 2019.</li></ul></li></ul>|  

\* Starting with update 18.1, Windows Identity Foundation is added to the product by Nuget. It's not installed by Setup.  

## <a name="WebServer"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web server components

|Specification|Requirement|  
|----|----|  
|Supported operating systems|<ul><li>Windows 11 Pro, Enterprise, or Education \(64-bit edition\)</li><li>Windows 10 Pro, Enterprise, or Education \(64-bit edition)</li><li>Windows Server 2022 (Datacenter, Standard)</li><li>Windows Server 2019 (Datacenter, Standard)</li></ul>For information about the supported versions and their lifecycles, see [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).|    
|Web server|<ul><li>Internet Information Services 10.|   
|Additional software|<ul><li>Microsoft .NET 6.0</li></ul>|  
|Additional information|<ul><li>[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer.<ul><li>Microsoft .NET Windows Server Hosting 6.0.15</li><li>Microsoft .NET 6.0</li><li>Internet Information Services 10 is installed with the required features enabled.</li></ul></li><li>For more information about configuring IIS, see [Configuring IIS](configure-iis.md)</li></ul>|  

## <a name="SQLReq"></a>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] database components

The following table shows the minimum system requirements for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database components.  

|Specification|Requirement|  
|----|-----|  
|Hardware resources|For more information, see [Hardware and Software Requirements for Installing SQL Server](https://go.microsoft.com/fwlink/?LinkId=622999). From this page, you can also access requirements for other versions of SQL Server.|  
|Database| Business Central supports database compatibility level 150 and 160 on SQL Server, Azure SQL Database, and Azure SQL Managed Instance. See [ALTER DATABASE (Transact-SQL) Compatibility Level](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-ver15&preserve-view=true) for details on SQL Server Database compatibility levels.<br> Note that if you use nonclustered column store (NCCI) indexes and deploy to Azure SQL Database, then the performance tier most be S3 or higher.|  
|Service Packs and Cumulative Updates| Unless explicitly stated, all released Service Packs and Cumulative Updates of the above Microsoft SQL Server versions are supported. it's recommended to always be on the latest released Service Pack and Cumulative Update.|
|Additional information|[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer:<ul><li>SQL Server 2019 Express \(64-bit edition\).<br>If the operating system on the target computer doesn't support SQL Server 2019 Express, Setup displays a pre-requisite warning. In this case, you should exit Setup. Then, update the operating system on the computer to one that does support SQL Server 2019 Express and run Setup again.<br /><br/>**Note**: With Business Central versions earlier than 20.1, SQL Server 2016 Express is installed</li><li>Report Builder for SQL Server 2019.<br><br> If Report Builder for SQL Server 2016 is already installed, it will be updated to Report Builder for SQL Server 2019.</li></ul>|  

## ADDITIONAL COMPONENTS AND FEATURES

## <a name="ADCS"></a> Automated Data Capture System  

The following table shows the minimum system requirements for Automated Data Capture System \(ADCS\) for [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

|Specification|Requirement|  
|-----|-----|  
|Additional software|<ul><li>MSXML version 6.0.</li><li>Telnet or Microsoft Windows HyperTerminal.</li><li>VT100 Plug-in for each computer on which you install ADCS.</li><li>Microsoft Loopback Adapter.</li></ul>|  
|Additional information|<ul><li>VT100 Plug-in acts as a virtual Telnet server.</li><li>Starting with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1, the VT100 Plug-in for ADCS is no longer included on installation media. You can use VT100 Plug-in from previous releases. However, remember to test that it works properly.</li><li> HyperTerminal is no longer included with Windows.</li></ul>|  

## <a name="BusInboxOutlook"></a>Business inbox in Microsoft Outlook

The following table shows the minimum system requirements for using [!INCLUDE[prod_short](../developer/includes/prod_short.md)] as your business inbox in Outlook.

|Specification|Requirement|  
|-----|-----|
|Supported Outlook Applications |<ul><li>Outlook 2019</li><li>Outlook on the web</li><li>Outlook for iOS</li><li>Outlook for Android&trade;.</li></ul>|
|Supported Exchange Servers|<ul><li>Exchange Online</li><li>Exchange Server 2019<br />In deployments that use Exchange Server, the Exchange PowerShell endpoint must be accessible by [!INCLUDE[server](../developer/includes/server.md)].</li></ul>|
|Supported Authentication|<ul><li>The [!INCLUDE[server](../developer/includes/server.md)] must be configured to run with NavUserPassword or Microsoft Entra authentication.<br /> Also, the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] must be configured for Secure Sockets Layer (SSL).</li></ul>|
|Supported Browsers|<ul><li>When using Outlook on the web, your computer must be running a supported browser listed in the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] Requirements.</li></ul>|
|Supported Operating Systems|<ul><li>When using Outlook for iOS or Outlook for Android&trade;, your mobile device must use a supported operating system that's listed in the [[!INCLUDE[nav_uni_app_md](../developer/includes/nav_uni_app_md.md)]](#DynNAVApp) section.</li></ul>|

> [!IMPORTANT]
> Starting with Business Central 2021 release wave 2, you will no longer be able to sign in to the Business Central add-in from Outlook versions earlier than 2012.  

## <a name="CRM"></a>Microsoft Dataverse and Dynamics 365 for Sales integration

The following table shows the product version requirements for integrating Business Central online and on premise with [!INCLUDE[cds_long_md.md](../developer/includes/cds_long_md.md)] and [!INCLUDE[crm](../developer/includes/crm_md.md)] online and on premises.

|Specification|Requirement|  
|-----|-----|
|[!INCLUDE[cds_long_md.md](../developer/includes/cds_long_md.md)] and [!INCLUDE[crm](../developer/includes/crm_md.md)] online |One the following authentication types:<ul><li> Office365 (legacy)<sup>1</sup></li><li>Office365 (modern, OAuth2 client secret based)<sup>2</sup></li><li>OAuth<sup>3</sup><br><br>For better security, we recommend Office365 (modern, OAuth2 client secret based) instead of OAuth.</li>|
|Dynamics 365 Customer Engagement on-premise<br><br>**Note**: Not supported with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online|<ul><li>Dynamics 365 Customer Engagement version 9.0.2</li><li> One of the following authentication types:<ul><li>AD</li><li>IFD</li><li>OAuth<sup>3</sup></li></ul>|

<sup>1</sup>Effective April 2022, Office365 (legacy) authentication will no longer be supported for Dataverse/Dynamics 365 Sales environments on existing tenants. For more information, see [Important changes (deprecations) coming in Power Apps, Power Automate and customer engagement apps](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-dataverse).

<sup>2</sup> Requires the registration of a third party application in Microsoft Entra ID. For more information, see [To register an application in Microsoft Entra ID for connecting from Business Central to Dataverse](/dynamics365/business-central/admin-how-to-set-up-a-dynamics-crm-connection#to-register-an-application-in-azure-ad-for-connecting-from-business-central-to-dataverse).

<sup>3</sup> AD, IFD, and OAuth types are supported with on-premises version of Dynamics 365 Sales. OAuth and Office 365 (legacy – basic) and Office 365 (modern – MFA) authentication are supported for online versions of Dynamics 365 Sales. For more information about authentication types, see [Connection strings in XRM tooling to connect to Dynamics 365](https://msdn.microsoft.com/library/mt608573.aspx). 

## <a name="SharePointApp"></a>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] as an app for SharePoint

The following table shows the minimum system requirements for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] as an App for SharePoint.  

|Specification|Requirement|  
|-|-|  
|Supported SharePoint servers|<ul><li>SharePoint Server 2019</li><li>SharePoint Online.</li></ul>|  

## See Also

[Welcome to the Developer and IT-Pro Help for Business Central](../index.md)  
[Product and Architecture Overview](product-and-architecture-overview.md)  
[Deployment](Deployment.md)  


[!INCLUDE [footer-banner](../includes/footer-banner.md)]
