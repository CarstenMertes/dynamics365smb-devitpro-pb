---
title: Adding help links from pages, reports, and XMLports
description: This article shows how to specify the Help link on pages, reports and XMLports in AL for Business Central.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 05/23/2022
ms.reviewer: solsen
ms.topic: conceptual
ms.author: solsen
---

# Adding help links from pages, reports, and XMLports

When creating new pages, you can specify which Help file to open if the user selects the *Learn more* links in the UI of [!INCLUDE[prod_short](includes/prod_short.md)].  

The context-sensitive Help link is generated based on a configuration setting in the `app.json` file and the name of the relevant Help file that you specify as part of the metadata for the page object. For more information, see [Configure Context-Sensitive Help](../help/context-sensitive-help.md).  

## Examples

The following examples show how you can specify the *ContextSensitiveHelpPage* property from new pages, reports, and XMLports:

```AL
page 50100 MyPageWithHelp
{
    ContextSensitiveHelpPage = 'sales-rewards';
}
```

```AL
report 50100 MyReportWithHelp
{
    requestpage
    {
        ContextSensitiveHelpPage = 'sales-rewards';
    }
}
```

```AL
xmlport 50100 XmlPortWithHelp
{
    requestpage
    {
        ContextSensitiveHelpPage = 'sales-rewards';
    }
}
```

In all three examples, the [ContextSensitiveHelpPage property](properties/devenv-contextsensitivehelppage-property.md) is set to point at the same Help file. This is because all three example objects support the same feature that is explained in the *sales-rewards* Help article. In your app, you can choose to structure the Help differently.  

## See Also

[Configure Context-Sensitive Help](../help/context-sensitive-help.md)  
[Translating Base App Help](devenv-translate-base-app-help.md)  
[JSON Files](devenv-json-files.md#appjson-file)  
[Page Object](devenv-page-object.md)  
[Report Object](devenv-report-object.md)  
[XMLport Object](devenv-xmlport-object.md)  
[Table Object](devenv-table-object.md)  
[ContextSensitiveHelpPage Property](properties/devenv-contextsensitivehelppage-property.md)  
