---
title: "OptionCaptionML Property"
description: "Sets the strings that are displayed to the user for selecting an option."
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
# OptionCaptionML Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the strings that are displayed to the user for selecting an option. OptionCaptionML is only used if the field or variable has an OptionMembers Property.

## Applies to
-   Table Field
-   Page Field
-   Report Column

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


> [!NOTE]  
> To submit an app to AppSource, you must use .xliff translation files. For more information, see [Working with Translation Files](../devenv-work-with-translation-files.md).
  
## Syntax
 
```AL
OptionCaptionML = <Language ID> = '<optioncaption [,optioncaption]*>'  
```  

## Remarks  

OptionCaptionML is multilanguage-enabled so it can contain a list of text in different languages. The text that is displayed is selected according to the current language settings of the user. For more information, see For more information, see [Working with Translation Files](../devenv-work-with-translation-files.md).  
  
`<Language ID>` is a Windows standard three-letter language ID and `<optioncaption [,optioncaption]*>` is the OptionCaption text(s) for this language. Commas are used to separate entries.  
  
Although you can use OptionCaptionML to limit the number of options displayed to the user, it is recommended that you use [OptionMembers Property](devenv-optionmembers-field-property.md) to do this. You cannot expand the set of options. If you do, a run-time error will occur when the user selects an option that is outside the option set defined for the field or variable.  
  
The following is an example of an OptionCaptionML value.  
  
```AL
OptionCaptionML = DAN = 'Resultatopgørelse,Balance', DEU = 'GuV,Bilanz', ESP = 'Comercial,Balance';  
```  
  
In this example, values are set up for Danish (DAN), German Standard (DEU), and Spanish Traditional Sort (ESP).  
  
## Examples of Using OptionCaptionML  

The following examples demonstrate the relationship between the [OptionMembers Property](devenv-optionmembers-field-property.md) and the OptionCaptionML property on fields (or variables) and controls.  
  
1. An Option field in a table has the following [OptionMembers Property](devenv-optionmembers-field-property.md) value: opt1,opt2,op3. The value of OptionCaptionML is not set. A page based on this table contains a text box that is based on the Option field. OptionString and OptionCaptionML are not set for the text box.  
  
     **Result** Users see opt1, opt2, and opt3 as the available choices.  
  
2. An OptionCaptionML property is added to the database field containing DAN = 'valg1,valg2,valg3', ENG = 'choice1,choice2,choice3'.  
  
     **Result** If a user selects DAN as the language, valg1, valg2, valg3 will be the available choices on the page. If a user selects ENG, choice1, choice2, choice3 will be available. For more information about what happens when the selected language is not available, see [Working with Translation Files](../devenv-work-with-translation-files.md).  
  
3. An OptionCaptionML property is added to the text box containing DAN = 'valg nummer 1,valg nummer 2,valg nummer 3'.  
  
     **Result** If a user sets DAN as the language, the choices are valg nummer 1, valg nummer 2, valg nummer 3. If a user sets the language to ENG, the same set of choices are available.  
  
4. The OptionCaptionML is removed from the field. The [OptionMembers Property](devenv-optionmembers-field-property.md) is set on the field; the OptionCaptionML property on the text box is set to DAN. The text strings specified in the OptionCaptionML property are used for all languages.  
  
     **Result** Same result as for example 3. As long as any OptionCaptionML property is set on the text box or the field, the [OptionMembers Property](devenv-optionmembers-field-property.md) is not used to display choices to the user.  
  
## See Also

[Working with Translation Files](../devenv-work-with-translation-files.md)
