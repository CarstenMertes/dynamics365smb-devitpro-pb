---
title: "ServiceEnabled Attribute"
description: "Exposes a method to the service."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# ServiceEnabled Attribute
> **Version**: _Available or changed with runtime version 2.0._

Exposes a method to the service.


## Applies To

- Method


## Syntax

```AL
[ServiceEnabled]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```AL
    [ServiceEnabled]
    procedure Post(var ActionContext: WebServiceActionContext)
    var
        SalesHeader: Record "Sales Header";
        SalesInvoiceHeader: Record "Sales Invoice Header";
    begin
        GetDraftInvoice(SalesHeader);
        PostInvoice(SalesHeader, SalesInvoiceHeader);
        SetActionResponse(ActionContext, SalesInvoiceHeader.Id);
    end;
```

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  