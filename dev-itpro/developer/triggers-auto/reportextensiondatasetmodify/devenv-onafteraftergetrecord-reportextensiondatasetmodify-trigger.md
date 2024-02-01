---
title: "OnAfterAfterGetRecord (Report Extension Data Set Modify) Trigger"
description: "Runs after the OnAfterGetRecord trigger of the base data item."
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

# OnAfterAfterGetRecord (Report Extension Data Set Modify) Trigger
> **Version**: _Available or changed with runtime version 7.1._

Runs after the OnAfterGetRecord trigger of the base data item.


## Syntax
```AL
trigger OnAfterAfterGetRecord()
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
            trigger OnAfterAfterGetRecord()
            begin
                // Do some changes here
            end;
        }
    }
...
```

Use this trigger to perform any processing that is needed, based on the values in the fields of the individual records of a data item. The base object trigger is run before this trigger. For more information, see [OnAfterGetRecord (Report Data Item) Trigger](../reportdataitem/devenv-onaftergetrecord-reportdataitem-trigger.md). 

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  