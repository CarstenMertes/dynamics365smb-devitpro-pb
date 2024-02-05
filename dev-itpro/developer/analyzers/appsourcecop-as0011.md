---
title: "AppSourceCop Error AS0011"
description: "An affix is required."
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
# AppSourceCop Error AS0011
An affix is required

## Description
An affix is required.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

In order to avoid name clashes for objects added by your extension and objects added by other extensions, an affix must be prepended or appended to the name of all new application objects, extension objects, and fields. For more information, see [Benefits and Guidelines for using a Prefix or Suffix](../../compliance/apptest-prefix-suffix.md).

### Using the property mandatoryAffixes

The rule validates that at least one of the affixes specified in the `mandatoryAffixes` property of the `AppSourceCop.json` file is used either at prefix or at suffix on identifier names of new elements.

|Setting|Mandatory|Value|
|-------|---------|-----|
|mandatoryAffixes|No|Affixes that must be prepended or appended to the name of all new application objects, extension objects, and fields.|

The `mandatoryAffixes` property expects to receive an array of string as follows:

```json
{
    "mandatoryAffixes": [ "Foo", "Bar" ]
}
```

### Using the properties mandatoryPrefix and mandatorySuffix

In order to preserve backward compatibility, the properties `mandatoryPrefix` and `mandatorySuffix` are still supported by the AppSourceCop.

Both properties expect to receive a string as follows:

```json
{
    "mandatoryPrefix": "Prefix",
    "mandatorySuffix": "Suffix"
}
```

However, their meaning has been modified to be closer to the new `mandatoryAffixes` property. The mandatory prefix and mandatory suffix properties are now both defining an affix that can be used either as prefix or as suffix.

As a consequence, we encourage you to use the new property `mandatoryAffixes` that offers more flexibility by allowing you to define more than two affixes, but also a more meaningful name .

## How to fix this diagnostic?

> [!NOTE]  
> If you are targeting the AppSource marketplace and do not have affixes registered, follow the steps defined in [Get Started with Building Apps](../readiness/get-started.md).

If you are not targeting the AppSource marketplace, you can suppress this rule using [rulesets](../devenv-using-code-analysis-tool-with-rule-set.md).

### For new objects

For objects that are introduced with the current version of the extension, appending one of the mandatory affixes to the object's name will fix the diagnostic.
Renaming objects which are not part of the baseline is allowed.

### For existing objects

For objects which already exist in the version of the extension used as baseline, it is not possible to rename them. It is therefore not possible to append one of the mandatory affixes. Instead, the offending object should be deprecated using the [ObsoleteState](../properties/devenv-obsoletestate-property.md) property and a new object whose name has one of the mandatory affixes should be introduced.

> [!NOTE]  
> The lack of affixes for enum values defined in enum extensions is reported as a warning with [AS0098](appsourcecop-as0098.md) if the enum value is already defined in your baseline extension. If the enum value is not defined in your baseline extension, it is reported as an error with [AS0011](appsourcecop-as0011.md). Make sure to specify your baseline extension in the AppSourceCop.json file.

#### Example - Adding an affix to an existing codeunit

For instance, if the baseline of the extension contains a codeunit without affix:

```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure()
    begin
        // Business logic.
    end;
}
```

The extension should be modified into:

```AL
codeunit 50100 MyCodeunit
{
    ObsoleteState = Pending;
    ObsoleteReason = 'Use Foo_MyCodeunit instead.';

    procedure MyProcedure()
    var 
        c: Codeunit Foo_MyCodeunit;
    begin
        // Re-direct calls to not break the runtime behaviour of dependent extensions.
        c.MyProcedure();
    end;
}

codeunit 50120 Foo_MyCodeunit
{
    procedure MyProcedure()
    begin
        // Business logic.
    end;
}
```

Once all dependent extensions have been updated to use the codeunit `Foo_MyCodeunit` instead of `MyCodeunit`, the codeunit `MyCodeunit` can be removed.

> [!NOTE]  
> When new objects are added to this rule, the transition can be made gradually because new objects are caught by the AS0011 rule, whereas the AS0098 rule catches existing or modified objects. The warning with the same behavior is described here: [AS0098](appsourcecop-as0098.md).

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
