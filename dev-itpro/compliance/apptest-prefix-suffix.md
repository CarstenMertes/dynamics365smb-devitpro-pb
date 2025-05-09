---
title: Prefix and suffix for naming in extensions
description: Use a prefix or suffix for names in your extension. This rule applies to all objects, including tables, pages, and codeunits. This topic explains the benefits and guidelines for using a prefix or suffix."
author: SusanneWindfeldPedersen
ms.date: 04/11/2023
ms.topic: how-to
ms.author: freddyk
ms.reviewer: jswymer
---

# Benefits and guidelines for using a prefix or suffix

In your extension, the name of each new application object (table, page, codeunit), must contain a prefix or suffix. This rule applies to all objects. You can use the [Caption](../developer/properties/devenv-caption-property.md) values for what you decide to display to the user. When you modify a core Dynamics 365 object using a table extension or a page extension, the prefix/suffix must be defined at the control/field/action/group level.

## Benefits

The use of affixes reduces name collisions with objects defined in other extensions.

Environments that have extensions with name collisions can experience issues when deploying new extensions, when upgrading the environment, or when creating a sandbox as a copy of the current environment (for production environments).

## General rules

- The prefix/suffix must be at exactly three characters
- The object/field name must start or end with the prefix/suffix
- If a conflict arises, the one who registered the prefix/suffix always wins
- For your own objects and extension objects, you can either use a namespace of at least two levels or you must set the prefix/suffix at the top object level
- For pages/tables/enums/reports/permissionsets in the base application or other apps that you extend, you must set the prefix/suffix at the control/field/action/procedure/values/dataitem/column level
- For extension objects that extend objects from the same publisher as your app, affixes aren't needed at the control/field/action/procedure/values/dataitem/column level
- Use the [AppSourceCop](../developer/devenv-using-code-analysis-tool.md) tool to find all missing prefixes and/or suffixes. Configuration options for this tool can be found [here](../developer/analyzers/appsourcecop.md). The Rules section explains the different checks that the analyzer does. For prefix/suffix detection, refer to the Configuration section. It explains how to set your affixes in the AppSourceCop.json file.

## Affixes requirements for extensions

### For AppSource extensions

> [!IMPORTANT]  
> The use of affixes for object names is required for AppSource submissions as part of the [Technical Validation Checklist](../developer/devenv-checklist-submission.md).


In order to meet the requirements for the AppSource technical validation, you must have a three letters affix registered for your extension publisher, and you must use the affix in your extension.

If you don't have any affixes registered yet, contact us at [d365val@microsoft.com](mailto:d365val@microsoft.com?subject=Affix%20Registration%20Request&body=MPN%20ID%3A%20%3CMPN%20ID%20in%20Partner%20Center%3E%0APublisher%20Name%3A%20%3Cthe%20publisher%20name%20that%20you%20use%20in%20your%20extensions%20(in%20the%20app.json%20file)%3E%0AAffixes%3A%20%3Cfive%20affix%20suggestions%20(each%20exactly%20three%20characters%20long)%20in%20order%20of%20priority%3E) and provide us with the following information to reserve the prefix/suffix of your choosing:

- Your MPN ID,
- The publisher name that you use in your extensions (in the app.json file),
- You must provide at least five affix suggestions. Each affix must be exactly three characters.

> [!NOTE]
> Affixes aren't case-sensitive, which means that for example "ABC", "abc", and "AbC" are treated as the same affix. Providing both "ABC" and "abc" counts as only one of your suggestions.

Note, that you aren't required to change any already registered affixes; you can continue using these affixes. The guidelines only apply to new registrations.

### For per-tenant extensions

Per-tenant extensions aren't required to use a prefix or suffix, but we strongly recommend that you do so. You can use *pte* as prefix or suffix to avoid conflicts with AppSource apps or base objects.

> [!NOTE]
> If your per-tenant extension causes a conflict with a new object in the base application or an updated AppSource app, then the per-tenant extension will be required to make the change.

