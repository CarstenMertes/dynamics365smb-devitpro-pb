---
title: "DecimalPlaces Property"
description: "Sets display and storage requirements for the Decimal Data Type."
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
# DecimalPlaces Property
> **Version**: _Available or changed with runtime version 1.0._

Sets display and storage requirements for the Decimal Data Type.

## Applies to
-   Table Field
-   Page Field
-   Report Column

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value  

You can enter minimum, maximum, or both values for the number of decimal places, as shown in the following examples.  
  
|Value|Description|  
|-----------|---------------------------------------|  
|**1**|A minimum of 1 and a maximum of 1 decimal place.|  
|**1:4**|A minimum of 1 and a maximum of 4 decimal places.|  
|**2:**|At least 2 decimal places.|  
|**:2**|No more than 2 decimal places.|  


> [!NOTE]
> The maximum number of decimal places that can be specified is 18. If you set a maximum number of decimal places greater than 18, the digits following the 18th decimal place will be ignored.

## Syntax

```AL
DecimalPlaces = 0 : 5;
```
  
## Remarks

For decimal fields, this property specifies the number of decimal places that you want to store. The default storage requirements for [Decimal Data Type](../methods-auto/library.md) are two decimal places for amounts. Use this property to specify storage requirements that are different than the default. 
  
This setting is evaluated on text boxes and fields during validation.  
  
When you create a new field of [Decimal Data Type](../methods-auto/library.md), the value is automatically formatted as a currency. If your decimal field does not contain a currency value, then you can use this property to determine the number of decimal places that appear on the screen. For example, in the G/L Entry table, the DecimalPlaces property of field 42, Quantity, is set to 0:5. The minimum number of decimal places that you can enter is 0 and the maximum is 5. 

For more information about formatting decimal values, see [Formatting Decimal Values in Fields](../devenv-format-field-data.md).
  
## See Also

[Decimal Data Type](../methods-auto/library.md)