---
title: API page type
description: Description of the API page type used for exposing web service endpoints.
author: SusanneWindfeldPedersen
ms.date: 03/14/2024
ms.topic: conceptual
ms.author: solsen
ms.reviewer: solsen
---

# API page type

Pages of the type `API` are used to create versioned, webhook-supported, OData v4 enabled REST web services. This type of page can't be displayed in the user interface, but is intended for building reliable integration services. When creating this page type, you must specify many properties that provide information for the web service endpoint. Use the snippet `tpage - Page of type API` to get the right template and the list of these properties automatically filled in. This page type can't be extended by creating a page extension object. Instead, you must create a new API by adding a page object. 

Pages of the type `API` can be used to develop a custom API. For more information, see [Developing a Custom API](devenv-develop-custom-api.md).

[!INCLUDE[extending_APIs_is_not_supported_note](includes/include-extending-APIs-is-not-supported-note.md)]


## Naming conventions

For the API page type, the following naming conventions exist:

- camelCase for naming attributes, tables, and APIPublisher, APIGroup, EntityName, and EntitySetName.
- Alphanumeric characters allowed (A-Z+a-z+0-9) in above elements. 
- APIVersion follows the pattern vX.Y or beta.

At design time, the compiler shows warnings on casing violations and errors on naming violations. Once an API page is deployed, the corresponding [$metadata](./devenv-connect-apps-tips.md) is exposed on the endpoint of the page. 

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

## Create, read, update, and delete operations
API pages support create, read, update, and delete operations. If you want to disallow, create, update, and delete operations, you can use the [InsertAllowed](properties/devenv-insertallowed-property.md), [ModifyAllowed](properties/devenv-modifyallowed-property.md), and [DeleteAllowed](properties/devenv-deleteallowed-property.md) properties respectively.

If you only want your API to expose committed data, you can add an OnOpenPageTrigger like this:

```AL
    trigger OnOpenPage()
    begin
        Rec.ReadIsolation := IsolationLevel::ReadCommitted;
    end;
```

## Example of the API page type

The following page example publishes an API available at:
`../contoso/app1/v2.0/companies({id})/customers`. The `APIVersion` can be specified as one version, or a list of versions, if the API is supported through multiple versions.

```AL
page 50120 MyCustomerApi
{
    PageType = API;
    Caption = 'My Customer API';
    APIPublisher = 'contoso';
    APIGroup = 'app1';
    APIVersion = 'v2.0', 'v1.0';
    EntityName = 'customer';
    EntitySetName = 'customers';
    SourceTable = Customer;
    DelayedInsert = true;
    
    layout
    {
        area(Content)
        {
            repeater(GroupName)
            {
                field(id; Id)
                {
                    Caption = 'ID';
                }
                field(name; Name)
                {
                    Caption = 'Name';
                }
            }
        }
    }
}
```

## Related information

[API developer overview](devenv-api.md)
[AL development environment](devenv-reference-overview.md)  
[API query type](devenv-api-querytype.md)  
[Walkthrough: developing a custom API](devenv-develop-custom-api.md)   
[Page extension object](devenv-page-ext-object.md)  
[APIPublisher property](properties/devenv-apipublisher-page-property.md)  
[APIGroup property](properties/devenv-apigroup-page-property.md)  
[APIVersion property](properties/devenv-apiversion-page-property.md)   
[EntityName property](properties/devenv-entityname-property.md)  
[EntitySetName property](properties/devenv-entitysetname-property.md)  
[Developing extensions](devenv-dev-overview.md)
