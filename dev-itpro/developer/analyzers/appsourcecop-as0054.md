---
title: "AppSourceCop Error AS0054"
description: "The AppSourceCop configuration must specify one of the following properties: 'mandatorySuffix', 'mandatoryPrefix', or 'mandatoryAffixes'."
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
# AppSourceCop Error AS0054
The AppSourceCop configuration must specify the set of affixes used by the application

## Description
The AppSourceCop configuration must specify one of the following properties: 'mandatorySuffix', 'mandatoryPrefix', or 'mandatoryAffixes'. The use of these affixes is validated by the AppSourceCop analyzer and helps prevent conflicts between different AppSource applications.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

In the `AppSourceCop.json` configuration file, use the `mandatorySuffix`, `mandatoryPrefix`, or `mandatoryAffixes` to specify which affixes apply for this particular extension. For example:

```json
{
    "mandatoryAffixes": [ "Foo", "Bar" ]
}
```

For more information, see [AppSourceCop Rule AS0011](appsourcecop-as0011.md).

## Registering your affixes for AppSource submissions

The use of affixes is required for extensions submitted to the AppSource marketplace, see [Technical Validation Checklist](../devenv-checklist-submission.md).

In order to register your affixes, see [Benefits and Guidelines for using a Prefix or Suffix](../../compliance/apptest-prefix-suffix.md).

## See Also  

[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)
[Benefits and Guidelines for using a Prefix or Suffix](../../compliance/apptest-prefix-suffix.md)
