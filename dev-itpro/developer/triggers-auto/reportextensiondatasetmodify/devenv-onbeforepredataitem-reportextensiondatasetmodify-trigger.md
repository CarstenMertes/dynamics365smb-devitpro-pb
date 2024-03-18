---
title: "OnBeforePreDataItem (Report Extension Data Set Modify) Trigger"
description: "Runs before the OnPreDataItem trigger of the base data item."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnBeforePreDataItem (Report Extension Data Set Modify) Trigger
> **Version**: _Available or changed with runtime version 7.1._

Runs before the OnPreDataItem trigger of the base data item.


## Syntax
```AL
trigger OnBeforePreDataItem()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This trigger can be called inside a `modify` section, as shown in this pseudo-code:

```al
reportextension 50111 MyExtension extends "Customer - List"
{
    dataset
    {
        modify(Customer)
        {
            trigger OnBeforePreDataItem()
            begin
                // Do some changes here
            end;
        }
    }
...
```

This trigger runs before the base object trigger [OnPreDataItem (Report Data Item) Trigger](../reportdataitem/devenv-onpredataitem-reportdataitem-trigger.md).


## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  