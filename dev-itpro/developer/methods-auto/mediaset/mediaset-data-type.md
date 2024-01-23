---
title: "MediaSet Data Type"
description: "Encapsulates media, such as images, in application database tables."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# MediaSet Data Type
> **Version**: _Available or changed with runtime version 1.0._

Encapsulates media, such as images, in application database tables.


## Static methods
The following methods are available on the MediaSet data type.


|Method name|Description|
|-----------|-----------|
|[FindOrphans()](mediaset-findorphans-method.md)|Discovers all orphaned media sets. Orphaned media sets are media sets that are not referenced by any other table.|

## Instance methods
The following methods are available on instances of the MediaSet data type.

|Method name|Description|
|-----------|-----------|
|[Count()](mediaset-count-method.md)|Gets the number of media objects that are included in the MediaSet of a record.|
|[ExportFile(Text)](mediaset-exportfile-method.md)|Exports the media objects in the current media set of a record to individual files on your computer or network. In the record, the media set is referenced in a MediaSet data type field.|
|[ImportFile(Text, Text [, Text])](mediaset-importfile-method.md)|Adds a media, such as a JPEG image, to the MediaSet data type field of a record for displaying the media in the client. The media is imported to the database and included in a MediaSet for the record.|
|[ImportStream(InStream, Text [, Text])](mediaset-importstream-method.md)|Adds a media file, such as a JPEG image, from an InStream object to the MediaSet of record for displaying in the client. The media is imported to the database and included in a MediaSet for the record.|
|[Insert(Guid)](mediaset-insert-method.md)|Adds a media object that already exists in the database to a MediaSet of a record.|
|[Item(Integer)](mediaset-item-method.md)|Gets the unique identifier (GUID) of a media object that is assigned to a MediaSet on a record.|
|[MediaId()](mediaset-mediaid-method.md)|Gets the unique identifier that is assigned to a MediaSet of a record. The MediaSet is a collection of media objects that are used on the record that can be displayed in the client.|
|[Remove(Guid)](mediaset-remove-method.md)|Removes a media object from a MediaSet of a record.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Working With Media on Records](../../devenv-working-with-media-on-records.md)