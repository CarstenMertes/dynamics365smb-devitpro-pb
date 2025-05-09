---
title: Hardening Business Central Server Security
description: Learn how you can harden security on the Business Central Server component to protect access to the configuration settings.
author: SusanneWindfeldPedersen
ms.topic: concept-article
ms.author: solsen
ms.date: 09/09/2024
ms.reviewer: solsen
---
# Hardening Business Central server security

[!INCLUDE[server](../developer/includes/server.md)] is a .NET-based Windows Service application that works exclusively with SQL Server and Azure SQL Server databases. [!INCLUDE[server](../developer/includes/server.md)] provides an extra layer of security between clients and the database. It applies the authentication features of the Windows Communications Framework to provide another layer of user authentication. It uses impersonation to ensure that business logic is executed in a process that is instantiated by the user who submitted the request. Authorization and logging of user requests are performed on a per-user basis.  
  
## Login account

The [!INCLUDE[server](../developer/includes/server.md)] is configured with a login account, which is referred to as the *service account*. The service account is used by [!INCLUDE[prod_short](../developer/includes/prod_short.md)] clients to log on to the [!INCLUDE[server](../developer/includes/server.md)] instance. The [!INCLUDE[server](../developer/includes/server.md)] then uses the service account to log on to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database.
  
The default configuration is for the service to log on using the NT Authority\\Network Service account. If [!INCLUDE[server](../developer/includes/server.md)] and SQL Server are on different computers, then we recommend that you configure [!INCLUDE[server](../developer/includes/server.md)] to log on using a dedicated Windows domain user account instead. This account shouldn't be an administrator either in the domain or on any local computer. A dedicated domain user account is considered more secure because no other services and therefore no other users have permissions for this account. Learn more about using a domain account and configuring the recommended permissions in [Provisioning the Business Central Server Service Account](../deployment/provision-server-account.md).  

## Authentication

We recommend that your solution uses Microsoft Entra ID for authentication, especially when a solution must access both cloud and on-premises resources. Microsoft Entra ID is a managed identities service that offers various security measures, like:

- Multifactor Authentication (MFA): Adds an extra layer of security beyond passwords.
- Passwordless sign-ins: Users can sign in using methods such as authentication apps, reducing reliance on traditional passwords.

[!INCLUDE[navuserpassword](../developer/includes/navuserpassword.md)]

## Disk quotas

 Client users can send files to be stored on [!INCLUDE[server](../developer/includes/server.md)], so we recommend that administrators set up disk quotas on all computers running [!INCLUDE[server](../developer/includes/server.md)]. This quota can prevent users from uploading too many files, which can make the server unstable. Disk quotas track and control disk space usage for NTFS volumes, which allows administrators to control the amount of data that each user can store on a specific NTFS volume. For more information about disk quotas, see the [Disk Quotas Technical Reference](/previous-versions/windows/it-pro/windows-server-2003/cc786969(v=ws.10)) on Microsoft TechNet.  
  
## Limiting client services port access

The client services port is used for communication between the [!INCLUDE[server](../developer/includes/server.md)] and [!INCLUDE[webserver](../developer/includes/webserver.md)]. By default, this port  is 7085.

- Ensure that this port is blocked from external networks, allowing communication only between the [!INCLUDE[server](../developer/includes/server.md)] and [!INCLUDE[webserver](../developer/includes/webserver.md)].
- When the [!INCLUDE[server](../developer/includes/server.md)] and [!INCLUDE[webserver](../developer/includes/webserver.md)] are on different machines, an inbound rule in Windows Firewall is required to allow communication on the port. To improve security, limit access to this port to a specific subnet. One way is to use `netsh`, which is a command-line tool for configuring and monitoring Windows-based computers at a command prompt. The specific version of this command that you would use is `netsh firewall set portopening`. For example, the following command limits access to port 7085 to the specified addresses and subnets:  
  
  ```  
  netsh firewall set portopening protocol=TCP port=7085 scope=subnet addresses=LocalSubnet  
  ```  

## <a name="data-encryption"></a>Data Encryption Between [!INCLUDE[server](../developer/includes/server.md)] and SQL Server  

When SQL Server and [!INCLUDE[server](../developer/includes/server.md)] are running on different computers, you can make this data channel more secure by encrypting the connection with IPSec. \(Other encryption options aren't supported.\) Learn more at [Enable Encrypted Connections to the Database Engine](/sql/database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine).

## Related information

[Configuring Business Central Server](../administration/configure-server-instance.md)  
[Security and Protection](security-and-protection.md)   
[How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10))
