---
title: Turn sending telemetry to application insights on or off
description: Learn how you can get richer telemetry by connecting your Business Central with Application Insights for telemetry. 
ms.author: kepontop
ms.topic: how-to
author: jswymer
ms.date: 07/23/2024
ms.custom: bap-template
ms.reviewer: jswymer
---

# Turn environment telemetry on or off

[!INCLUDE[2019_releasewave2.md](../includes/2019_releasewave2.md)]

This article describes how to set up sending telemetry data to [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] for [!INCLUDE [prod_short](../includes/prod_short.md)] online and on-premises environments.

> [!NOTE]
> For app/extension telemetry, see [Sending Extension Telemetry to Azure Application Insights](../developer/devenv-application-insights-for-extensions.md).

## <a name="appinsights"></a>Get started (set up Azure Application Insights)

1. If you don't already have one, get a subscription to [Microsoft Azure](https://azure.microsoft.com).
2. Sign in to the [Azure portal](https://portal.azure.com).
3. Create an [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource by following the guidelines at [Workspace-based Application Insights resources](/azure/azure-monitor/app/create-workspace-resource).

    [!INCLUDE [admin-appinsights-germany](../includes/admin-appinsights-germany.md)]

    The [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource can be in any Azure tenant that is accessible to your organization. For example, a delegated administrator from the reselling partner is the person analyzing the telemetry. But this person might not have access rights the customer's Azure instance. This scenario enables the partner to send the telemetry to their own [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] instance.

    > [!TIP]
    > You can use the same [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource for multiple tenants and their different environments.

    For more information, see [Create an Application Insights resource](/azure/azure-monitor/app/create-new-resource).  

4. Depending on your [!INCLUDE[prod_short](../includes/prod_short.md)] version, get the **Connection String** or **Instrumentation Key** of the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource.

    You can copy this information from the **Overview** page for resource in the Azure portal.

    - For [!INCLUDE[prod_short](../includes/prod_short.md)] 2020 release wave 2 (v17) or earlier, copy the **Instrumentation Key**.

    - For later versions, copy the **Connection String**. The maximum supported length for the connection string is 2,048 characters.

        > [!NOTE]
        > For these versions, you can use either the instrumentation key or the connection string. However, for reliability, we recommend that you use the connection string. 

        > [!NOTE]
        > Transition to using connection strings for data ingestion in Application Insights by **31 March 2025**. On 31 March 2025, technical support for instrumentation key–based global ingestion in the Application Insights feature of Azure Monitor will end. After that date, your [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resources will continue to receive data, but Microsoft no longer provide updates or customer support for instrumentation key–based global ingestion. 

### Video guidance

The following video summarizes how to store [!INCLUDE [prod_short](../includes/prod_short.md)] telemetry in Azure Application Insights.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=46f6d63d-2375-4348-96f1-1fd1b7b37ddc]

## Turn on telemetry on environments

Once you have the resource and its connection string or instrumentation key, you can enable your tenants to send telemetry to your [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource.

The way you turn on [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] depends on whether you want to connect to a [!INCLUDE [prod_short](../includes/prod_short.md)] online or [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises environment. For on-premises, if also depends on whether the [!INCLUDE[server](../developer/includes/server.md)] instance is configured as a single-tenant or multitenant instance.

### For online environments

For [!INCLUDE [prod_short](../includes/prod_short.md)] online, you can turn on telemetry on environments either from the admin center or by using the admin center API. To use the admin center, complete the following steps. For information about using the admin center API, go to [Put AppInsights key](administration-center-api_environment_settings.md#set-application-insights-key).

#### Video guidance

The following video shows how to turn on telemetry for online environments.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=e6f5a26f-7c60-4be4-9afd-6b53c7518da6]

#### From the admin center

1. In the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)], select **Environments**, and then select the environment that you want to change.

    > [!IMPORTANT]  
    > The next steps require a restart to the environment, which is triggered automatically at the end of this procedure. Plan to do this during non-working hours to avoid disruptions.
2. On the **Environment** page, the **Application Insights Key** field shows if the environment already uses application insights.

    To turn on telemetry, choose the **Define** caption, and then, in the **Set Application Insights Key** pane, choose the **Enable application insights** field and enter the instrumentation key in the **Instrumentation Key** field.  

    > [!NOTE]
    > In version 15 and 16, to turn on telemetry, choose the **Application Insights Key** action, and then specify the instrumentation key.
3. Choose the **Save** button.

### For on-premises environments (single-tenant mode)

For a single-tenant server instance of [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises, set the **Application Insights Connection String** or **Application Insights Instrumentation Key** setting of the server instance.

```powershell
Set-NAVServerConfiguration -ServerInstance BC200 -Keyname ApplicationInsightsConnectionString -Keyvalue 'InstrumentationKey=aaaaaaaa-0b0b-1c1c-2d2d-333333333333;IngestionEndpoint=https://westeurope-1.in.applicationinsights.azure.com/'
```
For more information, see [Configuring Business Central Server](configure-server-instance.md#general-settings).

### For on-premises environments (multitenant mode)

For a multitenant server instance of [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises, turn on telemetry on a per-tenant basis when you mount tenants on the [!INCLUDE[server](../developer/includes/server.md)] instance.

The [Mount-NAVTenant cmdlet](/powershell/module/microsoft.dynamics.nav.management/mount-navtenant?view=businesscentral-ps&preserve-view=true) includes the `-ApplicationInsightsConnectionString` and `-ApplicationInsightsKey` parameters. For example:

```powershell
Mount-NAVTenant -ServerInstance BC200 -Tenant tenant1 -DatabaseName "Demo Database BC (20-0)" -DatabaseServer localhost -DatabaseInstance BCDEMO -AadTenantId 'MyAadTenantId' -EnvironmentName 'MyEnvironmentName' -EnvironmentType Production -ApplicationInsightsConnectionString 'InstrumentationKey=aaaaaaaa-0b0b-1c1c-2d2d-333333333333;IngestionEndpoint=https://westeurope-1.in.applicationinsights.azure.com/'
```

Or

```powershell
Mount-NAVTenant -ServerInstance BC200 -Tenant tenant1 -DatabaseName "Demo Database BC (20-0)" -DatabaseServer localhost -DatabaseInstance BCDEMO -EnvironmentName 'MyEnvironmentName' -EnvironmentType Sandbox -ApplicationInsightsKey aaaabbbb-0000-cccc-1111-dddd2222eeee
```

If you use the same [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource for multiple environments, consider also using the parameters AadTenantId, EnvironmentName, and EnvironmentType to distinguish tenants in telemetry.

### For on-premises Docker sandbox environments

If you're using the BcContainerHelper module, specify the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] instrumentation key when you create the container. The key is used on the server instance for a single-tenant container. For a multi-tenant container, it's used on the default tenant.

```powershell
New-BcContainer `
    -accept_eula `
    -updateHosts `
    -artifactUrl (Get-BCArtifactUrl -country us) `
    -applicationInsightsKey "aaaabbbb-0000-cccc-1111-dddd2222eeee" 
```

You can specify the same or another key when creating more tenants:

```powershell
New-BcContainerTenant -tenantId "additional" -applicationInsightsKey "aaaabbbb-0000-cccc-1111-dddd2222eeee" 
```

## Turn off telemetry on environments

To turn off having telemetry sent from environments, follow the instructions above for turning on telemetry, but set the [!INCLUDE [azure-appinsights-name](../includes/azure-appinsights-name.md)] connection string or instrumentation key to a blank value.

## Troubleshooting telemetry setup

If you set up telemetry but don't get any data in [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)], then take a look at these common mistakes that others made.

1. Check that you used the correct [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] connection string. 
1. Check that you enabled telemetry in the correct environment.
1. (Only for on-premises) Check that network traffic from [!INCLUDE [prod_short](../includes/prod_short.md)] to [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] isn't blocked by a firewall or some software that is filtering outgoing calls to the ingestion endpoint. 
1. (Only for on-premises) Similar to checking network traffic, check if you block domain name service (DNS) to lookup Azure resources. 
1. (Only for on-premises) Did you restart [!INCLUDE [server](../developer/includes/server.md)] unstances after enabling telemetry?

## Assign a telemetry ID to users

To help troubleshooting problems experienced by a given [!INCLUDE[prod_short](../developer/includes/prod_short.md)] user, you can assign the user a random ID to be included in traces logged in Application Insights. This ID is a special globally unique identifier (GUID) that's only used for telemetry. It appears in the `user_Id` column in certain events, but not all. 

In [!INCLUDE[prod_short](../developer/includes/prod_short.md)] version 24 and later, the server and the browser components align on the GUIDs logged to the **user_Id** column in the *traces* and *pageViews* tables. For versions before version 24, only events logged by the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] server emit in the context of a user session. 

The [!INCLUDE [prod_short](../includes/prod_short.md)] server initially sets the telemetry ID for a user when the user is created. To change, or clear the telemetry ID on a user, set the **Telemetry ID** field on the **User Card** for the user in Business Central:

1. Sign in to [!INCLUDE [prod_short](../includes/prod_short.md)] using an administrator account.
2. Choose the ![Lightbulb that opens the Tell Me feature.](../developer/media/search_small.png "Tell me what you want to do") icon, enter **Users**, and then choose the related link.
3. Choose the user name to open the **User Card** page.
4. Select the **Telemetry ID** field ![lookup button that opens the dialog for setting the telemetry ID.](../developer/media/ellipse-button.png).

   ![Dialog for setting the telemetry ID on the user.](../developer/media/telemetry-id.png).

   - To assign or change the telemetry ID, choose **Set field to random GUID** > **OK**.
   - To clear the telemetry ID, choose **Set field to null GUID** > **OK**.

> [!NOTE]
> We recommend that a telemetry ID is assigned to all users to make it possible to troubleshoot situations that happened in the past using telemetry.

For more information on how to query the user_Id in telemetry, see [KQL example - following telemetry events for a user](./telemetry-analyze-with-kql.md#kql-example---following-telemetry-events-for-a-user).

## Cleaning up settings

If the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource is tied to your partner account, and you end the relationship with a customer where telemetry is set up based on your account's instrumentation key, you must remove the instrumentation key while you still have access to that customer's [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)].

It's good practice to change all user telemetry IDs at the end of the relationship with the customer. This practice removes traceability to users for all data in the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource.

## Related information

[Sending Extension Telemetry to Azure Application Insights](../developer/devenv-application-insights-for-extensions.md)  
[Environment Telemetry](tenant-admin-center-telemetry.md)  
[Analyze Telemetry with KQL](telemetry-analyze-with-kql.md)  
[Telemetry FAQ](telemetry-faq.md)  
[Telemetry overview](telemetry-overview.md)  
