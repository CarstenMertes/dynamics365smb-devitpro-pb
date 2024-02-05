---
title: "AppSourceCop Hidden AS0076"
description: "Obsolete Tag must have a specific format."
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
# AppSourceCop Hidden AS0076
Obsolete Tag format.

## Description
Obsolete Tag must have a specific format.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

The ObsoleteTag [property](../properties/devenv-obsoletetag-property.md) and [attribute parameter](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute) values are not validated by the AL compiler. However it is possible to setup the AppSourceCop to verify them using a Regex expression.

## Setting up AppSourceCop to validate the Obsolete Tag

### Enabling the rule using a ruleset

The diagnostics for rule AS0076 are hidden by default, so you first have to use a [ruleset](../devenv-rule-set-syntax-for-code-analysis-tools.md) in order to surface them.

For example, the following ruleset turns the diagnostic for rule AS0076 into an error.

```json
{
    "name": "My custom ruleset",
    "rules": [
        {
            "id": "AS0076",
            "action": "Error",
            "justification": "Validating that obsolete tags are formated properly is important"
        }
    ]
}
```

```json
{
    "al.ruleSetPath": "custom.ruleset.json"
}
```

> [!NOTE]  
> In order to fully validate obsolete properties and attributes, we recommend enabling the rules [AS0072](appsourcecop-as0072.md), [AS0073](appsourcecop-as0073.md), [AS0074](appsourcecop-as0074.md), [AS0075](appsourcecop-as0075.md), and [AS0076](appsourcecop-as0076.md).

### Setting up the AppSourceCop.json

By default, the rule will validate that the specified obsolete tags are following the pattern `(\\d+)\\.(\\d+)`.

However, it is possible to specify a custom pattern as a regular expression using the `obsoleteTagPattern` property in the AppSourceCop.json.
The property `obsoleteTagPatternDescription` can be used in order to provide a human readable version of the expected pattern. 
The pattern description is used when reporting diagnostics.

```json
{
    "obsoleteTagPattern": "^[A-Z]{3}$",
    "obsoleteTagPatternDescription": "Three upper case letters"
}
```

## How to fix this diagnostic?

In order to fix this diagnostic, make sure that your obsolete tags are matching the expected `obsoleteTagPattern`.

For instance, when using the default obsolete tag pattern, two diagnostics will be reported by rule AS0076 because the obsolete tag property and the obsolete tag attribute parameter values do not respect the format Major.Minor.

```AL
codeunit 50100 MyCodeunit
{
    ObsoleteState = Pending;
    ObsoleteReason = 'Use codeunit X instead.';
    ObsoleteTag = 'Next major';

    [Obsolete('Use function Y instead', 'Next spring')]
    procedure MyProcedure()
    begin
    end;
}
```

The code should be fixed a follows:

```AL
codeunit 50100 MyCodeunit
{
    ObsoleteState = Pending;
    ObsoleteReason = 'Use codeunit X instead.';
    ObsoleteTag = '17.0';

    [Obsolete('Use function Y instead', '17.0')]
    procedure MyProcedure()
    begin
    end;
}
```

> [!NOTE]  
> The version to specify when using the default obsolete tag pattern is validated by the rules [AS0072](appsourcecop-as0072.md) and [AS0074](appsourcecop-as0074.md).

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)