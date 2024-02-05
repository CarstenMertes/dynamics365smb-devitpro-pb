---
title: "TestIsolation Property"
description: "Specifies which changes to the database to roll back after the tests in the test runner codeunit execute."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TestIsolation Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies which changes to the database to roll back after the tests in the test runner codeunit execute.

## Applies to
-   Codeunit

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Disabled**|runtime version 1.0|Do not roll back any changes to the database. Tests are not isolated from each other. This is the default value.|
|**Codeunit**|runtime version 1.0|Roll back all changes to the database after each test codeunit executes.|
|**Function**|runtime version 1.0|Roll back all changes to the database after each test method executes.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
TestIsolation = Codeunit;
```

## Remarks  

We recommend that you design tests to be independent of each other. Tests might read from and write to the same database, which means that tests can interact with each other. If tests interact, then you may experience incorrect test results. To eliminate test interactions, use the **TestIsolation** property to roll back changes to the database after each test method or after each test codeunit.  
  
> [!NOTE]  
> If you specify that you want to roll back database changes, then all database changes are rolled back, including changes that were explicitly committed to the database during the test by using the [Commit Method](../methods-auto/database/database-commit-method.md).  

## See Also

[TestPermissions Property](devenv-testpermissions-property.md)  
[Properties](devenv-properties.md)
<!-- 
[How to: Create a Test Runner Codeunit](How-to--Create-a-Test-Runner-Codeunit.md)   
[Testing the Application](Testing-the-Application.md)
-->