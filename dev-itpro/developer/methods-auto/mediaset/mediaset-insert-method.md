---
title: "MediaSet.Insert(Guid) Method"
description: "Adds a media object that already exists in the database to a MediaSet of a record."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# MediaSet.Insert(Guid) Method
> **Version**: _Available or changed with runtime version 1.0._

Adds a media object that already exists in the database to a MediaSet of a record.


## Syntax
```AL
[Result := ]  MediaSet.Insert(MediaId: Guid)
```
## Parameters
*MediaSet*  
&emsp;Type: [MediaSet](mediaset-data-type.md)  
An instance of the [MediaSet](mediaset-data-type.md) data type.  

*MediaId*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
Specifies the unique ID that is assigned to the media object that you want to insert. Existing media objects are stored in the system table 2000000184 Tenant Media of the application database. There are different ways of obtaining the GUID of a media object. You could identify the media object ID by looking in the table. Or programmatically, you can use either the Item function on a MediaSet data type field of a record or the MEDIAID function on Media data type field of a record.  


## Return Value
*[Optional] Result*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the media is successfully added to the MediaSet, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
When media object is inserted in a MediaSet, it is assigned in index number. For more information, see [Indexing of media objects in a media set](../../devenv-working-with-media-on-records.md).

## Example  
This example uses the Insert method and [Item Method \(MediaSet\)](../../methods-auto/mediaset/mediaset-item-method.md) to take a media object that is already in the database and assigned to a record in a table (TableA), and add it to the MediaSet of a record in another table (TableB). This example assumes the following:

-   TableA and TableB already exist
-   Each table has a MediaSet data type field called **Images**
-   Each table contains the record number '1000'.
-   There is at least 1 media object in the MediaSet of record 1000 in TableA.

```al
 var
    recA: Record TableA;
    recB: Record TableB;
    mediasetId: GUID;
    Text000: Label 'Media %1 was added to MediaSet %2.';
    Text000: Label 'The media was not added to MediaSet %1.';
begin
    // Retrieves the GUID of the first media object (index number 1) in the MediaSet of record 1000 in TableA
    recA.Get('1000');  
    MediaId := recA.Images.Item(1);
    
    // Adds media object to the MediaSet of record 1000 in TableB based on the media object GUID
    recB.Get('1000');
    if recB.Images.Insert(mediaId) then begin
        recB.Modify;    
        Message(Text000, mediaId, recB.Images.MediaId);
    end else begin
       Message(Text001);
    end;
end;
``` 

## See Also
[MediaSet Data Type](mediaset-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)