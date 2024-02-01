---
title: "Installing Business Central in a Two Computer Environment"
description: Explains how to deploy Business Central on two computers.
ms.custom: na
ms.date: 10/13/2021
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---
# Deploying [!INCLUDE[prodsshort](../developer/includes/prod_short.md)] in a Two-Computer Topology

This article covers two deployment scenarios:

- Scenario 1

  You install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)] and [!INCLUDE[server](../developer/includes/server.md)] on a computer separate from the SQL Server database components. 

  > [!TIP]
  > For simplicity and performance advantages, we recommend this scenario.

  ![Installation on two computers with server and web server on one computer and the database on another.](../media/two-computer-topology-1.png "Installation on two computers with server and web server on one computer and the database on another")  

- Scenario 2

  You install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)] on a separate computer than [!INCLUDE[server](../developer/includes/server.md)] and the SQL Server database components.  

  ![Installation on two computers with server and database on one computer and the web server on another.](../media/two-computer-topology-2.png "Installation on two computers with server and database on one computer and the web server on another")  

<!--
> [!TIP]  
>  For a step-by-step example that describes how to deploy this scenario, see [Walkthrough: Installing the Microsoft Dynamics NAV Web Server Components on Two Computers](Walkthrough--Installing-the-Microsoft-Dynamics-NAV-Web-Server-Components-on-Two-Computers.md).
--> 

Many of the deployment tasks for both scenario are the same. The main difference is in the **Installation Tasks** section. 

## Pre-Installation Tasks

The following table includes tasks to do before you install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)].  

|Task|[!INCLUDE[bp_tabledescription](../developer/includes/bp_tabledescription_md.md)]|For more information, see...|  
|----------|---------------------------------------|-------------------------------|  
|Make sure that system requirements are met.|Verify that the computer has the required hardware and software installed.|[System Requirements](system-requirement-business-central.md)|  
|Install Internet Information Services.|When you install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)], [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] creates a website for the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] on IIS. If IIS is already installed, then make sure that the required features are enabled.<br /><br/>**Note:** This step is optional because instead of installing and configuring IIS manually, you can use [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] to install IIS and enable the required features by setting the **Install IIS Prerequisites** option to **Yes**.|[Configure Internet Information Services](configure-iis.md)|
|Determine the TCP ports for the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)], client services, and SOAP/OData web services (optional) and allow communication on the port through Windows Firewall.|[!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] creates a website on IIS. During Setup, you'll have to choose the port to use for the site. The default port is port 8080.<br /><br />The default client services port is 7085 (7046 in version 20 and earlier).<br /><br />If you'll enable SOAP and OData web services, you'll also need to specify a port for each. The default ports are 7047 and 7048.<br /><br />If you choose to do so, [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] will automatically create an inbound rule in Windows Firewall that allows communication on the ports. Otherwise, you'll have to do this manually.|[Identity and access management](/windows/security/identity-protection) in the Windows documentation.|  
|Set up the service account for [!INCLUDE[server](../developer/includes/server.md)] and the SQL Server database.|Optional. When you install [!INCLUDE[server](../developer/includes/server.md)], you can specify a user account that will be used to log on to the [!INCLUDE[server](../developer/includes/server.md)] instance and [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database. The default service account is Network Service. If you want to use Network Service, then no action is required for this task.|[Provisioning a Service Account](provision-server-account.md)|  
|Obtain and install an SSL certificate.|Optional. If you want to configure SSL on the connection to [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)], then complete the following procedures:<br /><br /> -   Obtain an SSL certificate.<br />-   Import the certificate into the local computer store of the computer on which you'll install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)].<br />-   Obtain the certificate's thumbprint.<br /><br />**Note:**  You can also configure SSL after you've installed the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)]. For more information, see [Post-installation Tasks](deploy-two-computer-environment.md#PostInstall).|[Configure SSL to Secure the Web Client Connection](configure-ssl-web-client-connection.md)|  

## Installation Tasks

See the section that matches your deployment scenario. Each section contains a table with the tasks specific to the scenario.  

### Scenario 1

