---
title: "Launch JSON file"
description: "Description of the settings of the launch JSON file for AL in Business Central."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 08/30/2023
ms.reviewer: na
ms.topic: conceptual
ms.author: solsen
---

# Launch JSON file

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

The `launch.json` file contains information about the server that the extension launches on. The `launch.json` file has multiple configuration options available, for example, for snapshot debugging and attach debugging. In Visual Studio Code, you can choose to add a new configuration to the `launch.json` file, by selecting the **Add Configuration** button. The following configuration options are available:

- [Publish to Microsoft cloud sandbox](devenv-json-launch-file.md#publish-to-cloud-settings)
- [Publish to your own server](devenv-json-launch-file.md#publish-to-local-server-settings)
- [Attach to the client on the cloud sandbox or on your own server](devenv-json-launch-file.md#attach-configuration-settings)
- [Initialize a snapshot debugging session on cloud or on your own server](devenv-json-launch-file.md#initialize-snapshot-debugging-settings)

In the following sections, you can find a description of the parameters that are available for each of the configurations. You'll also find a description of how to create a [global or workspace launch configuration file](devenv-json-launch-file.md#global-and-workspace-launch-configuration).

## Publishing settings for cloud and local server

The following table describes the settings in the `launch.json` file. The `launch.json` file has two configurations depending on whether the extension is published to a local server or to the cloud.

### Publish to local server settings

The settings for publishing to a local server are described in the following table.

<!-- NEW -->
|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"Your own server"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Request type of the configuration. Set to `"launch"`.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central.|
|server|Yes|The HTTP URL of your server, for example: `"https://localhost|serverInstance"`|
|port|No|The port assigned to the development service.|
|serverInstance|Yes|The instance name of your server, for example: `"US"`|
|authentication|Yes|Specifies the server authentication method and can be set to `"UserPassword"`, `"Windows"`, or `"AAD"`. To use Microsoft Entra authentication for on-premise servers, `primaryTenantDomain` setting must be entered. For more information, see [Using Microsoft Entra authentication for Business Central on-premises installations](devenv-aad-auth-onprem.md).|
|startupObjectType|No|Specifies whether the object to open after publishing is a Page type (`"Page"`), a Table type (`"Table"`), a Report type (`"Report"`) or a Query type (`"Query"`) object. The default is `"Page"`.|
|startupObjectId|No|Specifies the ID of the object to open after publishing. Only objects of type Page, Table, Report, and Query are currently supported.|
|startupCompany|No|Specifies the name of the company to open after publishing. If `startupCompany` is specified, the settings `startupObjectId` and `startupObjectType` must also be defined.|
|schemaUpdateMode|No|Specifies the data synchronization mode when you publish an extension to the development server, for example: <br>`"schemaUpdateMode": "Recreate"`</br> The default value is Synchronize. For more information, see [Retaining table data after publishing](devenv-retaining-data-after-publishing.md)  <br>[!INCLUDE[nav_not_supported](includes/nav_not_supported.md)]  |
|environmentName|No|Specifies which named production or sandbox environment to use in cases where multiple sandboxes are owned by the same tenant.|
|breakOnError | No |Specifies if and how the debugger breaks on errors in Try functions. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnError` contains the following options: `true` `false`, `None`, `All`, `ExcludeTry`.<br>`false/None` - does not break on any errors, `true/All` -breaks on all errors, and `ExcludeTry` - breaks on errors only if they occur outside of the context of a Try function.<br> The values `true` and `false` are retained for now for backwards compatibility. They map to `All` and `None`. We recommend using the latter going forward. `True` and `false` might become obsolete in a future version.|
|breakOnRecordWrite | No |Specifies if and how the debugger breaks on record changes. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnRecordWrite` contains the following options: `true`, `false`, `None`, `All`, and `Exclude Temporary`. <br> - `false`/`None` specifies to not break on any record writes.<br>- `true`/`All` specifies to break on all record writes.<br>- `ExcludeTemporary` specifies to break on record writes only if they are not on a temporary table.<br><br>The values `true` and `false` are retained for backward compatibility, mapping to `All` and `None`. It's recommended using the latter going forward. `True` and `false` might become obsolete in a future version.|
|launchBrowser|No|Specifies whether to open a new tab page in the browser when publishing the AL extension (Ctrl+F5). The default value is `false`. If the value isn't specified or set to `true`, the session is started. If the value is explicitly set to `false`, the session isn't started unless you launch your extension in debugging mode.|
|enableSqlInformationDebugger|Yes|Specifies whether the debugger shows the SQL information. The default value is `true`. For more information, see [Debugging SQL behavior](devenv-debugging.md#DebugSQL).|
|enableLongRunningSqlStatements|Yes|Specifies whether the debugger enables long running SQL statements in the debugger window.|
|longRunningSqlStatementsThreshold|Yes|Sets the number of milliseconds spent before a SQL statement is considered as long running in the debugger.|
|numberOfSqlStatements|Yes|Sets the number of SQL statements to be shown in the debugger.|
|dependencyPublishingOption|No|Available options are: <br>`Default` - set dependency publishing will be applied <br> `Ignore` - dependency publishing is ignored <br> `Strict` - dependency publishing will fail if there are any apps that directly depend on the startup project and these apps aren't part of the workspace. For more information, see [Working with multiple projects and project references](devenv-work-workspace-projects-references.md).|
|disableHttpRequestTimeout|No|Specifies if the default setting for HTTP request timeout in Visual Studio Code is switched off. The default value is `false`. If the value is set to `true` requests can run without timeout.|
|forceUpgrade|No| Always run upgrade codeunits, even if the version number of the extension is the same as an already installed version. This can be useful for troubleshooting upgrade issues. <br><br>**Note:** The `forceUpgrade` setting requires the package ID to be changed.|
|useSystemSessionForDeployment|No|Runs install and upgrade codeunits in a system session. This will prevent debugging install and upgrade codeunits.|
|snapshotFileName|No|Specifies the snapshot file name used when snapshot debugging files are saved. For more information, see [Snapshot Debugging](devenv-snapshot-debugging.md).|
|primaryTenantDomain|No|Specifies the URL of the Microsoft Entra organization or company associated with the Microsoft Entra tenant. This setting enables Microsoft Entra ID scenarios for on-premises installations. For more information, see [Microsoft Entra authentication for Business Central on-premises
](devenv-aad-auth-onprem.md)|
|tenant|Yes|For an on-premise server, this parameter must contain a tenant name, for example: MyTenant.|
|usePublicURLFromServer|No|Specifies whether to override the NST setting and instead use the host provided in the `launch.json` server property. When set to `false`, the `PublicWebBaseURL` server (NST) setting will be overridden with the server parameter of the `launch.json` when launching the browser using that specific launch configuration. <br>**Note:**<br>This option only affects launching debug sessions to on-premise servers.<br> When set to `true`, the `PublicWebBaseURL` server setting will be used.|

<!-- OLD
|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"Your own server"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Request type of the configuration. Can be set to `"launch"`, `"attach"`, or `"snapshotInitialize"` . Required by Visual Studio Code. For more information, see [Attach and Debug Next](devenv-attach-debug-next.md) and [Snapshot Debugging](devenv-snapshot-debugging.md).|
|server|Yes|The HTTP URL of your server, for example: `"https://localhost|serverInstance"`|
|port|No|The port assigned to the development service.|
|serverInstance|Yes|The instance name of your server, for example: `"US"`|
|authentication|Yes|Specifies the server authentication method and can be set to `"UserPassword"`, `"Windows"`, or `"AAD"`. To use AAD authentication for on-premise servers, `primaryTenantDomain` setting must be entered. For more information, see [Using Microsoft Entra authentication for Business Central on-premises installations](devenv-aad-auth-onprem.md).|
|startupObjectType|No|Specifies whether the object to open after publishing is a Page type (`"Page"`), a Table type (`"Table"`), a Report type (`"Report"`) or a Query type (`"Query"`) object. The default is `"Page"`.|
|startupObjectId|No|Specifies the ID of the object to open after publishing. Only objects of type Page, Table, Report, and Query are currently supported.|
|startupCompany|No|Specifies the name of the company to open after publishing. If `startupCompany` is specified, the settings `startupObjectId` and `startupObjectType` must also be defined.|
|schemaUpdateMode|No|Specifies the data synchronization mode when you publish an extension to the development server, for example: <br>`"schemaUpdateMode": "Recreate"`</br> The default value is Synchronize. For more information, see [Retaining table data after publishing](devenv-retaining-data-after-publishing.md)  <br>[!INCLUDE[nav_not_supported](includes/nav_not_supported.md)]  |
|environmentType|No|Specifies which type of environment to use to connect to [!INCLUDE [prod_short](includes/prod_short.md)]. Possible values are `OnPrem`, `Sandbox`, or `Production`.|
|environmentName|No|Specifies which named production or sandbox environment to use in cases where multiple sandboxes are owned by the same tenant.|
|breakOnError | No |Specifies if and how the debugger breaks on errors in Try functions. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnError` contains the following options: `true` `false`, `None`, `All`, `ExcludeTry`.<br>`false/None` - does not break on any errors, `true/All` -breaks on all errors, and `ExcludeTry` - breaks on errors only if they occur outside of the context of a Try function.<br> The values `true` and `false` are retained for now for backwards compatibility. They map to `All` and `None`. We recommend using the latter going forward. `True` and `false` might become obsolete in a future version.|
|breakOnNext| No | Specifies the session type that the server will connect to. The options are:<br> `WebserviceClient` - web API-based client including ODdata and SOAP clients, <br>`WebClient` - standard web client,<br> `Background` - background sessions, such as job queues, see [Task Scheduler](devenv-task-scheduler.md). <br><br>This setting applies to [Attach and Debug Next](devenv-attach-debug-next.md) and to [Snapshot Debugging](devenv-snapshot-debugging.md).<br><br> For *Attach* debugging, `breakOnNext` defines the next client session that the debug engine will attach to for the same user who has initiated an attach debug session from Visual Studio Code.<br><br>For *Snapshot* debugging, `breakOnNext` defines the next session to hook AL code execution recording for a given user on a tenant. Or, if this isn't specified with the userId in the configuration settings; the first user on the tenant.|
|breakOnRecordWrite | No |Specifies if and how the debugger breaks on record changes. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnRecordWrite` contains the following options: `true`, `false`, `None`, `All`, and `Exclude Temporary`. <br> - `false`/`None` specifies to not break on any record writes.<br>- `true`/`All` specifies to break on all record writes.<br>- `ExcludeTemporary` specifies to break on record writes only if they are not on a temporary table.<br><br>The values `true` and `false` are retained for backward compatibility, mapping to `All` and `None`. It's recommended using the latter going forward. `True` and `false` might become obsolete in a future version.|
|launchBrowser|No|Specifies whether to open a new tab page in the browser when publishing the AL extension (Ctrl+F5). The default value is `false`. If the value isn't specified or set to `true`, the session is started. If the value is explicitly set to `false`, the session isn't started unless you launch your extension in debugging mode.|
|enableSqlInformationDebugger|Yes|Specifies whether the debugger shows the SQL information. The default value is `true`. For more information, see [Debugging SQL behavior](devenv-debugging.md#DebugSQL).|
|enableLongRunningSqlStatements|Yes|Specifies whether the debugger enables long running SQL statements in the debugger window.|
|longRunningSqlStatementsThreshold|Yes|Sets the number of milliseconds spent before a SQL statement is considered as long running in the debugger.|
|numberOfSqlStatements|Yes|Sets the number of SQL statements to be shown in the debugger.|
|dependencyPublishingOption|No|Available options are: <br>`Default` - set dependency publishing will be applied <br> `Ignore` - dependency publishing is ignored <br> `Strict` - dependency publishing will fail if there are any apps that directly depend on the startup project and these apps aren't part of the workspace. For more information, see [Working with multiple projects and project references](devenv-work-workspace-projects-references.md).|
|disableHttpRequestTimeout|No|Specifies if the default setting for HTTP request timeout in Visual Studio Code is switched off. The default value is `false`. If the value is set to `true` requests can run without timeout.|
|forceUpgrade|No| Always run upgrade codeunits, even if the version number of the extension is the same as an already installed version. This can be useful for troubleshooting upgrade issues. <br><br>**Note:** The `forceUpgrade` setting requires the package ID to be changed.|
|useSystemSession|No|Runs install and upgrade codeunits in a system session. This will prevent debugging install and upgrade codeunits.|
|snapshotFileName|No|Specifies the snapshot file name used when snapshot debugging files are saved. For more information, see [Snapshot Debugging](devenv-snapshot-debugging.md).|
|primaryTenantDomain|No|Specifies the URL of the Microsoft Entra organization or company associated with the Microsoft Entra tenant. This setting enables AAD scenarios for on-premises installations. For more information, see [Microsoft Entra authentication for Business Central on-premises
](devenv-aad-auth-onprem.md)|
|usePublicURLFromServer|No|Specifies whether to override the NST setting and instead use the host provided in the `launch.json` server property. When set to `false`, the `PublicWebBaseURL` server (NST) setting will be overridden with the server parameter of the `launch.json` when launching the browser using that specific launch configuration. <br>**Note:**<br>This option only affects launching debug sessions to on-premise servers.<br> When set to `true`, the `PublicWebBaseURL` server setting will be used.|
-->

### Publish to cloud settings

The settings for publishing to a cloud sandbox are described in the following table.

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"Microsoft cloud sandbox"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Request type of the configuration. Must be set to `"launch"`. Required by Visual Studio Code.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central. Must be set to `Sandbox` or `Production`.|
|environmentName|No|Specifies which named production or sandbox environment to use in cases where multiple sandboxes are owned by the same tenant.|
|applicationFamily|No (Yes for Embed apps)|The application family in the cloud server, for example `Fabrikam`. This property is reserved for Embed apps.|
|startupObjectType|No|Specifies whether the object to open after publishing is a Page type (`"Page"`), a Table type (`"Table"`), a Report type (`"Report"`) or a Query type (`"Query"`) object.  The default is `"Page"`.|
|startupObjectId|No|Specifies the ID of the object to open after publishing. Only objects of type Page, Table, Report and Query are currently supported.|
|startupCompany|No|Specifies the name of the company to open after publishing. If `startupCompany` is specified, the settings `startupObjectId` and `startupObjectType` must also be defined.|
|tenant|No|Specifies the tenant to which the package is deployed. If you specify multiple configurations, a drop-down of options will be available when you deploy. This parameter must contain a tenant Microsoft Entra ID domain name, for example `mycustomer.onmicrosoft.com`.|
|breakOnError | No |Specifies if and how the debugger breaks on errors in Try functions. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnError` contains the following options: `true`, `false`, `None`, `All`, `ExcludeTry`.<br>`false/None` - does not break on any errors, `true/All` -breaks on all errors, and `ExcludeTry` - breaks on errors only if they occur outside of the context of a Try function.<br> The values `true` and `false` are retained for now for backwards compatibility. They map to `All` and `None`. We recommend using the latter going forward. `True` and `false` might become obsolete in a future version.|
|breakOnRecordWrite | No |Specifies if and how the debugger breaks on record changes. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnRecordWrite` contains the following options: `true`, `false`, `None`, `All`, and `Exclude Temporary`. <br> - `false`/`None` specifies to not break on any record writes.<br>- `true`/`All` specifies to break on all record writes.<br>- `ExcludeTemporary` specifies to break on record writes only if they are not on a temporary table.<br><br>The values `true` and `false` are retained for backward compatibility, mapping to `All` and `None`. It's recommended using the latter going forward. `True` and `false` might become obsolete in a future version.|
|launchBrowser|No|Specifies whether to open a new tab page in the browser when publishing the AL extension (Ctrl+F5). The default value is `false`. If the value isn't specified or set to `true`, the session is started. If the value is explicitly set to `false`, the session isn't started unless you launch your extension in debugging mode.|
|enableSqlInformationDebugger|Yes|Specifies whether the debugger shows the SQL information. The default value is `true`. For more information, see [Debugging SQL behavior](devenv-debugging.md#DebugSQL).|
|enableLongRunningSqlStatements|Yes|Specifies whether the debugger enables long running SQL statements in the debugger window.|
|longRunningSqlStatementsThreshold|Yes|Sets the number of milliseconds spent before a SQL statement is considered as long running in the debugger.|
|numberOfSqlStatements|Yes|Sets the number of SQL statements to be shown in the debugger.|
|dependencyPublishingOption|No|Available options are: <br>`Default` - set dependency publishing will be applied <br> `Ignore` - dependency publishing is ignored <br> `Strict` - dependency publishing will fail if there are any apps that directly depend on the startup project and these apps aren't part of the workspace. For more information, see [Working with multiple projects and project references](devenv-work-workspace-projects-references.md).|
|disableHttpRequestTimeout|No|Specifies if the default setting for HTTP request timeout in Visual Studio Code is switched off. The default value is `false`. If the value is set to `true` requests can run without timeout.|

## Attach configuration settings

The following tables describe the settings in the `launch.json` file for attach configuration settings. The attach configuration is used for specific debugging scenarios where you don't want to publish and invoke functionality to debug it. For more information, see [Attach and debug next](devenv-attach-debug-next.md).

### Attach to client on cloud sandbox settings

The settings for attaching to a client on a cloud sandbox are described in the following table.

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"Attach: Microsoft cloud sandbox"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Must be set to `attach`.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central. Must be set to `Sandbox`.|
|environmentName|Yes|Specifies which production, or sandbox environment to use.|
|breakOnError | No |Specifies if and how the debugger breaks on errors in Try functions. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnError` contains the following options: `true`, `false`, `None`, `All`, `ExcludeTry`.<br>`false/None` - does not break on any errors, `true/All` -breaks on all errors, and `ExcludeTry` - breaks on errors only if they occur outside of the context of a Try function.<br> The values `true` and `false` are retained for now for backwards compatibility. They map to `All` and `None`. We recommend using the latter going forward. `True` and `false` might become obsolete in a future version.|
|breakOnNext| No | Specifies the session type that the server will connect to. The options are:<br> `WebserviceClient` - web API-based client including OData and SOAP clients, <br>`WebClient` - standard web client,<br> `Background` - background sessions, such as job queues, see [Task Scheduler](devenv-task-scheduler.md). <br><br>This setting applies to [Attach and Debug Next](devenv-attach-debug-next.md) and to [Snapshot Debugging](devenv-snapshot-debugging.md).<br><br> For *Attach* debugging, `breakOnNext` defines the next client session that the debug engine will attach to for the same user who has initiated an attach debug session from Visual Studio Code.<br><br>For *Snapshot* debugging, `breakOnNext` defines the next session to hook AL code execution recording for a given user on a tenant. Or, if this isn't specified with the userId in the configuration settings; the first user on the tenant.|
|breakOnRecordWrite | No |Specifies if and how the debugger breaks on record changes. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnRecordWrite` contains the following options: `true`, `false`, `None`, `All`, and `Exclude Temporary`. <br> - `false`/`None` specifies to not break on any record writes.<br>- `true`/`All` specifies to break on all record writes.<br>- `ExcludeTemporary` specifies to break on record writes only if they are not on a temporary table.<br><br>The values `true` and `false` are retained for backward compatibility, mapping to `All` and `None`. It's recommended using the latter going forward. `True` and `false` might become obsolete in a future version.|
|enableSqlInformationDebugger|Yes|Specifies whether the debugger shows the SQL information. The default value is `true`. For more information, see [Debugging SQL behavior](devenv-debugging.md#DebugSQL).|
|enableLongRunningSqlStatements|Yes|Specifies whether the debugger enables long running SQL statements in the debugger window.|
|longRunningSqlStatementsThreshold|Yes|Sets the number of milliseconds spent before a SQL statement is considered as long running in the debugger.|
|numberOfSqlStatements|Yes|Sets the number of SQL statements to be shown in the debugger.|


### Attach to client on your own server

The settings for attaching to a client on your own server are described in the following table.

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"Attach: Your own server"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Must be set to `attach`.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central. Must be set to `OnPrem`.|
|server|Yes|The HTTP URL of your server, for example: `"https://localhost|serverInstance"`|
|port|No|The port assigned to the development service.|
|serverInstance|Yes|The instance name of your server, for example: `"US"`|
|authentication|Yes|Specifies the server authentication method and can be set to `"UserPassword"`, `"Windows"`, or `"AAD"` (Microsoft Entra ID). To use Microsoft Entra ID for authenticating on-premise servers, `primaryTenantDomain` setting must be entered. For more information, see [Using Microsoft Entra authentication for Business Central on-premises installations](devenv-aad-auth-onprem.md).|
|breakOnError | No |Specifies if and how the debugger breaks on errors in Try functions. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnError` contains the following options: `true`, `false`, `None`, `All`, `ExcludeTry`.<br>`false/None` - does not break on any errors, `true/All` -breaks on all errors, and `ExcludeTry` - breaks on errors only if they occur outside of the context of a Try function.<br> The values `true` and `false` are retained for now for backwards compatibility. They map to `All` and `None`. We recommend using the latter going forward. `True` and `false` might become obsolete in a future version.|
|breakOnNext| No | Specifies the session type that the server will connect to. The options are:<br> `WebserviceClient` - web API-based client including OData and SOAP clients, <br>`WebClient` - standard web client,<br> `Background` - background sessions, such as job queues, see [Task Scheduler](devenv-task-scheduler.md). <br><br>This setting applies to [Attach and Debug Next](devenv-attach-debug-next.md) and to [Snapshot Debugging](devenv-snapshot-debugging.md).<br><br> For *Attach* debugging, `breakOnNext` defines the next client session that the debug engine will attach to for the same user who has initiated an attach debug session from Visual Studio Code.<br><br>For *Snapshot* debugging, `breakOnNext` defines the next session to hook AL code execution recording for a given user on a tenant. Or, if this isn't specified with the userId in the configuration settings; the first user on the tenant.|
|breakOnRecordWrite | No |Specifies if and how the debugger breaks on record changes. With [!INCLUDE [prod_short](includes/prod_short.md)] 2022 release wave 2 `breakOnRecordWrite` contains the following options: `true`, `false`, `None`, `All`, and `Exclude Temporary`. <br> - `false`/`None` specifies to not break on any record writes.<br>- `true`/`All` specifies to break on all record writes.<br>- `ExcludeTemporary` specifies to break on record writes only if they are not on a temporary table.<br><br>The values `true` and `false` are retained for backward compatibility, mapping to `All` and `None`. It's recommended using the latter going forward. `True` and `false` might become obsolete in a future version.|
|enableSqlInformationDebugger|Yes|Specifies whether the debugger shows the SQL information. The default value is `true`. For more information, see [Debugging SQL behavior](devenv-debugging.md#DebugSQL).|
|enableLongRunningSqlStatements|Yes|Specifies whether the debugger enables long running SQL statements in the debugger window.|
|longRunningSqlStatementsThreshold|Yes|Sets the number of milliseconds spent before a SQL statement is considered as long running in the debugger.|
|numberOfSqlStatements|Yes|Sets the number of SQL statements to be shown in the debugger.|
|tenant|Yes|For an on-premise server, this parameter must contain a tenant name, for example: MyTenant.|

## Initialize snapshot debugging settings

The following tables describe the settings in the `launch.json` file for snapshot configuration settings. Snapshot debugging allows you to record AL code that runs on the server, and when it has completed, you can debug the recorded *snapshot* in Visual Studio Code. For more information, see [Snapshot debugging](devenv-snapshot-debugging.md).

### Initialize a snapshot debugging session on a cloud production environment

The settings for snapshot debugging on a cloud production environment are described in the following table.

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"snapshotInitialize: Microsoft production cloud"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Must be set to `snapshotInitialize`.|
|userId|No| The GUID of the user who initiated the process to start snapshot debugging. For on-premises, this can also be the user name in user password authentication scenarios. The user must be able to start, or have a session type opened that is specified in the `breakOnNext` parameter. <br>**Note:** Specifying `userId` doesn't work with Windows authentication: `"authentication" : "Windows"`, in which case you can only choose `sessionId` or attach to the next session. For more information, see [Launch JSON file](devenv-json-launch-file.md).|
|sessionId|No| A session ID for the user specified in `userId`.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central. Must be set to `Production`.|
|environmentName|Yes|Specifies the production environment to use.|
|breakOnNext| No | Specifies the session type that the server will connect to. The options are:<br> `WebserviceClient` - web API-based client including OData and SOAP clients, <br>`WebClient` - standard web client,<br> `Background` - background sessions, such as job queues, see [Task Scheduler](devenv-task-scheduler.md). <br><br>This setting applies to [Attach and Debug Next](devenv-attach-debug-next.md) and to [Snapshot Debugging](devenv-snapshot-debugging.md).<br><br> For *Attach* debugging, `breakOnNext` defines the next client session that the debug engine will attach to for the same user who has initiated an attach debug session from Visual Studio Code.<br><br>For *Snapshot* debugging, `breakOnNext` defines the next session to hook AL code execution recording for a given user on a tenant. Or, if this isn't specified with the userId in the configuration settings; the first user on the tenant.|
|executionContext|Yes|Specifies which kind of connection a snapshot debugging session will be established. There are three options: `Debug`, `DebugAndProfile`, and `Profile`. For more information, see [AL Profiler](devenv-al-profiler-overview.md#snapshot-configuration-settings).|
|snapshotVerbosity|No|Specifies the verbosity level of snapshot data. If SnapPoint is specified then stacktraces and line information will only be gathered on snap points. The options are: `Full`, which allows stepping through every line executed and `SnapPoint`, which only allows stepping to lines with SnapPoints.|
|profilingType|Yes|Specifies the profiling type to be used. There are two options: <br> `Instrumentation`, which means that if profiling is enabled then all frames executed will be measured for their total time <br>`Sampling`, which means that if profiling is enabled then frames will be collected and aggregated based on a sample interval. This option can only be used with the `executionContext` set to `Profile`. For more information, see [AL Profiler](devenv-al-profiler-overview.md|
|profileSamplingInterval|No| Specifies the sampling interval in milliseconds when the `Sampling` profiling type is specified. The default value is 100ms. Options are `50`, `100`, or `150` ms.|

### Initialize a snapshot debugging session on your own server

The settings for snapshot debugging on your own server are described in the following table.

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|Yes|"snapshotInitialize: Your own server"|
|type|Yes|Must be set to `"al"`. Required by Visual Studio Code.|
|request|Yes|Must be set to `snapshotInitialize`.|
|userId|No| The GUID of the user who initiated the process to start snapshot debugging. For on-premises, this can also be the user name in user password authentication scenarios. The user must be able to start, or have a session type opened that is specified in the `breakOnNext` parameter. <br>**Note:** Specifying `userId` doesn't work with Windows authentication: `"authentication" : "Windows"`, in which case you can only choose `sessionId` or attach to the next session. For more information, see [Launch JSON file](devenv-json-launch-file.md).|
|sessionId|No| A session ID for the user specified in `userId`.|
|environmentType|Yes|Specifies which environment to use to connect to Business Central. Must be set to `OnPrem`.|
|environmentName|Yes|Specifies the environment to use.|
|server|Yes|The HTTP URL of your server, for example: `"https://localhost|serverInstance"`|
|port|No|The port assigned to the development service.|
|serverInstance|Yes|The instance name of your server, for example: `"US"`|
|authentication|Yes|Specifies the server authentication method and can be set to `"UserPassword"`, `"Windows"`, or `"AAD"`. To use Microsoft Entra authentication for on-premise servers, `primaryTenantDomain` setting must be entered. For more information, see [Using Microsoft Entra authentication for Business Central on-premises installations](devenv-aad-auth-onprem.md).|
|breakOnNext| No | Specifies the session type that the server will connect to. The options are:<br> `WebserviceClient` - web API-based client including OData and SOAP clients, <br>`WebClient` - standard web client,<br> `Background` - background sessions, such as job queues, see [Task Scheduler](devenv-task-scheduler.md). <br><br>This setting applies to [Attach and Debug Next](devenv-attach-debug-next.md) and to [Snapshot Debugging](devenv-snapshot-debugging.md).<br><br> For *Attach* debugging, `breakOnNext` defines the next client session that the debug engine will attach to for the same user who has initiated an attach debug session from Visual Studio Code.<br><br>For *Snapshot* debugging, `breakOnNext` defines the next session to hook AL code execution recording for a given user on a tenant. Or, if this isn't specified with the userId in the configuration settings; the first user on the tenant.|
|executionContext|Yes|Specifies which kind of connection a snapshot debugging session will be established. There are three options: `Debug`, `DebugAndProfile`, and `Profile`. For more information, see [AL Profiler](devenv-al-profiler-overview.md#snapshot-configuration-settings).|
|snapshotVerbosity|No|Specifies the verbosity level of snapshot data. If SnapPoint is specified then stacktraces and line information will only be gathered on snap points. The options are: <br>`Full`, which allows stepping through every line executed <br>`SnapPoint`, which only allows stepping to lines with SnapPoints.|
|profilingType|Yes|Specifies the profiling type to be used. There are two options: <br> `Instrumentation`, which means that if profiling is enabled then all frames executed will be measured for their total time <br>`Sampling`, which means that if profiling is enabled then frames will be collected and aggregated based on a sample interval. This option can only be used with the `executionContext` set to `Profile`. For more information, see [AL Profiler](devenv-al-profiler-overview.md).|
|profileSamplingInterval|No| Specifies the sampling interval in milliseconds when the `Sampling` profiling type is specified. The default value is 100ms. Options are `50`, `100`, or `150` ms.|

## Global and workspace launch configuration

With [!INCLUDE[prod_short](includes/prod_short.md)] version 21.1, you can add a launch property to a code-workspace or in the settings.json file. This allows for a centralized configuration of projects. A local `launch.json` file overrides the workspace and global configuration. A workspace launch configuration overrides the launch configuration specified in the global `settings.json` file.

> [!NOTE]  
> If a local `launch.json` file doesn't contain a valid AL launch configuration, we'll try to find one in the code-workspace first, and then in the `settings.json` files. However, if the launch property is specified in the code-workspace file even without specifying a valid AL configuration, the global `settings.json` file won't be able to override it.

## See Also

[JSON files](devenv-json-files.md)  
[AL Development Environment](devenv-reference-overview.md)  
[App Identity](devenv-app-identity.md)  
[Debugging in AL](devenv-debugging.md)  
[Resource Exposure Policy Setting](devenv-security-settings-and-ip-protection.md)  
[AL Language Extension Configuration](devenv-al-extension-configuration.md)  
[Configure Context-Sensitive Help](../help/context-sensitive-help.md)  
[App Key Vaults](devenv-app-key-vault-overview.md)
