---
title: "OnBeforePostDataItem (Report Extension Data Set Modify) Trigger"
description: "Runs before the OnPostDataItem trigger of the base data item."
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

# OnBeforePostDataItem (Report Extension Data Set Modify) Trigger
> **Version**: _Available or changed with runtime version 7.1._

Runs before the OnPostDataItem trigger of the base data item.


## Syntax
```AL
trigger OnBeforePostDataItem()
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
            trigger OnBeforePostDataItem()
            begin
                // Do some changes here
            end;
        }
    }
...
```

This trigger runs before the base object trigger [OnPostDataItem (Report Data Item) Trigger](../reportdataitem/devenv-onpostdataitem-reportdataitem-trigger.md).

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  