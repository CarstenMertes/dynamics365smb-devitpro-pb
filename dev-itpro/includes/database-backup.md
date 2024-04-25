---
author: edupont04

ms.topic: include
ms.date: 05/03/2023
ms.author: edupont
---
Databases are protected by automatic backups that are kept for 28 days. The backup includes data from any production and sandbox environments that the database contains. Administrators of a [!INCLUDE [prod_short](prod_short.md)] tenant can't directly access or manage these backups because they're managed automatically by Microsoft. But admins can restore their environments to a specific point in time in the past using the [!INCLUDE [prod_short](prod_short.md)] admin center. For more information, see [Restoring an environment](../administration/tenant-admin-center-backup-restore.md) and [Automated backups - Azure SQL Database](/azure/azure-sql/database/automated-backups-overview).
