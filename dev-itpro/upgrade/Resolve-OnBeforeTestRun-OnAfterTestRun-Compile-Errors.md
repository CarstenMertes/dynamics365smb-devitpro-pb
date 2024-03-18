---
title: "Fix OnBeforeTestRun and OnAfterTestRun after database conversion"
description: Explains how to resolve the problems with the OnBeforeTestRun and OnAfterTestRun triggers you convert a Dynamics NAV database.
ms.custom: na
ms.date: 12/22/2023
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---

# Resolving OnBeforeTestRun and OnAfterTestRun trigger errors when converting a database

Use the [!INCLUDE[nav_dev_long_md](../developer/includes/nav_dev_long_md.md)] to change the signature of the C/AL OnBeforeTestRun and OnAfterTestRun trigger functions of the test runner codeunits to include the *TestPermissions* parameter.

OnBeforeTestRun trigger before change:
```
OnBeforeTestRun(CodeunitID : Integer;CodeunitName : Text[30];FunctionName : Text[128];) Ok : Boolean)
```
OnBeforeTestRun trigger after change:
```
OnBeforeTestRun(CodeunitID : Integer;CodeunitName : Text[30];FunctionName : Text[128];FunctionTestPermissions : TestPermissions) Ok : Boolean)
```
OnAfterTestRun trigger before change:
```
OnAfterTestRun(CodeunitID : Integer;CodeunitName : Text[30];FunctionName : Text[128];Success : Boolean)
```
OnAfterTestRun trigger after change:
```
OnAfterTestRun(CodeunitID : Integer;CodeunitName : Text[30];FunctionName : Text[128];FunctionTestPermissions : TestPermissions;Success : Boolean)
```
If you don't change the signature, you get errors when you compile these objects.

## See also  
 [Converting a Database](Converting-a-Database.md)  
