---
title: System Requirements for Business Central 2020 Release Wave 1
description: This article provides the specifications of minimum hardware and software requirements to install and run Business Central 2020 Release Wave 1 on-premises.
ms.custom: na
ms.topic: conceptual
ms.date: 04/01/2021
author: jswymer
---
# System Requirements for [!INCLUDE[prod_long](../developer/includes/prod_long.md)] 2020 Release Wave 1

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

The following sections list the minimum hardware and software requirements to use or connect to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online, and to install and run [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises (version 16). **Minimum** means that later versions \(such as SP1, SP2, or R2 versions\) of a required software product are also supported.  

> [!NOTE]  
>  [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs some software if it's not already present in the target computer. For more information, see the "Additional Information" section for each component.  

## Client Components

###  <a name="WebClient"></a> Web Client Requirements  
 The following table shows the minimum system requirements for the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web client on-premises.  

|Specification|Requirement|  
|------|-----|  
|Supported browsers|Recommended browsers:<ul><li>New Microsoft Edge for Windows</li><li>Google Chrome for Windows (81.0 or later)</li><li>Mozilla Firefox for Windows (75.0  or later)</li><li>Safari for macOS (75.0 or later)</li></ul>Other supported browsers:<ul><li>Internet Explorer 11</li><li>Microsoft Edge Legacy</li></ul>Cookies and JavaScript must be enabled in the browser.|
|Business inbox in Outlook|<ul><li>Microsoft 365, Microsoft Office 2019, or Microsoft Office 2016.</li></ul>|  
|Sending data to Excel|<ul><li>Microsoft 365, Microsoft Office 2019, or Microsoft Office 2016.</li></ul>|  
|Editing in Excel using the Excel Add-in |<ul><li>Excel 2019, Excel 2016, or Excel Online.<br /><br />For more information, see [Exporting Your Business Data to Excel](/dynamics365/business-central/about-export-data).</li></ul>|  
|SharePoint Online links|<ul><li>Microsoft Office 2019, Microsoft Office 2016, or Microsoft 365.</li></ul>|  
|Printing reports to Excel or Word|<ul><li>Microsoft Office 2019, Microsoft Office 2016, or Microsoft 365.</li></ul>|  
|Additional information|If you experience problems using the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)], you can try to turn off browser tools, such as translator tools that may run in the background.|  

###  <a name="NavApps"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Tablet Client and Phone Client \(in a Browser\) Requirements  
 The following table shows the minimum system requirements for the [!INCLUDE[nav_tablet](../developer/includes/nav_tablet_md.md)] and [!INCLUDE[nav_phone](../developer/includes/nav_phone_md.md)] running in a desktop browser when used for development and testing purposes.  

|Specification|Requirement|
|------|-----|  
|Server component|Identical to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web client.|  
|Supported browsers|Identical to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web client.|  

###  <a name="DynNAVApp"></a> [!INCLUDE[nav_uni_app_md](../developer/includes/nav_uni_app_md.md)] Requirements  
 The following table shows the minimum system requirements for the [!INCLUDE[nav_uni_app](../developer/includes/nav_uni_app_md.md)].  

