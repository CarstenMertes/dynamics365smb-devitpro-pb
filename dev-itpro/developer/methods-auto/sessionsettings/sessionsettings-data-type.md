---
title: "SessionSettings Data Type"
description: "Is a complex data type for passing user personalization settings for a client session as an object."
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
# SessionSettings Data Type
> **Version**: _Available or changed with runtime version 1.0._

Is a complex data type for passing user personalization settings for a client session as an object. The object contains properties that correspond to the fields in the system table **2000000073 User Personalization**, including: App ID, Company, Language ID, Locale ID, Profile ID, Scope, and Time Zone. You can use the AL methods of the SessionSettings data type to get, set, and send the user personalization settings for the current client session.



## Instance methods
The following methods are available on instances of the SessionSettings data type.

|Method name|Description|
|-----------|-----------|
|[Company([Text])](sessionsettings-company-method.md)|Gets or sets the company property in a SessionSettings object.|
|[Init()](sessionsettings-init-method.md)|Populates the instance of a SessionsSettings with the current client user's personalization properties (such as Profile ID and Company) that are stored in the database.|
|[LanguageId([Integer])](sessionsettings-languageid-method.md)|Gets or sets the language ID property in a SessionSettings object.|
|[LocaleId([Integer])](sessionsettings-localeid-method.md)|Gets or sets the locale ID property in a SessionSettings object.|
|[ProfileAppId([Guid])](sessionsettings-profileappid-method.md)|Gets or sets the ID of an extension, which provides a profile, in a SessionSettings object.|
|[ProfileId([Text])](sessionsettings-profileid-method.md)|Gets or sets the profile ID property in a SessionSettings object.|
|[ProfileSystemScope([Boolean])](sessionsettings-profilesystemscope-method.md)|Gets or sets the profile scope property in a SessionSettings object.|
|[RequestSessionUpdate(Boolean)](sessionsettings-requestsessionupdate-method.md)|Passes a SessionSettings object to the client to request a new session that uses the user personalization properties that are set in the object. The current client session is abandoned and a new session is started.|
|[TimeZone([Text])](sessionsettings-timezone-method.md)|Gets or sets the time zone property in a SessionSettings object.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  