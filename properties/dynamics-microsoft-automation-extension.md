---
title: extension resource type | Microsoft Docs
description: A extension in Dynamics 365 Business Central.
documentationcenter: ''
author: henrikwh

ms.topic: reference
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/01/2020
ms.author: solsen
---

# extension Resource Type
Represents an extension resource type in [!INCLUDE[d365fin_long_md](../developer/includes/d365fin_long_md.md)]. 

## Methods
| Method         | Return Type  |Description|
|:---------------|:-------------|:----------|
|[GET extensions](dynamics-microsoft-automation-extension-get.md)|extension|Gets all published extensions.|

## Bound Actions

| Actions         | Return Type  |Description|
|:---------------|:-------------|:----------|
|[Microsoft.NAV.install](dynamics-microsoft-automation-extension-post.md)|none|Installs a published extension.|
|[Microsoft.NAV.uninstall](dynamics-microsoft-automation-extension-post.md)|none|Uninstalls an extension.|
|[Microsoft.NAV.uninstallAndDeleteExtensionData](dynamics-microsoft-automation-extension-post.md)|none|Uninstalls an extension and deletes extension data.|

## Properties

| Property	      | Type |Description                             |
|:----------------|:-----|:---------------------------------------|
|packageId        |GUID  |The unique ID of the package. Read-Only.|
|displayName      |string|Specifies the extension name.                  |
|publisher|string|Specifies the publisher of the extension.                  |
|versionMajor     |int|Major version of the extension.     |
|versionMinor     |int|Minor version of the extension.     |
|isInstalled|boolean|Specifies the installation status.|

## Relationships
None

## JSON representation
Here is a JSON representation of the extension.

```json
{
    "packageId": "bbd8e783-238a-4a72-8071-c0d4ea8884e7",
    "displayName": "Sales and Inventory Forecast",
    "publisher": "Microsoft",
    "versionMajor": 2,
    "versionMinor": 0,
    "isInstalled": true
}
```

## See Also 
[Introduction to Automation APIs](itpro-introduction-to-automation-apis.md)  
[Get Extensions](dynamics-microsoft-automation-extension-get.md)  
[Install extension](dynamics-microsoft-automation-extension-post.md)  
[Uninstall extension](dynamics-microsoft-automation-extension-post.md)  
