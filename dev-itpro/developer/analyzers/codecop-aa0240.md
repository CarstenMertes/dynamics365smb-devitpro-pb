---
title: "CodeCop Warning AA0240"
description: "Email and Phone No must not be present in any part of the source code that might be collected as telemetry data."
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
# CodeCop Warning AA0240
Email and Phone No must not be present in any part of the source code.

## Description
Email and Phone No must not be present in any part of the source code that might be collected as telemetry data.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule
To prevent exposing personal data, make sure that Email or Phone No information is not available in the source code because that might be collected as telemetry data.

## Bad code example
```AL
table 18 Customer
{
   ...
   fields
   {
      field(1; Email; Text[50]){ CaptionML = ENU = 'john.smith@contoso.com'; }
   }
   ...
}
```

## Good code example
```AL
table 18 Customer
{
   ...
   fields
   {
      field(1; Email; Text[50]){ CaptionML = ENU = 'Email'; }
   }
   ...
}
```
## Remarks

The following elements are checked in code: 

- Object names
- Table captions
- Table field names
- Table field captions
- Page captions
- Page field names
- Page field captions
- Page field tooltips
- Value of labels (in declaration)
- Value of text constants
- Translation files (tags `<source>`, `<target>`, `<note>`)
- App manifest file (Name, Brief, Description, Publisher)

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  