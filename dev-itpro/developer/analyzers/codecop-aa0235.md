---
title: "CodeCop Info AA0235"
description: "When using trigger 'OnInstallAppPerCompany' in a codeunit with 'Subtype = Install' you should also add a 'Company-Initialize'::'OnCompanyInitialize' event subscriber to ensure that new companies also have the correct setup."
ms.author: solsen
ms.custom: na
ms.date: 12/09/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# CodeCop Info AA0235
When using 'OnInstallAppPerCompany' you should also add 'Company-Initialize'::'OnCompanyInitialize' event subscriber.

## Description
When using trigger 'OnInstallAppPerCompany' in a codeunit with 'Subtype = Install' you should also add a 'Company-Initialize'::'OnCompanyInitialize' event subscriber to ensure that new companies also have the correct setup.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule
'OnInstallAppPerCompany' is only run on companies that exist when installing the extension. Many extensions were missing a 'OnCompanyInitialize' subscription, so companies that were created after the extension installation were missing setup that the extension should do. For example, insertion of records in some tables was done only for existing companies and not for new ones.

## Bad code example
```AL
codeunit 1160 "AP Install"
{
   Subtype = Install;

   trigger OnInstallAppPerCompany()

   begin
   ...
   end;
}
```

## Good code example
```AL
codeunit 1160 "AP Install"
{
   Subtype = Install;

   trigger OnInstallAppPerCompany()

   begin
   ...
   end;

   [EventSubscriber(ObjectType::Codeunit, Codeunit::"Company - Initialize", 'OnCompanyInitialize', '', false, false)]
   local procedure CompanyInitialize()
   begin
   ...
   end;
}
```

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  