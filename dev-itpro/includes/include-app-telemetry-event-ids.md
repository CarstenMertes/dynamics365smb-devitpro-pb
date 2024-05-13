| Event ID | Area | Message |
|----------|-------------|-----------------|
|AL0000LA2|Changelog configuration|[Field added to changelog configuration](../administration/telemetry-changelog-configuration-trace.md#added)|
|AL0000LA1|Changelog configuration|[Field logging changed in changelog configuration](../administration/telemetry-changelog-configuration-trace.md#changed)|
|AL0000LA3|Changelog configuration|[Field removed from changelog configuration](../administration/telemetry-changelog-configuration-trace.md#removed)|
|AL0000CTV|Email|[Email sent successfully](../administration/telemetry-email-trace.md#success)|
|AL0000CTP|Email|[Failed to send email](../administration/telemetry-email-trace.md#failed)|
|AL0000GKK|Email|[Authenticated to SMTP server](../administration/telemetry-email-trace.md#smtp_auth)|
|AL0000GKJ|Email|[Connected to SMTP server](../administration/telemetry-email-trace.md#smtp_connection)|
|AL0000GKL|Email|[Email sent (using SMTP)](../administration/telemetry-email-trace.md#smtp_sent)|
|AL0000CTE|Field monitoring| [Sensitive field value has changed: {alfieldCaption} ({alFieldNumber}) in table {altableCaption} ({alTableNumber})](../administration/telemetry-field-monitoring-trace.md#changed) |
| AL0000DD3 | Field monitoring | [Sensitive field monitor status has changed to {almonitorStatus}](../administration/telemetry-field-monitoring-trace.md#status) |
|AL0000EMW|Field monitoring |[Sensitive field added to or removed from monitor: {alfieldCaption} ({alFieldNumber}) in table {alTableCaption} ({alTableNumber})](../administration/telemetry-field-monitoring-trace.md#added)|
|AL0000E2A|Permissions|[User-defined permission set added: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#setadded)|
|AL0000E2B|Permissions|[User-defined permission set removed: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#setremoved)|
|AL0000E28 |Permissions|[Permission set link added: {alSourcePermissionSetId} -> {alLinkedPermissionSetId}](../administration/telemetry-permission-changes-trace.md#linkadded)|
|AL0000E29 |Permissions|[Permission set link removed: {alSourcePermissionSetId} -> {alLinkedPermissionSetId}](../administration/telemetry-permission-changes-trace.md#linkremoved)|
|AL0000E2C |Permissions|[Permission set assigned to user: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#assigneduser)|
|AL0000E2D |Permissions|[Permission set removed from user: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#removeduser)|
|AL0000E2E |Permissions|[Permission set assigned to user group: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#assignedusergroup)|
|AL0000E2F |Permissions|[Permission set removed from user group: {alPermissionSetId}](../administration/telemetry-permission-changes-trace.md#removedusergroup)|
|AL0000D3L |Retention Policy |[Retention Policy Log Entry Logged: {alMessageType}](../administration/telemetry-retention-policy-trace.md#info)|
|AL0000D6H |Retention Policy|[Records Deleted Using Retention Policy: Deleted {alRecordsDeleted} records from Table {alTableNo}, {alTableName}](../administration/telemetry-retention-policy-trace.md#deleted)|
|AL0000D6I|Retention Policy|[First retention policy enabled on: {alCompanyName}](../administration/telemetry-retention-policy-trace.md#first)|
|AL0000D6J|	Retention Policy|[Last retention policy disabled on: {alCompanyName}](../administration/telemetry-retention-policy-trace.md#last)|
|AL0000I74|	Azure Function Integration |[Request sent to Azure function succeeded: {Function Host}](../administration/telemetry-azure-function-integration-trace.md)|
|AL0000I75|	Azure Function Integration |[Authorization failed to Azure function: {Function Host}](../administration/telemetry-azure-function-integration-trace.md)|
|AL0000I7P|	Azure Function Integration |[Request sent to Azure function failed: {Function Host}](../administration/telemetry-azure-function-integration-trace.md)|
|AL0000DHR|	Performance Toolkit |[Performance Toolkit run started](../administration/telemetry-performance-toolkit-trace.md#started)|
|AL0000DHS|	Performance Toolkit |[Performance Toolkit run finished](../administration/telemetry-performance-toolkit-trace.md#completed)|
|AL0000DHT|	Performance Toolkit |[Performance Toolkit run cancelled](../administration/telemetry-performance-toolkit-trace.md#cancelled)|
|AL0000DGF|	Performance Toolkit |[Performance Toolkit - {BCPT Header code} - {BCPT Scenario code} - {BCPT Line status}](../administration/telemetry-performance-toolkit-trace.md#scenario)|
|AL0000EIW|Onboarding|[Onboarding Started](../administration/telemetry-onboarding-trace.md#started)|
|AL0000EIV|Onboarding|[Onboarding criteria completed: {Criteria}](../administration/telemetry-onboarding-trace.md#CriteriaCompleted)|