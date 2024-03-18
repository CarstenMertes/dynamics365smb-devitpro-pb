---
title: "EnableExternalImages Property"
description: "Sets whether external images are allowed on a report."
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
# EnableExternalImages Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether external images are allowed on a report.

## Applies to
-   Report

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Value  

**True** if external images are allowed; otherwise, **false**. The default is **false**.  

## Syntax

```AL
EnableExternalImages = true;
```
 
## Remarks  

> [NOTE]
> It applies to client report definition \(RDLC\) report layouts.  

When you use the Visual Studio Report Designer for creating reports for the RoleTailored client, you can add images such as your company logo to a report. You can add either *embedded* or *external* images.  
  
- With an embedded image, the source file is compiled as part of the report. If a report only uses embedded images, then you can set the **EnableExternalImages** property to **false**. For an example of using embedded images, see [How to add a Company Picture to a Report](/archive/blogs/nav-reporting/).  
  
- With an external image, the source file is stored outside of the report in a location that must be accessible from the RoleTailored client, such as on a file server or local computer. The image is referenced from the report and loads when the report opens. To use external images on a report, the **EnableExternalImages** property must be set to **true**.  
  > [!NOTE]  
  >  The **EnableExternalImages** property exposes the [LocalReport.EnableExternalImages property](/dotnet/api/microsoft.reporting.webforms.localreport.enableexternalimages) of the [Microsoft.ReportViewer.WebForms.LocalReport object](/dotnet/api/microsoft.reporting.webforms.localreport), which is embedded in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)]. The Microsoft.ReportViewer.WebForms.LocalReport object is part of the [ReportViewer controls](/previous-versions/ms251671(v=vs.140)) that are available in Visual Studio for adding reports to your application.  
  

For information about how to add images using Visual Studio Report Designer, see [Adding Images to a Report (Visual Studio Report Designer)](/previous-versions/ms251715(v=vs.100)).  
  
## Security Considerations  

[!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] cannot verify image sources and protect against malicious images or sources that may be harmful to your computer. You should set the **EnableExternalImages** property to **true** only if you can ensure that images on the report come from a trusted source.  
  
## See Also  

[Properties](devenv-properties.md)