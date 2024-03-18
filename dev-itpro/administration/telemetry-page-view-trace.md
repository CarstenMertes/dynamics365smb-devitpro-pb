---
title:  Page View Telemetry | Microsoft Docs
description: Learn about the page views telemetry in Business Central  
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 03/22/2022
ms.author: jswymer
---
# Analyzing Page View Telemetry

**INTRODUCED IN:** [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1, version 16.3. Available in extension telemetry from version 18.0. Available in on-premises environments from version 21.0. Query telemetry available from version 23.0.

Page view telemetry gathers data about the pages that users open in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] client. Each page view tells you how long it took to open the page, information about the user's environment, and more.

Use the data to gather statistics about system usage and also troubleshoot performance issues caused by the users' environments.

> [!NOTE]
> In Application Insights, telemetry about page views is logged to the **pageViews** table and not the **traces** table like other [!INCLUDE[prod_short](../developer/includes/prod_short.md)] traces. This also means that you can use the built-in pages in the **Usage** feature of the Application Insights to investigate how users interact with the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment. For more information, see [Usage analysis with Application Insights](/azure/azure-monitor/app/usage-overview).

## Page opened: {alObjectName}

Occurs when a page has been opened in the client.  

### General dimensions

The pageViews table is a built-in table in Application Insights. Here are some of the fields most used in analysis of the signal:

|Field|Description or value|
|---------|-----|
|client_Browser|Browser running on the client device.|
|client_OS|Operating system of the client device.|
|client_Type|Type of the client device.|
|duration| Number of milliseconds it took the application to handle the page view.|
|url|URL of the page view.|
|name|Name of the page opened in the client |
|session_id|An identifier for the session. Can be used to create a timeline of page views happening in the session|

All fields are documented here: [Application Insights PageViews Schema](/azure/azure-monitor/reference/tables/pageviews)

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|aadTenantId|[!INCLUDE[aadTenantId](../includes/include-telemetry-dimension-aadtenantid.md)]|
|alObjectId|[!INCLUDE[aadTenantId](../includes/include-telemetry-dimension-page-object-id.md)]|
|alObjectName|[!INCLUDE[objectName](../includes/include-telemetry-dimension-page-object-name.md)]|
|alObjectType|**Page**|
|appId|[!INCLUDE[appId](../includes/include-telemetry-dimension-page-app-id.md)]|
|appName|[!INCLUDE[appName](../includes/include-telemetry-dimension-page-app-name.md)]|
|appPublisher|[!INCLUDE[appPublisher](../includes/include-telemetry-dimension-page-app-publisher.md)]|
|appVersion|[!INCLUDE[appVersion](../includes/include-telemetry-dimension-page-app-version.md)]|
|clientType| [!INCLUDE[clientType](../includes/include-telemetry-dimension-client-type.md)] |
|companyName|[!INCLUDE[companyName](../includes/include-telemetry-dimension-company-name.md)]|
|component|**Dynamics 365 Business Central Server**.|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|deprecatedKeys|A comma-separated list of all the keys that have been deprecated. The keys in this list are still supported but will eventually be removed in the next major release. We recommend that update any queries that use these keys to use the new key name.|
|designerLevel|Specifies the design level in which the page was opened. This dimension provides additional insight when the `hostType` dimension is **Designer**. <ul><li>**None**<br /> The page  wasn't opened in a design mode. This value is shown when the `hostType` dimension is a value other than **Designer**</li><li>**Personalization**<br /> The page opened in the personalizing mode for tailoring the page in the user's workspace only. See [Personalize Your Workspace](/dynamics365/business-central/ui-personalization-user). </li><li>**Configuration** <br /> The page opened in customizing mode for tailoring the page for all users of a specific profile. See [Customizing Pages for Profiles](/dynamics365/business-central/ui-personalization-manage). </li><li>**Development** <br /> The page opened in design mode for developing and modifying the page from the client for all users. See [Use Designer](../developer/devenv-inclient-designer.md).</li><li>**Inspector**<br /> The page opened in page inspection mode for viewing page information like source table, source extension, and filters. See [Inspecting Pages](/dynamics365/business-central/across-inspect-page).</li><li>**All** - the page was opened in the personalization, configuration, development, and inspector modes.|
|deviceLocale|Specifies the preferred language that's configured for the device that opened the page. For example, this dimension could show the language setting of a browser used to view the page. The value is a language code, such as **en-US** or **da-DK**. |
|deviceScreenResolution|Specifies the display resolution of the device that opened the page. The value is given as {width}×{height}, with the units in pixels. For example, **1024×768** means the width is 1024 pixels and the height is 768 pixels.|
|environmentName|[!INCLUDE[environmentName](../includes/include-telemetry-dimension-environment-name.md)]|
|environmentType|[!INCLUDE[environmentType](../includes/include-telemetry-dimension-environment-type.md)]|
|eventID|**CL0001** (note that this is different from other signals where the dimension is called *eventId*)|
|expandedFastTabs|Specifies the FastTabs on the page that were expanded when the page opened.|
|factboxExpanded|Specifies whether the FactBox area was shown or hidden when the page was opened. **true** indicates that the FactBox was shown. **false** indicates that the FactBox was hidden.|
|hostType|Specifies the host that loads the page. <ul><li>**Device App**<br /> The page was loaded by a Business Central mobile app, from a desktop, tablet, or phone. </li><li>**Office add-in**<br /> The page was loaded by Office application, like Excel or Outlook.</li><li>**Designer** <br /> The page was loaded by the in-client designer, used for changing page layout. The designer has different modes. Each mode provides a different level of page customization, as specified in the `designerLevel` dimension.</li><li>**Shim Browser** <br /> The page was loaded by the UWP (Universal Windows Platform) application.</li><li>**Browser**<br /> The page was loaded by web browser, like Microsoft Edge or Google Chrome. </li></ul>|
|message|**Page opened: {alObjectName}**|
|pageIsModal|Specifies whether the page was opened as a modal page.  **true** indicates that the page was opened as a modal page; otherwise, **false**. |
|pageMode|Specifies whether the page was opened in one of the following modes: <ul><li>**View** indicates the page was opened for viewing only</li><li>**Edit** indicates the page was opened for making changes</li><li>**Create** indicates the page was opened for creating a new entity.</li><li>**Select** indicates the page was opened for selecting an existing entity.</li><li>**Delete** indicates the page was opened for deleting an entity.</li></ul>The mode in which a page opened determined by different things, like the [RunPageMode Property](../developer/properties/devenv-runpagemode-property.md) or the [URL](../developer/devenv-web-client-urls.md) used to open the page. |
|pageType|Specifies the type of page, such as **Card**, **List**, **Document**, and more. For a complete list of page types and descriptions, see [Page Types and Layouts](../developer/devenv-page-types-and-layouts.md).|
|refUri|Specifies the URI of the page.|
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|

