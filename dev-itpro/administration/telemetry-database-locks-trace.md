---
title: Database Lock Timeout Trace Telemetry | Microsoft Docs
description: Learn about the database lock timeout Trace Telemetry telemetry in Business Central  
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 04/01/2021
ms.author: jswymer
---

# Analyzing Database Lock Timeout Trace Telemetry

**INTRODUCED IN:** Business Central 2020 release wave 1, version 16.0

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

Database lock timeout telemetry gathers information about database locks that have timed out. The telemetry data allows you to troubleshoot what caused these locks.

In the client, when a lock has timed out, the user is presented with a message, similar to the following message:

*The operation could not complete because a record in the [table name] table was locked by another user. Please retry the activity.*

Two types of trace events are emitted to Application Insights:

- The first is a **Database lock timed out** event. This event includes general information about the lock request. This event includes information like the AL object and code that is impacted by the lock, the extension involved, and more.

- The **Database lock timed out** event then triggers one or more **Database lock snapshot** events. **Database lock snapshot** events provide details about SQL sessions that hold database locks at the time of lock timeout, including the session that caused the lock timeout. These events include specific details about the SQL lock request on the database, like the type, status, mode, and the table.

> [!NOTE]
> In later versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises, the [!INCLUDE[server](../developer/includes/server.md)] includes the `EnableLockTimeoutMonitoring` setting. Use this setting to turn database lock timeout telemetry on or off. By default, it is off. For more information, see [Configuring Business Central Server](configure-server-instance.md#Database).

## Database lock timed out

Occurs when a database lock has timed out for a session.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Database lock timed out**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|aadTenantId|Specifies the Microsoft Entra tenant ID used for Microsoft Entra authentication. For on-premises, if you aren't using Microsoft Entra authentication, this value is **common**. |
|alExecutingMethodScope|Specifies the AL action that is running the transaction that caused the lock.|
|alObjectId|Specifies the ID of the running AL object that requested the lock. |
|alObjectName|Specifies the name of the running AL object that requested the lock. not shown|
|alObjectType|Specifies the type of the running AL object that requested the lock, such as a page or report. |
|alStackTrace|The stack trace in AL.|
|clientType|Specifies the type of client that executed the SQL Statement, such as **Background** or **Web**. For a list of the client types, see [ClientType Option Type](../developer/methods-auto/clienttype/clienttype-option.md).|
|companyName|Specifies the display name of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] company.|
|component|**Dynamics 365 Business Central Server**|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|deprecatedKeys|Specifies a comma-separated list of all the keys that have been deprecated. The keys in this list are still supported but will eventually be removed in the next major release. We recommend that update any queries that use these keys to use the new key name.|
|eventId|**RT0012**|
|environmentName|Specifies the name of the tenant environment. See [Managing Environments](tenant-admin-center-environments.md).|
|environmentType|Specifies the environment type for the tenant, such as **Production**, **Sandbox**, **Trial**. See [Environment Types](tenant-admin-center-environments.md#types-of-environments)|
|extensionId|Specifies the AppID of the extension that was involved in the lock.|
|extensionName|Specifies the name of the extension that was involved in the lock.|
|extensionVersion|Specifies the version of that was involved in the lock.|
|sessionId|Specifies the ID of the session that requested the lock. |
|snapshotId|Specifies the ID of the database snapshot. This ID is used to identify associated **Database lock snapshot** trace events.|
|sqlServerSessionId|Specifies the ID of the SQL server session that requested the lock. |
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|

### Sample KQL code

This KQL code can help you get started troubleshooting lock timeouts.

```kql
traces 
| where timestamp > ago(2d) // adjust to your needs
| where customDimensions has 'RT0012'
| where customDimensions.eventId == 'RT0012'
| project timestamp
, aadTenantId = customDimensions.aadTenantId
, environmentType = customDimensions.environmentType
, environmentName = customDimensions.environmentName
, companyName = customDimensions.companyName
, clientType = customDimensions.clientType
, alObjectId = customDimensions.alObjectId
, alObjectType = customDimensions.alObjectType
, alObjectName = customDimensions.alObjectName
, extensionVersion = customDimensions.extensionVersion
, extensionName = customDimensions.extensionName
, extensionId = customDimensions.extensionId
, alStackTrace = customDimensions.alStackTrace
, sqlStatement = customDimensions.sqlStatement
, sqlServerSessionId = customDimensions.sqlServerSessionId
, snapshotId = customDimensions.snapshotId
, sessionId = customDimensions.sessionId
, usertelemetryId = case(
  // usertelemetryId was introduced in the platform in version 20.0
  toint( substring(customDimensions.componentVersion,0,2)) >= 20, user_Id
, 'N/A'
)
```

## Database lock snapshot

This telemetry event can occur in two ways:
1. when a database lock has timed out
2. when a user or AL process has issued that a snapshot is taken

In the case of a database lock timeout, the BC server also takes a snapshot. Here, the **Database lock snapshot** trace event is associated with a specific **Database lock timed out** trace event. The value of the `{snapshotId}` maps to the `snapshotId` dimension of the **Database lock timed out** trace event that triggered this event.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Database lock snapshot: {snapshotId}**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|aadTenantId|Specifies the Microsoft Entra tenant ID used for Microsoft Entra authentication. For on-premises, if you aren't using Microsoft Entra authentication, this value is **common**. |
|alExecutingMethodScope|Specifies the AL action that is running the transaction that caused the lock.|
|alObjectId|Specifies the ID of the running AL object that requested the lock. |
|alObjectName|Specifies the name of the running AL object that requested the lock.|
|alObjectType|Specifies the type of the running AL object that requested the lock, such as a page or report. |
|alStackTrace|The stack trace in AL.|
|component|**Dynamics 365 Business Central Server**|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|deprecatedKeys|Specifies a comma-separated list of all the keys that have been deprecated. The keys in this list are still supported but will eventually be removed in the next major release. We recommend that update any queries that use these keys to use the new key name.|
|eventId|**RT0013**|
|environmentName|Specifies the name of the tenant environment. See [Managing Environments](tenant-admin-center-environments.md).|
|environmentType|Specifies the environment type for the tenant, such as **Production**, **Sandbox**, **Trial**. See [Environment Types](tenant-admin-center-environments.md#types-of-environments)|
|extensionId|Specifies the AppID of the extension that was involved in the lock.|
|extensionName|Specifies the name of the extension that was involved in the lock.|
|extensionVersion|Specifies the version of that was involved in the lock.|
|sessionId|Specifies the ID of the session that requested the lock. |
|snapshotId|Specifies the ID of the database snapshot. All messages in the snapshot share this ID.  |
|sqlLockRequestMode|Specifies the lock mode that determines how concurrent transactions can access the resource. For more information, see [Lock Modes](/previous-versions/sql/sql-server-2008-r2/ms175519(v=sql.105)). |
|sqlLockRequestStatus|Specifies the current status of the lock, which can be one of the following values:<ul><li>`CNVRT` - means that the lock is transitioning from another mode, but the conversion is blocked by another process that holds a lock with a conflicting mode.</li><li>`GRANT` - means that the lock is active.</li><li>`WAIT`- means that the lock is blocked by another process that holds a lock with a conflicting mode.</li></ul> |
|sqlLockResourceType|Specifies the database resource affected by the lock. For example, `DATABASE`, `FILE`, `OBJECT`, `PAGE`, `KEY`, and more. |
|sqlServerSessionId|Specifies the ID of the SQL server session that requested the lock. |
|sqlTableName|Specifies the name of table on which the lock was held.|
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|

### Sample KQL code 
This KQL code can help you get started analyzing database lock snapshots:

```kql
traces 
| where timestamp > ago(2d) // adjust to your needs
| where customDimensions has 'RT0013'
| where customDimensions.eventId == 'RT0013'
| project timestamp
, aadTenantId = customDimensions.aadTenantId
, environmentType = customDimensions.environmentType
, environmentName = customDimensions.environmentName
, companyName = customDimensions.companyName
, snapshotId = customDimensions.snapshotId
, clientTypeHoldingLock = customDimensions.clientType
, alObjectTypeHoldingLock = customDimensions.alObjectType
, alObjectIdHoldingLock = customDimensions.alObjectId
, alObjectNameHoldingLock = customDimensions.alObjectName
, alStackTraceHoldingLock = customDimensions.alStackTrace
, extensionNameHoldingLock = customDimensions.extensionName
, extensionIdHoldingLock = customDimensions.extensionId
, extensionVersionHoldingLock = customDimensions.extensionVersion
, extensionPublisherHoldingLock = customDimensions.extensionPublisher
, sqlTableLocked = customDimensions.sqlTableName
, sqlLockResourceType = customDimensions.sqlLockResourceType
, sqlLockRequestMode = customDimensions.sqlLockRequestMode
, sqlLockRequestStatus = customDimensions.sqlLockRequestStatus
, sqlServerSessionId = customDimensions.sqlServerSessionId
, alSessionIdHoldingLock = customDimensions.sessionId
```


## Troubleshooting locking issues with telemetry

The telemetry you see for lock timeouts only represents the session that is the victim in a locking issue, not the sessions that hold the locks. When analyzing database lock timeout telemetry, it's therefore useful to look at combined data from the **Database lock timed out** event and **Database lock snapshot** events. You might be lucky that the snapshot has captured information from locks that were held when the lock timeout occurred.

You can combine data from different events by using *joins* in your Kusto queries. For an example, see [LockTimeouts.kql](https://github.com/microsoft/BCTech/blob/master/samples/AppInsights/KQL/Queries/ExampleQueriesForEachArea/LockTimeouts.kql) in the **Microsoft/BCTech** repository on GitHub. For more general information about using joins, see [Joins in Azure Monitor log queries](/azure/azure-monitor/log-query/joins) in the Microsoft Azure documentation.


## See also

[Monitoring and Analyzing Telemetry](telemetry-overview.md)  
[Enable Sending Telemetry to Application Insights](telemetry-enable-application-insights.md)  
