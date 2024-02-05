---
title: "Access Property"
description: "Sets the object accessibility level, which controls whether the object can be used from other code in your module or other modules."
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
# Access Property
> **Version**: _Available or changed with runtime version 4.0._

Sets the object accessibility level, which controls whether the object can be used from other code in your module or other modules.

## Applies to
-   Codeunit
-   Query
-   Table
-   Table Field
-   Enum Type
-   Interface
-   Permission Set

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Public**|runtime version 1.0|The object can be accessed by any other code in the same module and in other modules that references it.|
|**Internal**|runtime version 1.0|The object can be accessed only by code in the same module, but not from another module.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


### Table field level

For table fields there are two additional settings for **Access** and you have the following settings available:

|Access modifier    |Level of accessibility |
|-------------------|-----------------------|
|Local              |The field can be accessed only by code in the same table or table extension where the field is defined.|
|Protected          |The field can be accessed only by code in the same table or table extensions of that table.|
|Public|The object can be accessed by any other code in the same module and in other modules that references it. It is the default value.|
|Internal|The object can be accessed only by code in the same module, but not from another module.|

## Syntax

### Tables
```AL
table 50111 MyTable
{
    DataClassification = CustomerContent;
    Access = Internal;
    ...
    
```
### Table fields

```AL
table 50111 MyTable
{
    DataClassification = CustomerContent;
        
    fields
    {
        field(1;MyField; Integer)
        {
            DataClassification = CustomerContent;
            Access = Protected;
    ...            

```
### Queries

```AL
query 50114 MyQuery
{
    QueryType = Normal;
    Access = Internal;
    ...
```

### Codeunits

```AL
codeunit 50113 MyCodeunit
{
    Access = Internal;
    ...

```
## Remarks 

> [!IMPORTANT]  
> This property is only taken into consideration at compile time. For example, at compile time, a table with `Access = Internal` cannot be used from other modules that do not have access to the internals of the module where the table is defined, but at runtime, any module can access the table by using reflection-based mechanisms such as `RecordRef`, or `TransferFields`. And the `OnRun` trigger can be run on `internal` codeunits by using `Codeunit.Run`. Setting the object accessibility level as `Access = Internal;` *cannot* be used as a security boundary. Also see [JSON Files](../devenv-json-files.md#appjson-file).

> [!NOTE]
> The accessibility of tables and table fields is taken into account when using [Designer](../devenv-inclient-designer.md). As a consequence, only table fields which have their accessibility set to `Public` can be added to the page. 

## See Also  
[Properties](devenv-properties.md)   
[Extensible Property](devenv-extensible-property.md)   
[Protected Variables](../devenv-protected-variables.md)