### Sample KQL code (page views)

This KQL code can help you get started analyzing which pages users use:

```kql
// Page views (normal pages)
pageViews
| where timestamp > ago(7d) // adjust as needed
| where customDimensions.pageDataSourceType != 'Query'
| parse kind=regex client_Browser with browserName:string ' ' browserVersion:string
| project timestamp
// in which environment/company did it happen
, aadTenantId = customDimensions.aadTenantId
, environmentName = customDimensions.environmentName
, environmentType = customDimensions.environmentType
, companyName = customDimensions.companyName
// in which extension/app
, appId = customDimensions.appId
, appName = customDimensions.appName
, appPublisher = customDimensions.appPublisher
, appVersion = customDimensions.appVersion
// in which object
, alObjectId = customDimensions.alObjectId
, alObjectName = customDimensions.alObjectName
, alObjectType = customDimensions.alObjectType
// which client (browser, tablet, phone, ...)
, clientType = customDimensions.clientType
// device info
, deviceLocale = customDimensions.deviceLocale
, deviceScreenResolution = customDimensions.deviceScreenResolution
// page details
, designerLevel = customDimensions.designerLevel
, expandedFastTabs = customDimensions.expandedFastTabs
, factboxExpanded = customDimensions.factboxExpanded
, hostType = customDimensions.hostType
, pageIsModal = customDimensions.pageIsModal
, pageMode = customDimensions.pageMode
, pageType = customDimensions.pageType
, refUri = customDimensions.refUri
// all of this data is not stored in customDimensions
, browserName = iff(browserName=='Edg', 'Edge', browserName)
, browserVersion = browserVersion
, clientBrowser = client_Browser
, clientOS = client_OS
, durationInMs = duration
, location = client_CountryOrRegion
```

## Query opened

Occurs when a query has been opened in the client.

**INTRODUCED IN:** [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2, version 23.0.

### Custom dimensions

Query usage telemetry use the same dimensions as normal page views. The only difference is that the custom dimension pageDataSourceType is set to the value **Query**.

### Sample KQL code (query usage)

This KQL code can help you get started analyzing which queries users use to analyze data:

```kql
// Page views (for queries)
pageViews
| where timestamp > ago(7d) // adjust as needed
| where customDimensions.pageDataSourceType == 'Query'
| project timestamp
// in which environment/company did it happen
, aadTenantId = customDimensions.aadTenantId
, environmentName = customDimensions.environmentName
, environmentType = customDimensions.environmentType
, companyName = customDimensions.companyName
// in which extension/app
, appId = customDimensions.appId
, appName = customDimensions.appName
, appPublisher = customDimensions.appPublisher
, appVersion = customDimensions.appVersion
// in which object
, alObjectId = customDimensions.alObjectId
, alObjectName = customDimensions.alObjectName
, alObjectType = 'Query'
// copy KQL code on client type, device info, page details etc. from the KQL sample code on normal page views above
```


## See also

[Monitoring and Analyzing Telemetry](telemetry-overview.md)  
[Enable Sending Telemetry to Application Insights](telemetry-enable-application-insights.md)  
