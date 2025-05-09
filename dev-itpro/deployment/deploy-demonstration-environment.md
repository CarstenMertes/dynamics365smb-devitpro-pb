---
title: "Deploying a Business Central Demonstration Environment"
author: jswymer
description: Learn about deploying demos for Business Central on-premises. 
ms.date: 04/01/2021
ms.topic: how-to
---
# Deploying a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Demonstration Environment

This deployment scenario installs the major [!INCLUDE[prod_short](../developer/includes/prod_short.md)] components on a single computer, complete with a base application and database with demonstration data. After the installation, you will have an end-to-end environment, where you can access [!INCLUDE[prod_short](../developer/includes/prod_short.md)] data from the Web client. The installation requires minimal hardware resources, preparation, and configuration.  

## Installed Components and Configuration  

### Components  
 This scenario installs the following components:  

- [!INCLUDE[webservercomponents](../developer/includes/webservercomponents.md)]  

- Internet Information Services

    If IIS is already installed, then the setup will enable any required features that are not currently enabled.

- [!INCLUDE[server](../developer/includes/server.md)]  

- SQL Server Database Components, including [!INCLUDE[demolong](../developer/includes/demolong_md.md)] and demo license.

    For information about what you can do with this license, see [Demonstration License for Business Central On-Premises](../developer/properties/devenv-demolicense-properties.md).  

- [!INCLUDE[adminshell](../developer/includes/adminshell.md)] 

- [!INCLUDE[admintool](../developer/includes/admintool.md)] 

  [!INCLUDE[admin_tool_deprecated](../developer/includes/admin_tool_deprecated.md)] 

- Al Development Environment

### Configuration

This scenario uses the default setting of [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)], which includes the following:  

- [!INCLUDE[webserver](../developer/includes/webservercomponents.md)]
  - Port: 8080 (inbound rule automatically added to Windows Firewall)
  - Protocol: HTTP

- Windows authentication for authenticating users.  
- [!INCLUDE[server](../developer/includes/server.md)] configuration:  

  - Service instance name: BC*NNN* (like BC210, BC200, BC190, or BC140, depending on the version) 
  - Client service port: 7085 (7046 in version 20 and earlier)  
  - SOAP web services port: 7047  
  - OData web services port: 7048  

- [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database components configuration:  
  - Service instance: BCDEMO  
  - Database: Demo Database BC (*NN*-0)

    *NN* is the version number, like 21, 20, 19, or 14.
- NETWORK SERVICE account is used as the service account for [!INCLUDE[server](../developer/includes/server.md)] and database.  

## Prepare for the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] installation  

1. Get access to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] installation media. For example, this could be a DVD or network drive that contains the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] installation files.  
2. Make sure that the computer meets the hardware and software requirements.  

  For more information, see [System Requirements](system-requirement-business-central.md).  

## Run [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)]  

1. From the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] installation media (DVD folder), run the setup.exe file to start the [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)].  

2. Follow the setup until you get to the **Microsoft [!INCLUDE[prod_long](../developer/includes/prod_long.md)]** page, then choose **Advanced installation option** > **Install Demo**.  

    The installation starts. This can take several minutes.  

## Open the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)]  

- To open the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] from the computer where you installed [!INCLUDE[prod_short](../developer/includes/prod_short.md)], on the **Start** menu, choose **All Programs**, and then choose **[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Web Client**.  

- To open the [!INCLUDE[nav_web](../developer/includes/nav_web_md.md)] from other devices on the network, open an Internet browser, and type the following URL in the address box:

  ```http
  http://ComputerName:8080/BCServerInstance  
  ```

  Substitute **ComputerName** with the name of the computer where you installed [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. If you are working on the computer where you installed [!INCLUDE[prod_short](../developer/includes/prod_short.md)], then you can use **localhost**.

   Substitute **BCServerInstance** with the name of the [!INCLUDE[server](../developer/includes/server.md)], like BC210, BC200, BC190, or BC140 (depending on your version).  

  For example:

  ```http
  http://localhost:8080/BC210 
  ```

## Related information  
[Business Central Web Server Overview](web-server-overview.md) 
 
