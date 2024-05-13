---
title: Analyzing configuration package lifecycle trace telemetry
description: Learn about the telemetry for configuration package telemetry for Azure Application Insights.  
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 12/20/2023
ms.author: jswymer
---

# Analyzing configuration package telemetry

**APPLIES TO:** [!INCLUDE[prod_short](../includes/prod_short.md)] 2020 release wave 2, version 17.2, and later

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

Configuration package telemetry gathers data about the following operations on configuration packages:

- Export
- Import
- Apply 
- Delete

For information about working with configuration packages, see [Prepare a Configuration Package](/dynamics365/business-central/admin-how-to-prepare-a-configuration-package) in the [!INCLUDE[prod_short](../includes/prod_short.md)] Application Help.

## <a name="other"></a>**Common custom dimensions**
The following table explains custom dimensions that are common to all configuration package traces. 

|Dimension|Description or value|
|---------|-----|
|aadTenantId|Specifies the Microsoft Entra tenant ID used for Microsoft Entra authentication. For on-premises, if you aren't using Microsoft Entra authentication, this value is **common**. |
|alCategory|**RapidStart**|
|alDataClassification|**SystemMetadata**|
|clientType|Specifies the type of client that executed the SQL Statement, such as **Background** or **Web**. For a list of the client types, see [ClientType Option Type](../developer/methods-auto/clienttype/clienttype-option.md). Added in version 20.0.|
|companyName|The name of the company where the operation is applied. Added in version 20.0. |
|component|**Dynamics 365 Business Central Server**.|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|environmentType|Specifies the environment type for the tenant, such as **Production**, **Sandbox**, **Trial**. See [Environment Types](tenant-admin-center-environments.md#types-of-environments).|
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|


## <a name="exportstarted"></a>Configuration package export started

Occurs when an export operation on a configuration package is started.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package export started: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3F**|
|alExecutionId|Specifies the ID of the export operation.|
|alPackageCode|Specifies the Code of the configuration package being exported.|


## <a name="exportsuccessful"></a>Configuration package exported successfully

Occurs when an export operation on a configuration package completes successfully. 

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package exported successfully: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3G**|
|alExecutionId|Specifies the ID of the export operation.|
|alExecutionTimeInMs|Specifies the number of milliseconds it took to complete the export operation.|
|alPackageCode|Specifies the Code of the configuration package that was exported.|
|[See common custom dimensions](#other)||


## <a name="importstarted"></a>Configuration package import started

Occurs when an import operation on a configuration package is started. 

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package import started: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |


### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3H**|
|alExecutionId|Specifies the ID of the import operation.|
|alPackageCode|Specifies the ID of the configuration package being imported.|
|[See common custom dimensions](#other)||


## <a name="importsuccessful"></a>Configuration package imported successfully

Occurs when an import operation on a configuration package completes successfully.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package imported successfully: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3I**|
|alExecutionTimeInMs|Specifies the number of milliseconds it took to complete the import operation.|
|alExecutionId|Specifies the ID of the import operation.|
|alPackageCode|Specifies the ID of the configuration package that was imported.|
|[See common custom dimensions](#other)||


## <a name="applystarted"></a>Configuration package apply started

Occurs when an apply operation on a configuration package is started.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package apply started: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3N**|
|alExecutionId|Specifies the ID of the apply operation.|
|alPackageCode|Specifies the Code of the configuration package being applied.|
|[See common custom dimensions](#other)||


## <a name="applysuccessful"></a>Configuration package applied successfully

Occurs when an apply operation on a configuration package completes successfully.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package applied successfully: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3O**|
|alExecutionId|Specifies the ID of the apply operation.|
|alExecutionTimeInMs|Specifies the number of milliseconds it took to complete the apply operation.|
|alErrorCount|Specifies the number of errors that occurred when applying the configuration package.|
|alFieldCount|Specifies the number of fields that were included in the migration table of the applied configuration package. |
|alPackageCode|Specifies the Code of the configuration package that was applied.|
|alRecordCount|Specifies the number of records that were included in the applied configuration package.|
|[See common custom dimensions](#other)||


## <a name="deletesuccessful"></a>Configuration package deleted successfully

Occurs when a configuration package is deleted successfully.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Configuration package deleted successfully: {alPackageCode}**|
|severityLevel|**1**|
|user_Id|[!INCLUDE[user_Id](../includes/include-telemetry-user-id.md)] |

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**AL0000E3P**|
|alPackageCode|Specifies the Code of the configuration package that was deleted.|
|[See common custom dimensions](#other)||


## See also

[Monitoring and Analyzing Telemetry](telemetry-overview.md)  
[Enable Sending Telemetry to Application Insights](telemetry-enable-application-insights.md)  
[Prepare a Configuration Package](/dynamics365/business-central/admin-how-to-prepare-a-configuration-package) in the [!INCLUDE[prod_short](../includes/prod_short.md)]  
