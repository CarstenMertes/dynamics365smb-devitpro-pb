---
author: solsen
ms.topic: include
ms.date: 08/23/2023
ms.author: solsen
---
When an environment is created as a copy of another environment, a number of precautions are taken for that copy:

- Tasks in the job queue are automatically stopped  

    To see which scheduled jobs are stopped, and to decide which jobs to restart in the new environment, go to the **Scheduled Tasks** page in [!INCLUDE [prod_short](prod_short.md)]. There, you can set tasks to be ready to run in the job queue. However, only tasks that are marked as belonging to the current environment can run. For more information, see [View Scheduled Tasks](/dynamics365/business-central/admin-job-queues-schedule-tasks#view-scheduled-tasks) in the business functionality content.  
- Any base application integration settings are cleared  
- Any irreversible features that were enabled in the original environment will also be turned on in the copy. For more information, see [Features that can't be turned off](../../administration/feature-management.md#features-that-cant-be-turned-off).  
- Development extensions that are published from [AL-Go for GitHub](https://aka.ms/AL-Go) or Azure DevOps and any extensions that depend on them are uninstalled when the source environment is a sandbox. Any data that was created in the original environment by the extensions that are now uninstalled in the copy will not be deleted. Any updates to per-tenant extensions that are slotted to be upgraded with the next minor or major upgrade will be retained.
- Outbound HTTP calls from extensions are blocked by default and must be approved for each extension, otherwise instead of an external call, the system will display the following error message: *The request was blocked by the runtime to prevent accidental use of production services*.  

    To enable outbound HTTP calls, go to the **Extension Management** page in [!INCLUDE [prod_short](prod_short.md)], and choose **Configure**. Then, on the **Extension Settings** page, make sure that **Allow HttpClient Requests** is selected. This setting must be enabled for each extension, including libraries.  
- Any action taken for the purpose of complying with privacy laws and regulations must be handled separately and repeated for the environment. There is no synchronization with the original environment after the copy has been created.  

    The internal administrator has the same tools and responsibilities for the copy as they do for the original environment. As a data processor, [!INCLUDE [prod_short](prod_short.md)] offers the same level of data protection and data handling restrictions to all types of environments, both sandboxes and production environments.  
    
[!INCLUDE [create copy-restore-cleanup-operations](copy-restore-cleanup-operations.md)]

- The environment settings set in the admin center, including the Application Insights connection string and update window, are copied over to the target environment. If you don't want the target environment to emit telemetry to the same Application Insights resource as the source environment, you can remove or change the connection string after the copy completes or use [Data Collection Rules](/dynamics365/business-central/dev-itpro/administration/telemetry-control-cost#use-data-collection-rules-dcr) on the Application Insights resource to filter out telemetry from any environments from which you don't want to collect telemetry on that resource.
