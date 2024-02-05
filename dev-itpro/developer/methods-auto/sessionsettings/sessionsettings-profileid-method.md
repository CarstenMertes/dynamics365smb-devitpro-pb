---
title: "SessionSettings.ProfileId([Text]) Method"
description: "Gets or sets the profile ID property in a SessionSettings object."
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
# SessionSettings.ProfileId([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the profile ID property in a SessionSettings object.


## Syntax
```AL
[ProfileId := ]  SessionSettings.ProfileId([NewProfileId: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*SessionSettings*  
&emsp;Type: [SessionSettings](sessionsettings-data-type.md)  
An instance of the [SessionSettings](sessionsettings-data-type.md) data type.  

*[Optional] NewProfileId*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the ID of the profile to set in the SessionSettings object. The value must be a valid profile ID in the system table **2000000072 Profile**.  


## Return Value
*[Optional] ProfileId*  
&emsp;Type: [Text](../text/text-data-type.md)  
The profile ID that is set in the SessionSettings object.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
The profile ID determines the Role Center that is used in the client session. The ProfileId property in a SessionSettings object corresponds to the **Profile ID** field in the in the system table **2000000073 User Personalization**.

## Example
This example creates a SessionSettings object that is populated with the current client user's personalization data, and uses the changes the Profile method to set the profile to 'Business Manager'. Finally, the RequestSessionUpdate method sends a request to the client to abandon the current session and start a new session that uses the new profile ID. This example requires a SessionSettings data type variable.

```al
var
  MySessionSettings : SessionSettings;
begin
  MySessionSettings.Init;
  MySessionSettings.ProfileId('Business Manager');
  MySessionSettings.RequestSessionUpdate(false);
end;  
```  


## See Also
[SessionSettings Data Type](sessionsettings-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)