|Task|Description|For more information, see...|  
|----------|-----------------|-------------------------------|  
|On one computer, install SQL Server Database Components.|Run the [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] setup.exe file, choose **Advanced installation options** > **Choose an installation option** > **Custom**, and then choose the **SQL Server Database Components** option.|[Install Business Central Using Setup](install-using-setup.md)| 
|Start the SQL Server Browser Service on the SQL Server computer.|This task is only required if you're using a named database instance for [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. By default, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] uses the database instance named BCDEMO. The SQL Server Browser Service is required so that the database instance can be discovered by the [!INCLUDE[server](../developer/includes/server.md)] instance, which in this scenario, is another computer. To start the SQL Server, use SQL Server Configuration Manager.|[Start, Stop, Pause, Resume, Restart SQL Server Services](/sql/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services)| 
|On the other computer, install the [!INCLUDE[server](../developer/includes/server.md)] and [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)] .|Run [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)], choose **Advanced installation options** > **Choose an installation option** > **Custom**, and then the **Server** and **Web Server Components** options.|[Install Business Central Using Setup](install-using-setup.md)<br /><br /> [Business Central Web Server Overview](web-server-overview.md)|  

### Scenario 2

|Task|Description|For more information, see...|  
|----------|-----------------|-------------------------------|  
|On one computer, install [!INCLUDE[server](../developer/includes/server.md)] and SQL Server Database Components.|Run the [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] setup.exe file, choose **Advanced installation options** > **Choose an installation option** > **Custom**, and then choose the **Server** and **SQL Server Database Components** options.|[Install Business Central Using Setup](install-using-setup.md)| 
|On the other computer, install the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)].|Run [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)], choose **Advanced installation options** > **Choose an installation option** > **Custom**, and then the **Web Server Components** option.|[Install Business Central Using Setup](install-using-setup.md)<br /><br /> [Business Central Web Server Overview](web-server-overview.md)|  
|Configure delegation from the web server to [!INCLUDE[server](../developer/includes/server.md)].|Because [!INCLUDE[server](../developer/includes/server.md)] is running on a different computer than the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)], you must configure the computer that is running [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)] to delegate its access to [!INCLUDE[server](../developer/includes/server.md)] on behalf of the device trying to access from the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)].|[Configure Delegation for Business Central Web Server](configure-delegation-web-server.md)|  

##  <a name="PostInstall"></a> Post-installation Tasks  
 The following table includes tasks to configure the [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)] after installation. These tasks are optional depending on your organizational and network requirements.  

|Task|Description|For more information, see|  
|----------|-----------------|-------------------------------|  
|Change the user authentication method.|The [!INCLUDE[prod_short](../developer/includes/prod_short.md)] supports the following authentication methods: Windows, UserName, NavUserPassword, and AccessControlService. By default, Windows authentication is used.|[Authentication and User Credential Type](../administration/users-credential-types.md)|
|Secure the connection to the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] with SSL.|You can help secure [!INCLUDE[prod_short](../developer/includes/prod_short.md)] data that is transmitted over the Internet by enabling Secure Sockets Layer \(SSL\) on the connection to the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)].|[Configure SSL to Secure the Web Client Connection](configure-ssl-web-client-connection.md)|   
|Change the configuration of the [!INCLUDE[webserver](../developer/includes/webserver.md)].|There are several parameters in the [navsettings.json configuration file](../administration/configure-web-server.md#WebClientSettingsFile) for the [!INCLUDE[webserver](../developer/includes/webserver.md)] that you can modify to change the behavior of the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)]. Some of the more common parameters include the [!INCLUDE[server](../developer/includes/server.md)] instance, company, language, time zone, regional settings, session time-out, and online Help URL.|[Configuring Business Central Web Server](../administration/configure-web-server.md)|
|Set up multiple [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] applications on a website.|You can set up multiple web server instances for the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] on the existing website. The web server instances will use the same address \(URL\) except with an alias that specifies the specific application.|[Creating and Managing [!INCLUDE[webserver](../developer/includes/webserver.md)] Instances Using PowerShell](configure-multiple-web-server-instances.md)|  
|Configure web browsers on devices.|The [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] supports several different web browsers. To access the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)], the web browser must be enabled on a device with cookies and JavaScript.|[Web Client Requirements](system-requirement-business-central.md#WebClient)|  

## See Also  
 [Business Central Web Server Overview](web-server-overview.md)   
 [Installing Business Central in a Single Computer Environment](deploy-single-computer-environment.md)   
 [Installing Business Central in a Three Computer Environment](deploy-three-computer-environment.md)
