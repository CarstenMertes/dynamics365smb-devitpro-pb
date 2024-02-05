---
title: "AppSourceCop Hidden AS0055"
description: "The AppSourceCop configuration must specify the list of countries/regions targeted by the application."
ms.author: solsen
ms.custom: na
ms.date: 12/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Hidden AS0055
The AppSourceCop configuration must specify the list of countries/regions targeted by the application

## Description
The AppSourceCop configuration must specify the list of countries/regions targeted by the application.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
In the AppSourceCop.json file specify the setting as shown in the example below:
```json
"supportedCountries": ["DE", "AT"];
```

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  