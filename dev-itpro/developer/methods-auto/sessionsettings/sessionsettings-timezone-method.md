---
title: "SessionSettings.TimeZone([Text]) Method"
description: "Gets or sets the time zone property in a SessionSettings object."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# SessionSettings.TimeZone([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the time zone property in a SessionSettings object.


## Syntax
```AL
[TimeZone := ]  SessionSettings.TimeZone([NewTimeZone: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*SessionSettings*  
&emsp;Type: [SessionSettings](sessionsettings-data-type.md)  
An instance of the [SessionSettings](sessionsettings-data-type.md) data type.  

*[Optional] NewTimeZone*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the time zone property in the SessionsSettings object. The value must be a valid Windows time zone name, such as **UTC** or **Pacific Standard Time**.  


## Return Value
*[Optional] TimeZone*  
&emsp;Type: [Text](../text/text-data-type.md)  
The time zone set in the SessionSettings object.
      


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The default time zone is **UTC**. This method can also be used with web service sessions.

## Example

This example creates a SessionSettings object that is populated with the current client user's personalization data, and then uses the TimeZone method to set the time zone to 'UTC' (Coordinated Universal Time). Finally, the RequestSessionUpdate method sends a request to the client to abandon the current session and start a new session that uses the new profile ID. This example requires a SessionSettings data type variable.

```al
var
  MySessionSettings : SessionSettings;
begin
  MySessionSettings.Init;
  MySessionSettings.TimeZone('UTC');
  MySessionSettings.RequestSessionUpdate(false);
end;  
```  


## See Also

[SessionSettings Data Type](sessionsettings-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Managing Time Zones with Web Services](../../../webservices/Managing-Time-Zones-with-Web-Services.md)