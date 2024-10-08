---
title: "AppSourceCop Error AS0084"
description: "The ID range assigned to the extension must be within the range allowed for AppSource applications."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Error AS0084
The ID range assigned to the extension must be within the allowed range

## Description
The ID range assigned to the extension must be within the range allowed for AppSource applications.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This rule validates that the ID range specified in the `app.json` of your extension is contained within the range allowed for AppSource application.

For more information about the object ID ranges in Business Central, see [Object ranges in Dynamics 365 Business Central](../devenv-object-ranges.md).

For more information about the properties in the `app.json` file, see [JSON files](../devenv-json-files.md).

## How to fix this diagnostic?

If you're targeting the AppSource marketplace, you need to update the ID range in your `app.json` file with the one that Microsoft provided you with.

> [!NOTE]  
> If you're targeting the AppSource marketplace and don't have an ID range assigned, follow the steps defined in [Get started with building apps](../readiness/get-started.md).

If you aren't targeting the AppSource marketplace, you can suppress this rule using [rulesets](../devenv-using-code-analysis-tool-with-rule-set.md).

## Code example triggering the rule

### The ID range is outside the range allowed for AppSource applications

The `app.json` file of the extension:
```json
{
   [...]
   "idRanges": [
    {
      "from": 50100,
      "to": 50149
    }
    [...]
  ]
}
```

The ID range specified isn't contained in the range allowed for AppSource applications. 

### The ID range isn't specified

The `app.json` file of the extension:
```json
{
  [...]
}
```

If the ID range is not specified, the default ID range is used. As the default ID range spans outside the allowed ID range for AppSource applications, a diagnostic will be reported.

## Code example not triggering the rule

The `app.json` file of the extension:
```json
{
   [...]
   "idRanges": [
    {
      "from": 1000000,
      "to": 1000100
    }
    [...]
  ]
}
```

The ID range specified is included in the range allowed for AppSource applications. 

## Related information

[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
