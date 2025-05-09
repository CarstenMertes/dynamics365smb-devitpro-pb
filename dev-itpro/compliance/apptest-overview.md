---
title: Rules and guidelines for AL code
description: Describing the steps you must go through to successfully submit your Dynamics 365 Business Central app to AppSource.
author: SusanneWindfeldPedersen
ms.date: 04/11/2023
ms.reviewer: solsen
ms.topic: overview
ms.author: freddyk
---

# Rules and guidelines for AL code

This page defines the rules and guidelines to follow when writing AL code in an extension package for [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. The rules and guidelines are grouped according to two importance levels: critical errors that must be resolved, and important errors that should be resolved. Errors that aren't resolved must include an explanation and justification for the error.

## Critical errors

- Code uses encryption key functions such as ImportEncryptionKey, ExportEncryptionKey, CreateEncryptionKey, and DeleteEncryptionKey. (It's fine to use the Encrypt and Decrypt methods.)
- Code uses AssertError.
- External data connections don't properly handle sensitive data.
- It doesn't encrypt sensitive table data. (that is, credit card info, passwords, etc.).

## Important errors

- Temporary files aren't cleaned up after use.
- Code uses codeunits that require printers to be selected.
- Code uses a specific time zone or locale.

## Common pitfalls

To help you save time, we're sharing a list of the top 15 common pitfalls that regularly lead to app validation failures.  

1. Prefix/Suffix missing

    One of the app requirements is for you to reserve a prefix/suffix for your app. This is needed to ensure a healthy app ecosystem by avoiding collision amongst apps. This common failure occurs due to not setting your prefix/suffix in some or all required places. For more information, see [Benefits and Guidelines for using a Prefix or Suffix](apptest-prefix-suffix.md).  
2. DataClassification missing or set incorrectly

    Due to the requirements of privacy laws and regulations, fields of field class *Normal* must use the [DataClassification property](../developer/properties/devenv-dataclassification-property.md), and its value must be different from *ToBeClassified*. This applies to fields in tables and table extensions. Use the [AppSourceCop](../developer/devenv-using-code-analysis-tool.md) tool for detecting this.  
3. Required translation files missing

    There are many country/regions today that where [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] is available, and that you can support as well with your app. For specifying extra languages, we no longer support Caption ML. You must use xliff translation files instead. For more information, see [Working with Translation Files](../developer/devenv-work-with-translation-files.md).  
    Microsoft provides a free translation tool that you can access from [https://lcs.dynamics.com](https://lcs.dynamics.com).
    To support a specific country/region, you must include a translation file per for each language code. For example, to support Switzerland, you must provide fr-CH, de-CH, and it-CH.
4. Missing permission sets

    Your app must provide one or more permission sets so that users can use your app's functionality. Your app must never require the SUPER permission set. <!--TODO: Add link-->
5. Permission errors

    For your app to be a good citizen in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)], permission errors must not appear unless it's a necessary reason for showing the error.  
    It's acceptable to throw an error to a user that does not have your permission set marked and tries to access your page object.
    It isn't acceptable to throw an error to that same user trying to access [!INCLUDE[prod_short](../includes/prod_short.md)] pages in the base application, or to throw an error to a user who isn't trying to access your app's functionality.
6. Missing application area tagging

    Tag in which part your app participates. Pages, controls, actions, and fields won't appear in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] if the [Application Area property](../developer/properties/devenv-applicationarea-property.md) hasn't been set.
7. Usage Category not set

    You enable a page or report to be available through search in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] by using the [UsageCategory property](../developer/properties/devenv-usagecategory-property.md). For more information, see [Using Tell Me to Find Features and Information](/dynamics365/business-central/ui-search).
8. OnCompany procedure

    Due to their performance impact, *OnBeforeCompanyOpen* and *OnAfterCompanyOpen* can't be used. For more information, see [Replacing OnBeforeCompanyOpen and OnAfterCompanyOpen](apptest-onbeforecompanyopen.md).
9. Upgrade procedures

    Make sure that your app can be upgraded properly. For more information, see [Upgrading extensions](../developer/devenv-upgrading-extensions.md).
10. Profiles

    Don't insert into the Profile table. Use the [Profile object](../developer/devenv-profile-object.md) instead.
11. App file not properly code-signed

    Your app file must be digitally signed with a certificate from a third-party certification authority trusted by Windows.
12. You tested your app on an obsolete [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] version (or never even tested it)

    Make sure that your app is properly tested on the correct version. For more information, see [Current Build - Developing for Dynamics 365 Business Central](https://partner.microsoft.com/dashboard/collaborate/packages/4756) on the Collaborate site.
13. You tested using SUPER permissions

    You tested your app, but your user had SUPER permissions. This can hide critical errors. You must test with a user that doesn't have the SUPER permissions. The user must have the ESSENTIAL license. For more information, see [Testing your Extension](apptest-testingyourextension.md).  
14. User scenario document unclear

    Our validation team is testing your app functionality manually, so we need to be able to understand the core functionality of your app. If your user scenario document is missing important details that are needed for us to properly walk through your app's setup and usage scenarios, we can't validate your app successfully. For more information, see [User Scenario Documentation](apptest-userscenario.md).
15. The .json file is incorrect

    There are many values in the app.json file that may not be mandatory to compile your app, but are mandatory for your app to be in AppSource. For example, your app can't be published to a production tenant if the **target** value is set to *OnPrem*. It must be set to *Cloud*. For information, see [JSON Files](../developer/devenv-json-files.md).

## Related information

[Best practices for AL code](apptest-bestpracticesforalcode.md)  
[Checklist for submitting your app](../developer/devenv-checklist-submission.md)  