For the latest information, see the app in the Windows Store, App Store, or Google Play.  
[![Windows Store.](../developer/media/install-mobile-app/windowsstore.png)](https://go.microsoft.com/fwlink/?LinkId=734848)
[![App Store.](../developer/media/install-mobile-app/appstore.png)](https://go.microsoft.com/fwlink/?LinkId=734847) [![Google Play](../developer/media/install-mobile-app/googleplay.png)](https://go.microsoft.com/fwlink/?LinkId=734849)  

|Specification|Requirement|
|------|-----|  
|Supported operating systems|<ul><li>Windows 10 S, Home, Pro, Enterprise, or Education \(32-bit and 64-bit editions\).</li><li>Android (tablet and phone): The latest three major versions and their updates.</li><li> iOS (iPad and iPhone): The latest three major versions and their updates.</li></ul>|  
|Additional hardware|<ul><li>1-GB RAM for Android and Windows.</li></ul>|  
|Additional software|<ul><li>A third-party telephony or VoIP app such as Skype is required for placing calls from [!INCLUDE[prod_short](../developer/includes/prod_short.md)].</li><li>A third-party email program such as Outlook is required for sending emails from [!INCLUDE[prod_short](../developer/includes/prod_short.md)].</li><li>Microsoft Office 2019, Office 2016, or Microsoft 365 is required for sending data to Microsoft Excel or to Microsoft Word.</li></ul>|  
|Additional information|<ul><li>Device diagonal screen size 7" for tablets.</li><li>Screen resolution 960 × 510 for tablets.</li><li>Device diagonal screen size 4" for phones.</li><li>Screen resolution 854 x 480 for phones.</li></ul>|  

### AL Development Requirements

The following table shows the minimum system requirements for customizing or extending [!INCLUDE[prod_short](../developer/includes/prod_short.md)] using the AL language in Visual Studio Code.

|Specification|Requirement|
|-----|-----|
|Supported operating systems|<ul><li>Windows Server 2019</li><li>Windows Server, version 1809 or later</li><li>Window Server 2016.</li><li>Windows 10 - [supported versions](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</ul></li>|
|Required software|<ul><li>[Visual Studio Code](https://code.visualstudio.com/Download)</li><li>[AL language extension](https://marketplace.visualstudio.com/items?itemName=ms-dynamics-smb.al)</li></ul>|
|Hardware resources|<ul><li>Hard disk space: 500 MB.</li><li>CPU: four cores minimum</li><li>Memory:<br />16 GB for development only. <br />16 GB for developing and locally deploying small extensions (<1000 objects).<br />32-64 GB for developing and locally deploying large extensions (>1000 objects).</li></ul>| 
|Reports|<ul><li>For creating and editing RDL report layouts:<ul><li>Report Builder for SQL Server 2016 or later, or</li><li>Visual Studio 2017 with [Microsoft Rdlc Report Designer for Visual Studio](https://go.microsoft.com/fwlink/?linkid=857038) installed.</li></ul></li><li>For creating and editing Word report layouts:<ul><li>Word 2016 or later</li></ul></li></ul>|  

For more information, see [Get Started with AL](../developer/devenv-get-started.md).

## Server Components

###  <a name="NavServerReqs"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Server Requirements

 The following table shows the minimum system requirements for [!INCLUDE[server](../developer/includes/server.md)].  

|Specification|Requirement|
|-----|-----|  
|Supported operating systems|<ul><li>Windows 10 Pro, Enterprise, or Education \(64-bit edition\).</li><li>Windows Server 2019 (Datacenter, Standard)</li><li>Windows Server, version 1809 or later (Datacenter, Standard)</li><li>Windows Server 2016 Standard, Essentials, or Datacenter.</li></ul>|  
|Hardware resources|<ul><li>Hard disk space: 2 GB</li><li>Memory:<br /> 8 GB for running application only<br />16 GB recommended for publishing small extensions (<1000 objects) to server<br />32-64 GB recommended for publishing large extensions (>1000 objects) to server</li>**Note** The memory for publishing extensions is recommended to ensure extensions publish in a reasonable amount of time. Publishing extensions with less memory is possible but it will take longer.</ul>|  
|[!INCLUDE[crm](../developer/includes/crm_md.md)] integration|<ul><li>Windows Identity Foundation.<br />For a list of supported [!INCLUDE[crm](../developer/includes/crm_md.md)] versions, see [Microsoft Dynamics 365 for Sales Integration Requirements](system-requirement-business-central.md#CRM).|  
|Additional software|<ul><li>Microsoft .NET Framework 4.8</li><li>Windows PowerShell 4.0.|  
|Additional information|<ul><li>[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer:<ul><li>Microsoft .NET Framework 4.8</li><li>Windows Identity Foundation*.</li><li>Report Builder for SQL Server 2016 (update 16.12 and earlier). Report Builder 15.0 for SQL Server 2019 (update 16.13 and later)<br><br> With an update 16.13 and later installation, if Report Builder for SQL Server 2016 is already installed, it will be updated to Report Builder 15.0.</li></ul></li></ul>|  

\* Starting with update 16.13, Windows Identity Foundation is added to the product by Nuget. It's not installed by Setup.  

###  <a name="WebServer"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web Server Components Requirements  

|Specification|Requirement|
|----|----|  
|Supported operating systems|<ul><li>Windows 10 Pro, Enterprise, or Education \(64-bit edition\).</li><li>Windows Server 2019 (Datacenter, Standard)</li><li>Windows Server, version 1809 or later (Datacenter, Standard)</li><li>Windows Server 2016 Standard, Essentials, or Datacenter.</li></ul>.|  
|Web server|<ul><li>Internet Information Server 10, Internet Information Server 8.5, or Internet Information Server 8.0.|   
|Additional software|<ul><li>Microsoft .NET Framework 4.8</li><li>Windows PowerShell 4.0.|  
|Additional information|<ul><li>[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer.<ul><li>Microsoft .NET Core 1.0 Windows Server Hosting. This software is installed by [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] if not already present.</li><li>Microsoft .NET Framework 4.8</li><li>Internet Information Server 10, Internet Information Server 8.5, or Internet Information Server 8.0. The version depends on the operating system. Internet Information Server is installed with the required features enabled.</li></ul></li><li>For more information about configuring IIS, see [Configuring IIS](configure-iis.md)</li></ul>|  

###  <a name="SQLReq"></a>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Database Components for SQL Server Requirements  
 The following table shows the minimum system requirements for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database components for SQL Server.  

|Specification|Requirement|
|----|-----|  
|Supported operating systems|<ul><li>Windows 10 Pro, Enterprise, or Education \(64-bit edition\).</li><li>Windows Server 2019 (Datacenter, Standard)</li><li>Windows Server, version 1809 or later (Datacenter, Standard)</li><li>Windows Server 2016 Standard, Essentials, or Datacenter.</li></ul> |  
|Hardware resources|For more information, see [Hardware and Software Requirements for Installing SQL Server](/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server). From this page, you can also access requirements for other versions of SQL Server.|  
|SQL Server|<ul><li>Microsoft SQL Server 2019 Express, Standard, or Enterprise.</li> <li>Microsoft SQL Server 2017 Express, Standard, or Enterprise.</li> <li>Microsoft SQL Server 2016 Express, Standard, or Enterprise (Service Pack 1 or later).</li><li>Azure SQL Database Managed Instance, Elastic Pool, or Single Database.</li></ul>|  
|Service Packs and Cumulative Updates| Unless explicitly stated, all released Service Packs and Cumulative Updates of the above Microsoft SQL Server versions are supported. it's recommended to always be on the latest released Service Pack and Cumulative Update.|
|Additional information|[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer:<ul><li>SQL Server 2016 Express \(64-bit edition\).<br>If the operating system on the target computer doesn't support SQL Server 2016 Express, Setup displays a pre-requisite warning. In this case, you should exit Setup. Then, update the operating system on the computer to one that does support SQL Server 2016 Express and run Setup again.</li><li>Report Builder for SQL Server 2016 (update 16.12 and earlier). Report Builder 15.0 for SQL Server 2019 (update 16.13 and later)<br><br> With an update 16.13 and later installation, if Report Builder for SQL Server 2016 is already installed, it will be updated to Report Builder 15.0.</li></ul>|  

###  <a name="HelpServer"></a> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Help Server Requirements  
 The following table shows the minimum system requirements for the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Help Server.  

|Specification|Requirement|
|-----|-----|  
|Supported operating systems|<ul><li>Windows 10 Pro, Enterprise, or Education \(64-bit editions\).</li><li>Windows Server 2019 (Datacenter, Standard)</li><li>Windows Server, version 1809 or later (Datacenter, Standard)</li><li>Windows Server 2016 Standard, Essentials, or Datacenter.</li></ul>|  
|Hardware resource|<ul><li>Hard disk space: 500 MB.</li><li>Memory: 2 GB.</li></ul>|  
|Web server|<ul><li>Internet Information Server 10, Internet Information Server 8.5, or Internet Information Server 8.0.</li></ul>|  
|Additional software|<ul><li>Microsoft .NET Framework 4.8</li></ul>|  
|Additional information|<ul><li>[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] installs the following software if it's not already present on the target computer.<ul><li>Microsoft .NET Framework 4.8</li><li>Internet Information Server 10, Internet Information Server 8.5, or Internet Information Server 8.0. The version depends on the operating system. it's installed with the required features enabled.</li></ul></li><li>Windows Search must be enabled on the computer that you install the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Help Server on.</li></ul>|  

## Additional Components and Features

###  <a name="ADCS"></a> Automated Data Capture System Requirements  

The following table shows the minimum system requirements for Automated Data Capture System \(ADCS\) for [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

|Specification|Requirement|
|-----|-----|  
|Additional software|<ul><li>MSXML version 6.0.</li><li>Telnet or Microsoft Windows HyperTerminal.</li><li>VT100 Plug-in for each computer on which you install ADCS.</li><li>Microsoft Loopback Adapter.</li></ul>|  
|Additional information|<ul><li>HyperTerminal is no longer included with Windows. For more information, see [What happened to HyperTerminal?](https://go.microsoft.com/fwlink/?LinkId=222571) in the Windows Help.</li><li>VT100 Plug-in acts as a virtual Telnet server. </li></ul>| 

> [!NOTE]
> Starting with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1, the VT100 Plug-in for ADCS is no longer included on installation media. You can use VT100 Plug-in from previous releases. However, remember to test that it works properly. 

###  <a name="BusInboxOutlook"></a> Business Inbox in Microsoft Outlook Requirements  
The following table shows the minimum system requirements for using [!INCLUDE[prod_short](../developer/includes/prod_short.md)] as your business inbox in Outlook.

|Specification|Requirement|
|-----|-----|
|Supported Outlook Applications |<ul><li>Outlook 2016 or later</li><li>Outlook Web App</li><li>Outlook Web App for iPad</li><li>Outlook Web App for iPhone</li><li> Outlook Web App for Android.</li></ul>|
|Supported Exchange Servers|<ul><li>Exchange Online</li><li>Exchange Server 2019</li><li>Exchange Server 2016<br />In deployments that use Exchange Server, the Exchange PowerShell endpoint must be accessible by [!INCLUDE[server](../developer/includes/server.md)].</li></ul>|
|Supported Authentication|<ul><li>The [!INCLUDE[server](../developer/includes/server.md)] must be configured to run with NavUserPassword, ACS, or Microsoft Entra credentials type.<br /> Also, the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] must be configured for Secure Sockets Layer (SSL).</li></ul>|
|Supported Browsers|<ul><li>When using the Outlook Web App (Microsoft Outlook Web App), your computer must be running a supported browser listed in the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] Requirements.</li></ul>|
|Supported Operating Systems|<ul><li>When using Outlook Web App for iPad, iPad, or Android, your mobile device must use a supported Operating System listed in [!INCLUDE[nav_uni_app_md](../developer/includes/nav_uni_app_md.md)] Requirements.</li></ul>|  

###  <a name="Outlook"></a> Microsoft Outlook Add-In Requirements  
The following table shows the minimum system requirements for the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Add-In for Outlook for synchronization with Outlook.

|Specification|Requirement|  
|-----|-----|  
|Supported Outlook Applications |<ul><li>Outlook 2019</li><li>Outlook 2016</li></ul>|
|Supported Exchange Servers|<ul><li>Exchange Server 2019</li><li>Exchange Server 2016</li><li>Exchange Online.</li></ul>|  

### <a name="CRM"></a>Microsoft Dataverse and Dynamics 365 for Sales Integration

The following table shows the product version requirements for integrating Business Central online and on premise with [!INCLUDE[cds_long_md.md](../developer/includes/cds_long_md.md)] and [!INCLUDE[crm](../developer/includes/crm_md.md)] online and on premises.

|Specification|Requirement|  
|-----|-----|
|[!INCLUDE[cds_long_md.md](../developer/includes/cds_long_md.md)] and [!INCLUDE[crm](../developer/includes/crm_md.md)] online |One the following authentication types:<ul><li> Office365 (legacy)<sup>1</sup></li><li>Office365 (modern, OAuth2 client secret based)<sup>2</sup>- only supported with version 16.2 and later</li><li>OAuth<sup>3</sup><br><br>For better security, we recommend Office365 (modern, OAuth2 client secret based) instead of OAuth.</li>|
|Dynamics 365 Customer Engagement on-premise<br><br>**Note**: Not supported with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online|<ul><li>Dynamics 365 Customer Engagement version 9.0.2</li><li> One of the following authentication types:<ul><li>AD</li><li>IFD</li><li>OAuth<sup>3</sup></li></ul>|

<sup>1</sup>Effective April 2022, Office365 (legacy) authentication will no longer be supported for Dataverse/Dynamics 365 Sales environments on existing tenants. For more information, see [Important changes (deprecations) coming in Power Apps, Power Automate and customer engagement apps](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-dataverse).

<sup>2</sup> Requires the registration of a third party application in Microsoft Entra ID. For more information, see [To register an application in Microsoft Entra ID for connecting from Business Central to Dataverse](/dynamics365/business-central/admin-how-to-set-up-a-dynamics-crm-connection#to-register-an-application-in-azure-ad-for-connecting-from-business-central-to-dataverse).

<sup>3</sup> AD, IFD, and OAuth types are supported with on-premises version of Dynamics 365 Sales. OAuth and Office 365 (legacy – basic) and Office 365 (modern – MFA) authentication are supported for online versions of Dynamics 365 Sales. For more information about authentication types, see [Connection strings in XRM tooling to connect to Dynamics 365](/previous-versions/dynamicscrm-2016/developers-guide/mt608573(v=crm.8)). 

###  <a name="SharePointApp"></a>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] as an App for SharePoint Requirements  
The following table shows the minimum system requirements for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] as an App for SharePoint.  

|Specification|Requirement|  
|-|-|  
|Supported operating systems|<ul><li>Windows Server 2019 Standard, Essentials, or Datacenter.</li><li>Windows Server 2016 Standard, Essentials, or Datacenter.</li></ul>|  
|Additional software|<ul><li>SharePoint 2013 Service Pack 1.</li><li>SharePoint Online.</li></ul>|  

## See Also

[Welcome to the Developer and IT-Pro Help for Business Central](../index.md)  
[Product and Architecture Overview](product-and-architecture-overview.md)  
[Deployment](Deployment.md)