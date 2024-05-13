---
title: "Configuring Business Central Web Server instance"
description: Learn about the different configuration settings when you deploy the Business Central web server on-premises.
ms.custom: bap-template
ms.date: 08/20/2022
ms.reviewer: jswymer
ms.service: dynamics-365-op
ms.topic: conceptual
author: jswymer
---
# Configuring [!INCLUDE[webserver](../developer/includes/webserver.md)] Instances

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

Accessing [!INCLUDE[prod_short](../developer/includes/prod_short.md)] from the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] or App requires a [!INCLUDE[webserver](../developer/includes/webserver.md)] instance on IIS. You create a [!INCLUDE[webserver](../developer/includes/webserver.md)] instance for the [!INCLUDE[webserver](../developer/includes/webserver.md)] two ways:

- Using the [!INCLUDE[prodsetup](../developer/includes/prodsetup.md)] to install the [!INCLUDE[webserver](../developer/includes/webserver.md)]
- Running the [New-NAVWebServerInstance cmdlet](/powershell/module/Microsoft.Dynamics.Nav.Management/new-navwebserverinstance).

When you set up a web server instance, you're configuring the connection to the [!INCLUDE[server](../developer/includes/server.md)] instance. The connection settings are saved in a configuration file for the web server instance.

## <a name="WebClientSettingsFile"></a>About the configuration file
The configuration file for the web server instances is a .json file type called **navsettings.json**. The navsettings.json file is a JavaScript Object Notification file type that is similar to files that use the XML file format.

After installation, you can change the configuration by modifying the navsettings.json. There are two ways to modify this file: directly or using PowerShell.

### Where to find the navsettings.json file

The navsettings.json file is in the physical path of the web server instance. By default, the path is *C:\\inetpub\\wwwroot\\[WebServerInstanceName]* on the computer's hard drive.

*[WebServerInstanceName]* corresponds to the name (alias) of the web server instance in IIS, for example, *C:\inetpub\\wwwroot\\[!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]*. 

## Modify the navsettings.json file directly

1. Open the navsettings.json in any text or code editor, such as Notepad or Visual Studio Code.

    Each setting is defined by a key-value pair.  
    
    -   In the navsettings.json file, a setting has the format:

        ```
        "keyname": "keyvalue",
        ```
   
    The `keyname` is the name of the configuration setting and the `keyvalue` is the value.
    
    For example, the configuration setting that specifies the Windows credential type for authenticating users is:

    ```
    "ClientServicesCredentialType":  "Windows",
    ```

    Include values in double quotes.
