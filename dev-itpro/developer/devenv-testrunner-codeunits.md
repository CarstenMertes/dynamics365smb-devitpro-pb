---
title: Test Runner Codeunits
description: This article describes how to create test codeunits and how to create test runner codeunits. 
ms.custom: na
ms.date: 08/12/2022
ms.reviewer: solsen
ms.topic: conceptual
author: blrobl
---

# Create Test Runner Codeunits

You can create test runner codeunits to manage the execution of test codeunits and to integrate with test management or test reporting frameworks. By integrating with a test management framework, you can automate your tests and enable them to run unattended.  

To create a test runner codeunit, create a codeunit and set the [SubType Property](properties/devenv-subtype-codeunit-property.md) to **TestRunner**.

To specify what changes in the database you want to roll back after the tests in the test runner codeunit execute, set the [TestIsolation Property](properties/devenv-testisolation-property.md).

<!--
> [!TIP]
> In the test runners in the automated application test libraries on the Dynamics NAV product media, test isolation is set to Codeunit.
-->

Test runner codeunits include the following triggers:  

- [OnRun Trigger](triggers-auto/codeunit/devenv-onrun-codeunit-trigger.md) 

- [OnBeforeTestRun Trigger](triggers-auto/codeunit/devenv-onbeforetestrun-codeunit-trigger.md)  

- [OnAfterTestRun Trigger](triggers-auto/codeunit/devenv-onaftertestrun-codeunit-trigger.md)  

In the **OnRun** trigger, you'll enter the code to run the codeunits. It runs when you execute the codeunit and before the test methods run. You can use the **OnBeforeTestRun** and the **OnAfterTestRun** triggers to perform preprocessing and postprocessing, such as initialization or logging test results. If you implement the **OnBeforeTestRun** trigger, then it executes before each test method executes. If you implement the **OnAfterTestRun** trigger, then it executes after each test method executes and also suppresses the automatic display of the results message.  

> [!WARNING]  
> The **OnBeforeTestRun** and **OnAfterTestRun** triggers always run in their own transactions, regardless of the value of the [TestIsolation Property](properties/devenv-TestIsolation-Property.md), the value of the [TransactionModel Property](./properties/devenv-properties.md), or the outcome of a test method. 

## Example

This sample codeunit runs three test codeunits in the automated application test libraries.

```AL
codeunit 50101 TestRunnerCodeunit
{
    Subtype = TestRunner;

    trigger OnRun()
    begin
        Codeunit.RUN(Codeunit::"ERM Vendor Statistics");
        Codeunit.RUN(Codeunit::"ERM Sales Quotes");
        Codeunit.RUN(Codeunit::"ERM Dimension");

    end;
}
```

You may want to define your test suite in a table and then write code in the test runner codeunit to iterate through the items in the table. And then run each test codeunit. In that case, you can make use of the following example.

```AL
codeunit 50102 TestRunnerCodeunit
{
    Subtype = TestRunner;

    trigger OnRun()
    var
        EnabledTestCodeunit: Record "CAL Test Enabled Codeunit";
        Object: Record "Object";
    begin
        if EnabledTestCodeunit.FINDSET then
            repeat
                if Object.GET(ObjectType::Codeunit, '', EnabledTestCodeunit."Test Codeunit ID") then
                    CODEUNIT.RUN(EnabledTestCodeunit."Test Codeunit ID");
            until EnabledTestCodeunit.NEXT = 0

    end;
}
```

## See Also
[Testing the Application](devenv-Testing-Application.md)