---
title: "TestPermissions Property"
ms.date: 10/01/2020
ms.reviewer: na
ms.suite: na
ms.topic: article
ms.author: solsen
author: SusanneWindfeldPedersen
---

# TestPermissions Property

Specifies a value that can be used to determine which permission sets are used on tests that are run by test codeunits. Test codeunits are codeunits that have the **SubType** property set to **Test**.

## Applies to

- Test codeunits
    
## Property values

The property has the following values: 

* **Disabled**
* **Restrictive**
* **NonRestrictive**
* **InheritFromTestCodeunit**

    **InheritFromTestCodeunit** is only relevant for test methods; not test codeunits. It specifies that a test method uses the TestPermissions property setting of the test codeunit to which it belongs. If you use this value on a test codeunit, the property will resolve to **Restrictive** at runtime.

Apart from **InheritFromTestCodeunit**, the values themselves do not perform any operations or have any specific behavior. Instead, you programmatically define what each value does, and the permissions sets it applies at runtime, by adding code in a test runner codeunit.

## Syntax

```AL
TestPermissions = Disabled;
```

## Remarks

The **TestPermissions** property works together with the **OnBeforeTestRun** and **OnAfterTestRun** triggers in test runner codeunits. The value of the **TestPermissions** property is passed as a parameter to the test runner codeunit triggers. The permission sets that are used during a test are determined by the code that you add to the triggers. Typically, you use the **OnBeforeTestRun** trigger to apply permissions sets and the **OnAfterTestRun** trigger to clear permissions sets.

> [!NOTE]  
> To specify the permission sets that are used by the tests run by a specific test method, use the [TestPermissions Attribute](../methods/devenv-testpermissions-attribute.md).

## See Also

[Properties](devenv-properties.md)  
[TestPermissions Attribute](../methods/devenv-testpermissions-attribute.md)
<!--
## See Also
[Testing With Permission Sets](../devenv-testing-permissionsets.md)  
[Testing the Application](../devenv-Testing-the-Application.md)  
[How to: Create a Test Runner Codeunit](../devenv-How-to-Create-a-Test-Runner-Codeunit.md)  
[How to: Create Test Codeunits and Test Methods](../methods/devenv-How-to-Create-Test-Codeunits-and-Test-Methods.md)  
[How to: Create Handler Methods](../methods/devenv-How-to-Create-Handler-Methods.md)  
[Walkthrough: Testing Purchase Invoice Discounts](../Walkthrough--Testing-Purchase-Invoice-Discounts.md)  
[OnAfterTestRun Trigger](../triggers/devenv-trigger-onaftertestrun.md)  
[OnBeforeTestRun Trigger](../triggers/devenv-trigger-onbeforetestrun.md)  -->