## Examples of objects with affixes or namespaces

Use a two-level namespace for your top-level objects to avoid needing affixes. Otherwise, declare your objects with a prefix or suffix as shown in the following examples.

### Table

```AL
namespace MyUniquePublisherName.Sales;

table 70000000 Salesperson
{
    Caption = 'Sales Person';
}
```

```AL
table 70000000 MyPrefixSalesperson
{
    Caption = 'Sales Person';
}
```

```AL
table 70000001 SalespersonMySuffix
{
    Caption = 'Sales Person';
}
```

### Page

```AL
namespace MyUniquePublisherName.Sales;

page 70000000 Salesperson
{
    Caption = 'Sales Person';
}
```

```AL
page 70000000 MyPrefixSalesperson
{
    Caption = 'Sales Person';
}
```

```AL
page 70000001 SalespersonMySuffix
{
    Caption = 'Sales Person';
}
```

### Page extension objects

For extension objects which are extending other publishers' objects, affixes are required.

```AL
actions
{
    addafter(ApprovalEntries)
    {
        action(MyPrefixVacation)
        {
            Caption = 'Vacation';
        }
    }
}
```

```AL
actions
{
    addafter(ApprovalEntries)
    {
        action(VacationMySuffix)
        {
            Caption = 'Vacation';
        }
    }
}
```

### Codeunit
```AL
namespace MyUniquePublisherName.Sales;

codeunit 70000000 Salesperson
```

```AL
codeunit 70000000 MyPrefixSalesperson
```

```AL
codeunit 70000001 SalespersonMySuffix
```

## Examples – per-tenant extension

Let's say that you're creating a per-tenant extension, **myext** and you want to future-proof the naming by applying the prefix or suffix *pte*, which you aren't required to register.  

Let's look at some examples:

| Prefixes                   | Suffixes                   |
|----------------------------|----------------------------|
| pte-myext-salespersoncode  | salespersoncode-myext-pte  |
| pte_myext_salespersoncode  | salespersoncode_myext_pte  |
| pte myext salesperson code | salesperson code myext pte |
| pteMyExtSalesPersonCode    | SalesPersonCodeMyExtPte    |

## Examples - AppSource app

Alternatively, let's say that your company is Fabrikam, and you're building an app called *Rentals*. First thing, you email [d365val@microsoft.com](mailto:d365val@microsoft.com) and register *fab* as your company affix.  

A registered affix must be three letters, no more, no less, and you must provide the publisher name, which you use in the app.json file when you apply for an affix.  

Once you get confirmation from Microsoft, you're free to use object and field names that start with *fab* or end with *fab*. Here are some examples:

| Prefixes               | Suffixes               |
|------------------------|------------------------|
| fab-salespersoncode | salespersoncode-fab |
| fab_salespersoncode | salespersoncode_fab |
| fab salespersoncode | salespersoncode fab |
| FabSalesPersonCode  | SalesPersonCodefab  |

At Fabrikam, another team is building another app, so you request a special affix for your app so that the two Fabrikam apps can be kept apart. In this scenario, you don't have to register anything with Microsoft, as long as you do this with your company affix. Here are some examples:

| Prefixes               | Suffixes               |
|------------------------|------------------------|
|fab-rentals-salespersoncode|salespersoncode-rentals-fab|
|fab_rentals_salespersoncode|salespersoncode_rentals_fab|
|fab rentals salesperson code|salesperson code rentals fab|
|FabRentalsSalesPersonCode|SalesPersonCodeRentalsfab|

In this scenario, your AppSourceCop.json file configuration specifies `fab-rentals` and `rentals-fab` as values for `mandatoryaffixes`, even though only *fab* was registered with Microsoft.

## Related information

[Checklist for submitting your app](../developer/devenv-checklist-submission.md)  
[Rules and guidelines for AL code](apptest-overview.md)  