2.  Find the configuration settings that you want to change, and then change the values.

    See the [Settings](configure-web-server.md#Settings) section for a description of each setting.
3.  When you're done making changes, save the file.
4.  Restart the [!INCLUDE[webserver](../developer/includes/webserver.md)] instance for the changes to take effect.
    
    For example, in IIS Manager, in the **Connections** pane, select website node for [!INCLUDE[webserver](../developer/includes/webserver.md)], and then in the **Actions** pane, choose **Restart**. Or, from your desktop, run `iisreset`. 

## Modify the navsettings.json file by using the Set-NAVWebServerInstanceConfiguration cmdlet

The PowerShell script module **NAVWebClientManagement.psm1** includes the [Set-NAVWebServerInstanceConfiguration cmdlet](/powershell/module/Microsoft.Dynamics.Nav.Management/Set-NAVWebServerInstanceConfiguration) that enables you to configure a web server instance.

1. Depending on your installation, run the [!INCLUDE[devshell](../developer/includes/devshell.md)] or Windows PowerShell as an administrator.

    For more information, see [Get started with the [!INCLUDE[webserver](../developer/includes/webserver.md)] cmdlets](../deployment/configure-multiple-web-server-instances.md#GetStartedWebServerCmdlets).

2. For each setting that you want to change, at the command prompt, run the following command:

    ```powershell
    Set-NAVWebServerInstanceConfiguration -Server [MyComputer] -ServerInstance [ServerInstanceName] -WebServerInstance [MyBCWebServerInstance] -KeyName [Setting] -KeyValue [Value]
    ```

    Replace:
    - `[MyComputer]` with the name of the computer that is running the [!INCLUDE[server](../developer/includes/server.md)]
    - `[ServerInstanceName]` with the name of the server instance, such as **[!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]**.
    - `[MyBCWebServerInstance]`with the name of the web server instance for the [!INCLUDE[webserver](../developer/includes/webserver.md)].
    - `[KeyName]` with the name of the setting. Refer to the next section in this article.
    - `[KeyValue]` with the new value of the setting.

## <a name="Settings"></a>Settings in the navsettings.json

The navsettings.json has the following structure, where settings are included under one of two root elements: `NAVWebSettings` and `ApplicationIdSettings`:

```
{
  "NAVWebSettings": {
     "//ServerInstance":  "Name of the Business Central Server instance to connect to (for client) or listen on (for server).",
     "ServerInstance":  "BC150",
      [...more keys]
 },
  "ApplicationIdSettings": {
      "BlogLink": "https://myBCBlog.com",
      [...more keys]
  }
}
```

`//` indicates a comment that provides help for the setting, and has no effect on the Web Server instance.

The following table describes the settings that are available in the navsettings.json for each root element.
- If you don't see a setting in the file, it's because some settings aren't automatically included as a key in the file. For these settings, you can add the key manually.
- If you don't add the key, the default value of the setting is used.  

> [!IMPORTANT]  
>  If modifying the file directly, place values in double quotes `""`.

### `NAVWebSettings` element settings

|Setting/KeyName|Description|  
|-------------|-----------------|
|AadApplicationId|Specifies the application (client) ID assigned to the registered application for Business Central in the Microsoft Entra tenant. This setting is only used for Microsoft Entra authentication in Business Central, version 20.0 and later. The value must match the value of the `Valid Audiences` setting on the [!INCLUDE[server](../developer/includes/server.md)]. For more information, see [Authenticating [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Users with Microsoft Entra ID](authenticating-users-with-azure-ad-openid-connect.md)|
|AadAuthorityUri|Specifies the URI of the Microsoft Entra ID authority used for Microsoft Entra authentication. This setting is only used for Microsoft Entra authentication in Business Central, version 20.0 and later. The value has the format `https://login.microsoftonline.com/<AADTenentID>`, where `<AADTenentID>` is the Microsoft Entra tenant ID. For more information, see [Authenticating [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Users with Microsoft Entra ID](authenticating-users-with-azure-ad-openid-connect.md)|
|AllowedCrossFrameMessageAncestors|Specifies the host name of any web domain that is allowed to send messages to iframes hosting [!INCLUDE[prod_short](../developer/includes/prod_short.md)] or parts of it. By default, the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web server won't allow messages to be sent to the iframes, unless the website is hosted on the same web server. This condition can affect the browser printing functionality of the product. The value of this setting is a comma-separated list of host names (URIs). Wildcard names are accepted. For example: `https://mysite.sharepoint.com, https://*.myportal.com`.|  
|AllowedFrameAncestors|Specifies the host name of any web sites in which the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] or parts of are embedded. By default, the [!INCLUDE[webserver](../developer/includes/webserver.md)] won't allow a website to display it inside an iframe unless the website is hosted on the same web server. This value of this setting is a comma-separated list of host names (URIs). Wildcard names are accepted. For example: `https:mysite.sharepoint.com, https:*.myportal.com`<BR /><BR /> <!--For more information, see [Embedding Microsoft Dynamics NAV Web Client Pages in Other Websites](Embedding-Microsoft-Dynamics-NAV-Web-Client-Pages-in-Other-Websites.md)-->|
|AllowNtlm|Specifies whether NT LAN Manager \(NTLM\) fallback is permitted for authentication.<br /><br /> To require Kerberos authentication, set this value to `false`.<br /><br /> Values: `true`, `false`<br /><br /> Default value: `true`|
|AuthenticateServer |Specifies whether enable service identity checks on the protocol between the web server and the Business Central Server instance.<br /><br /> Values: `true`, `false`<br /> Default value: `true`|  
|ClientServicesCredentialType|Specifies the authorization mechanism that is used to authenticate users who try to connect to the [!INCLUDE[webserver](../developer/includes/webserver.md)]. For more information, see [Authentication and User Credential Type](../administration/users-credential-types.md).<br /><br /> The credential type must match the credential type configured for the [!INCLUDE[server](../developer/includes/server.md)] instance that the [!INCLUDE[webserver](../developer/includes/webserver.md)] connects to. For information about how to set up the credential type on [!INCLUDE[server](../developer/includes/server.md)], see [Configuring Business Central Server](configure-server-instance.md).<br /><br /> Values: Windows, UserName, NavUserPassword, AccessControlService<br /><br /> Default value: Windows|  
|ClientServicesChunkSize|Sets the maximum size, in kilobytes, of a data chunk that is transmitted between [!INCLUDE[webserver](../developer/includes/webserver.md)] and [!INCLUDE[server](../developer/includes/server.md)]. Data that's transmitted between [!INCLUDE[webserver](../developer/includes/webserver.md)] and [!INCLUDE[server](../developer/includes/server.md)] is broken down into smaller units called chunks. It's then reassembled when it reaches its destination.<br /><br /> Values: From 4 to 80.<br /><br /> Default value: 28<br /><br />[!INCLUDE[2022rw1_and-earlier_only](../developer/includes/2022rw1_and-earlier_only.md)]|  
|ClientServicesCompressionThreshold|Sets the threshold in memory consumption at which [!INCLUDE[webserver](../developer/includes/webserver.md)] starts compressing data sets. This setting limits amount of consumed memory. The value is in kilobytes.<br /><br /> Default value: 64|
|ClientServicesPort|Specifies the TCP port for the [!INCLUDE[server](../developer/includes/server.md)]. The port is part of the [!INCLUDE[server](../developer/includes/server.md)]'s URL.<br /><br /> Values: 1-65535<br /><br /> Default value: 7085 (7046 in version 20 and earlier)|  
|ClientServicesProtectionLevel|Specifies the security services used to protect the data stream between the [!INCLUDE[webserver](../developer/includes/webserver.md)] and [!INCLUDE[server](../developer/includes/server.md)]. This value must match the value that is specified in the [!INCLUDE[server](../developer/includes/server.md)] configuration file. For more information, see [Configuring Business Central Server](configure-server-instance.md).<br /><br /> Values: EncryptAndSign, Sign, None<br /><br /> Default value: EncryptAndSign<br /><br />[!INCLUDE[2022rw1_and-earlier_only](../developer/includes/2022rw1_and-earlier_only.md)]| 
|DefaultRelativeHelpPath|Specifies the default Help article to open if no other context-sensitive link is specified.<br /><br /> Default value: none|
|Designer|Specifies whether the in-client designer is enabled in the [!INCLUDE[webclient](../developer/includes/webclient.md)]. Set to `true` to enable designer.<br /><br />For more information, see [Use Designer](../developer/devenv-inclient-designer.md).|
|DnsIdentity|Specifies the subject name or common name of the service certificate for [!INCLUDE[server](../developer/includes/server.md)].<br /><br /> This parameter is only relevant when security certificates are used on the [!INCLUDE[webserver](../developer/includes/webserver.md)] and [!INCLUDE[server](../developer/includes/server.md)] to protect communication. **Note:**  You can find the subject name by opening the certificate in the Certificates snap-in for Microsoft Management Console \(MMC\). The MMC is available on the computer that's running [!INCLUDE[webserver](../developer/includes/webserver.md)] or [!INCLUDE[server](../developer/includes/server.md)]. <br /><br /> For more information, see [Authentication and User Credential Type](../administration/users-credential-types.md).<br /><br /> Value: The subject name of the certificate.<br /><br /> Default value: none|
|GlobalEndPoints|Specifies the comma-separated list of global endpoints that are allowed to call this website. The values must include http scheme and fully qualified domain name (FDQN), such as `https://businesscentral.microsoft.com`.<br /><br />"GlobalEndPoints": "null,ms://businesscentral,ms://dynamicsnav"<br /><br /> Default value: none|
|HelpServer|Specifies the name of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Help Server if the deployment uses Help Server. If the deployment uses an online library, remove this setting.<br /><br /> Default value: none|
|HelpServerPort|Specifies the TCP port on the specified [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Help Server if the deployment uses Help Server. If the deployment uses an online library, remove this setting.<br /><br /> Default value: none|
|LoadScriptsFromCdn|Specifies whether to load scripts from Content Distribution Networks (CDNs). This setting only applies to scripts that are available from a CDN, like jQuery.<br /><br />If set to `false`, scripts will be loaded from the web server, which is useful in, for example, an intranet scenario where there's no internet access.<br />Default value: `true`<br /><br />**DISCONTINUED AFTER:** Business Central Spring 2019|
|ManagementServicesPort|The listening TCP port for the Business Central management endpoint. <br /><br />Valid range: 1-65535<br />Default value: 7045|
|OfficeSuiteShellServiceClientTimeout |Defines the time Business Central will wait for the Office Suite Shell Service to respond.<br /><br />**Important:** This setting has been deprecated in Business Central, and it has no effect on the Web Server instance. <br /><br /> Default value: 10|
|PersonalizationEnabled|Specifies whether personalization is enabled in the [!INCLUDE[webclient](../developer/includes/webclient.md)]. Set to `true` to enable personalization.<br /><br />For more information, see [Managing Personalization](/dynamics365/business-central/ui-personalization-manage).|
|ProductName|Specifies the full name of the application.|
|ProductNameShort|Specifies the short name of the application.|
|ProductNameMarketing|Specifies the marketing name of the application.|
|RequireSsl|Specifies whether SSL (https) is required. If the value is set to `true`, all cookies will be marked with a `\u0027secure\u0027` attribute. If SSL is enabled on the web server, you should set this setting to `true`.<br /><br /> Values: `true`, `false`<br /> Default value: `false`|
|Server|Specifies the name of the computer that is running the [!INCLUDE[server](../developer/includes/server.md)].<br /><br /> Default value: localhost|  
|ServerInstance|Specifies the name of the [!INCLUDE[server](../developer/includes/server.md)] instance that the [!INCLUDE[webserver](../developer/includes/webserver.md)] connects to.<br /><br /> Default value: [!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]| 
|ServerHttps|Specifies whether https is used over the connection to the [!INCLUDE[server](../developer/includes/server.md)] instance. If the `ClientServicesSSLEnabled` setting of the [!INCLUDE[server](../developer/includes/server.md)] is set to `true` then `ServerHttps` must also be set to `true`.<br /><br />For more information, see [Using Security Certificates with Business Central On-Premises](../deployment/implement-security-certificates-production-environment.md). <br /><br />Default value: false| 
|ServicePrincipalNameRequired|If this parameter is set to `true`, then the [!INCLUDE[webserver](../developer/includes/webserver.md)] can only connect to a [!INCLUDE[server](../developer/includes/server.md)] instance that has been associated with a service principal name \(SPN\).<br /><br /> If this parameter is set to `false`, then the [!INCLUDE[webserver](../developer/includes/webserver.md)] attempts to connect to the configured [!INCLUDE[server](../developer/includes/server.md)] service, even if the service isn't associated with an SPN.<br /><br /> For more information about SPNs, see [Configure Delegation](../deployment/configure-delegation-web-server.md).<br /><br /> Default: `false`|
|SessionTimeout|Specifies the maximum time that a connection between the [!INCLUDE[webserver](../developer/includes/webserver.md)] and the [!INCLUDE[server](../developer/includes/server.md)] can remain idle before the session is stopped.<br /><br /> In the [!INCLUDE[webserver](../developer/includes/webserver.md)], this setting determines how long an open [!INCLUDE[prod_short](../developer/includes/prod_short.md)] page or report can remain inactive before it closes. For example, suppose the SessionTimeout is set to 20 minutes. If a user doesn't take any action on a page within 20 minutes, then the page closes and it's replaced with the following message: **The page has expired and the content cannot be displayed.**<br /><br /> The time span has the format \[dd.\]hh:mm:ss\[.ff\]:<br /><br /> -   dd is the number of days<br />-   hh is the number of hours<br />-   mm is the number of minutes<br />-   ss is the number of seconds<br />-   ff  is fractions of a second<br /><br /> Default value: 00:20:00|
|ShowPageSearch|Specifies whether to show the ![Tell me what you want to do](../developer/media/search-icon.png "Search for Page or Report") **Tell me what you want to do** icon in the Business Central header. This feature lets users find [!INCLUDE[prod_short](../developer/includes/prod_short.md)] objects, such as pages, reports, and actions. <br /><br /> If you don't want to show the **Tell me what you want to do** icon, then set the parameter to `false`.<br /><br /> Default value: `true`|
|<a name="spn"></a>UnknownSpnHint|Specifies whether to use a server principal name when establishing the connection between the [!INCLUDE[webserver](../developer/includes/webserver.md)] server and [!INCLUDE[server](../developer/includes/server.md)]. This setting is used to authenticate the [!INCLUDE[server](../developer/includes/server.md)], and it prevents the [!INCLUDE[webserver](../developer/includes/webserver.md)] server from restarting when it connects to [!INCLUDE[server](../developer/includes/server.md)] for the first time. You set values that are based on the value of the ServicePrincipalNameRequired key.<br /><br /> Value: The value has the following format.<br /><br /> \(net.tcp://BCServer:Port/ServerInstance/Service\)=NoSpn&#124;SPN<br /><br /> -   `BCServer` is the name of the computer that is running the [!INCLUDE[server](../developer/includes/server.md)].<br />-   Port is the port number on which the [!INCLUDE[server](../developer/includes/server.md)] is running.<br />-   ServerInstance is the name of the [!INCLUDE[server](../developer/includes/server.md)] instance.<br />-   NoSpn&#124;SPN specifies whether to use an SPN. If the ServicePrincipalNameRequired key is set to `false`, then set this value to NoSpn. If the ServicePrincipalNameRequired key is set to `true`, then set this value to `Spn`.<br /><br /> Default value: \(net.tcp://localhost:7046/[!INCLUDE[serverinstance](../developer/includes/serverinstance.md)]/Service\)=NoSpn<br /><br /> If you set this key to the incorrect value, then during startup, the [!INCLUDE[webserver](../developer/includes/webserver.md)] will automatically determine a correct value. An incorrect value will cause the [!INCLUDE[webserver](../developer/includes/webserver.md)] to restart. **Note:**  For most installations, you don't have to change this value. Unlike the [!INCLUDE[nav_windows](../developer/includes/nav_windows_md.md)], this setting isn't updated automatically. If you want to change the default value, then you must change it manually.<br /><br />[!INCLUDE[2022rw1_and-earlier_only](../developer/includes/2022rw1_and-earlier_only.md)]|  
|UseAdditionalSearchTerms|Specifies whether **Tell me** uses the other search terms that are defined on pages and reports.<br /><br />The other search terms are specified by the [AdditionalSearchTerms](../developer/properties/devenv-additionalsearchterms-property.md) and [AdditionalSearchTermsML](../developer/properties/devenv-additionalsearchtermsml-property.md) properties.<br /><br /> If you set this key name to `false`, the other search terms are ignored.<br /><br /> Default value: true |
|SaveValueToDatabasePromptly|If set to `true`, changes to values in fields are saved to the database as soon as the user moves focus from the field, for example, by selecting <kbd>Tab</kbd>. `false` is the default value. If set to `false`, changes aren't saved until the user closes the page by using the back arrow or stops editing by choosing the edit (pencil) button. After making changes to a field and moving focus to the next field, a user will see the status in the upper-right corner of the page change to **Saving** and then to **Saved**. This behavior can be misleading because the changes aren't yet saved to the database at this time.|

### `ApplicationIdSettings` element settings

|Setting/KeyName|Description|  
|-------------|-----------------|  
|BaseHelpUrl|Specifies the link to the online Help library that the deployment uses, such as *`https://mysite.com/{0}/mylibrary/`*.<br /><br /> Default value: none<br /><br />For more information, see [Configuring the Help Experience](../deployment/configure-help.md). |
|BlogLink|Specifies the target of the **blog** link on the **Help & Support** page. Use this link to give users access to your end-user blog. <br /><br />Value: a valid URL<br />Default value: https://go.microsoft.com/fwlink/?linkid=2076643|
|ComingSoonLink|Specifies the target of **coming soon** link on the **Help & Support** page. Use this link to give users access to information about your roadmap or any upcoming features and fixes.<br /><br />Value: A valid URL.<br /> Default value: [https://go.microsoft.com/fwlink/?linkid=2047422](/dynamics365/release-plans/)|
|CommunityLink|Specifies the URL to a community or resource for sharing information. <br /><br />Value: a valid URL <br />Default value: https://go.microsoft.com/fwlink/?LinkId=287089|
|ContactSalesLink|Specifies the target of the contact sales link on the **Help & Support** page. Use this link to give users access to your sales-focused web page where users can engage with your sales process. **Note:** This setting and link aren't used for Business Central on-premises.|
|SigninHelpLink|Specifies the URL to open if the user selects help on the sign-in page box. <br /><br />Value: a valid URL<br />Default value: none|


<!--
|AndroidPrivacy||
|AndroidSoftwareLicenseTerms||
|AndroidThirdPartyNotice||
|IosPrivacy||
|IosSoftwareLicenseTerms||
|IosThirdPartyNotice||
|FeedbackLink|Specifies the URL to a feedback system for gathering end-user feedback about the application. |
|KeyboardShortcutsLink|Specifies the URL to an article that describes the keyboard shortcuts for the application.<br /><br />Default value: https://go.microsoft.com/fwlink/?linkid=2064754|
|LegalLink|Specifies the URL to the legal information about application. <br /><br />Default value: https://go.microsoft.com/fwlink/?LinkId=843026|
|PrivacyLink|Specifies the URL to the privacy information for the application. This link also appears in the sign-in page.<br /><br />Default value: https://go.microsoft.com/fwlink/?LinkId=837448|
-->

## See Also  
[Setting up Multiple Business Central Web Server Instances](../deployment/configure-multiple-web-server-instances.md)   
[Install Business Central Components](../deployment/install-using-setup.md)  
[Business Central Web Server Overview](../deployment/web-server-overview.md)  
[Configuring Business Central Server](configure-server-instance.md)  
[Configuring the Help Experience](../deployment/configure-help.md)
