---
title: "OnPreXmlItem Trigger"
description: "OnPreXmlItem trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---


# OnPreXmlItem Trigger
Runs after the table is initialized and before you start exporting data to an XML object. This trigger only applies to XMLPort elements that have a source type of **Table**.  
  
## Applies to  
- XMLports  
  
## Remarks  
 This trigger is only used to export data. It is typically used to set filters on the data and to initialize variables before finding the first record.  
  
## See Also  
 [Triggers](devenv-triggers.md)  
 [XMLport trigger](devenv-xmlport-triggers.md)  