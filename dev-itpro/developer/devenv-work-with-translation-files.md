---
title: Working with translation files
description: How to work with translations, multilanguage, and XLIFF files in Business Central.
ms.date: 04/14/2025
ms.topic: conceptual
ms.author: solsen
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---

# Working with translation files

[!INCLUDE [prod_short](includes/prod_short.md)] is multi-language enabled, which means that you can display the user interface (UI) in different languages. In [!INCLUDE [prod_short](includes/prod_short.md)], this is done using XLIFF files, which is a standardized format used for computer-based translations.  

[!INCLUDE [translation-services-deprecation](../includes/translation-services-deprecation.md)]

> [!TIP]
> Optionally, use the [Dynamics 365 Translation Service](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/translation-service-overview) to get translations for your target languages. For more information, see [Translate user interface files](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/use-translation-service).

For an overview of how translations are applied, see [Translations overview](devenv-translations-overview.md).

## Generating the XLIFF file

To add a new language to the extension that, you've built, first, you must enable the generation of XLIFF files. The XLIFF file extension is .xlf. The generated XLIFF file contains the strings that are specified in properties such as **Caption**, **CaptionML**, and **Tooltip**.

> [!NOTE]  
> To submit an app to AppSource, you must use XLIFF translation files.

In the app.json file of your extension, add the following line:

```json
  "features": [ "TranslationFile" ]
```

> [!NOTE]  
> If the **Incremental Build** setting is enabled in the **AL Language extension configuration** then all translations will be ignored, even though the `"features": [ "TranslationFile" ]` setting is specified in the `app.json` file. For more information, see [AL Language Extension Configuration](devenv-al-extension-configuration.md).
> The same is true when using **RAD** publishing, all translations will also be ignored. For more information, see [Work with Rapid Application Development](devenv-rad-publishing.md).

Now, when you run the build command (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>) in Visual Studio Code, a `\Translations` folder is generated and populated with the .xlf file that contains all the labels, label properties, and report labels that you're using in the extension. The generated .xlf file can now be translated.

> [!IMPORTANT]  
> The **ML** versions of properties are **not** included in the .xlf file:  
>
> - [AboutTitleML](properties/devenv-abouttitleml-property.md)  
> - [AboutTextML](properties/devenv-abouttextml-property.md)  
> - [CaptionML](properties/devenv-captionml-property.md)
> - [InstructionalTextML](properties/devenv-instructionaltextml-property.md)
> - [OptionCaptionML](properties/devenv-optioncaptionml-property.md)
> - [PromotedActionCategoriesML](properties/devenv-promotedactioncategoriesml-property.md)
> - [RequestFilterHeadingML](properties/devenv-requestfilterheadingml-property.md)
> - [ToolTipML](properties/devenv-tooltipml-property.md)
> 
> The [TextConst data type](methods-auto/textconst/textconst-data-type.md) is not included in the .xlf file either.

> [!IMPORTANT]  
> Make sure to rename the translation file before building the extension next time, as it'll be overwritten.

By setting the `GenerateCaptions` flag in the app.json file, you specify that you want to generate captions based on the object name for pages, tables, reports, XMLports, and request pages. If the object already has a `Caption` property set, that value is used. For the table fields, the `OptionCaption` is used. The syntax is as follows:

```json
  "features": [ "TranslationFile", "GenerateCaptions" ]
```

### GenerateLockedTranslations

[!INCLUDE[2020_releasewave2](../includes/2020_releasewave2.md)]

By setting the `GenerateLockedTranslations` flag in the app.json file, you specify that you want to generate `<trans-unit>` elements for locked labels in the XLIFF file. The default behavior is that these elements aren't generated. For more information, see [JSON Files](devenv-json-files.md).

```json
  "features": [ "GenerateLockedTranslations" ]
```

## Label syntax

The label syntax is shown in the example below for the **Caption** property: 

```AL
Caption = 'Developer translation for %1',  Comment = '%1 is extension name', locked = false, MaxLength=999; 
```

> [!NOTE]  
> The `comment`, `locked`, and `maxLength` attributes are optional and the order isn't enforced. For more information, see [Label Data Type](methods-auto/label/label-data-type.md).

Use the same syntax for report labels:  

```AL
labels
{
  LabelName = 'Label Text', Comment='Foo', MaxLength=999, Locked=true;
} 
```

And the following is the syntax for **Label** data types:

```AL
var
    a : Label 'Label Text', Comment='Foo', MaxLength=999, Locked=true;
```

## The XLIFF file

In the generated .xlf file, you can see a `<source>` element for each label. For the translation, you'll now have to add the `target-language` and a `<target>` element per label. The `target-language` must be specified in the format `"<language code>-<country code>"`, for example `"da-DK"`, `"es-ES"`, or `"de-DE"`. The `<trans-unit id>` attribute corresponds to the object ID in the extension. This is illustrated in the example below.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="urn:oasis:names:tc:xliff:document:1.2 xliff-core-1.2-transitional.xsd">
  <file datatype="xml" source-language="en-US" target-language="da-DK" original="ALProject16">
    <body>
      <group id="body">
        <trans-unit id="PageExtension 50110" maxWidth="999" size-unit="char" translate="yes" xml:space="preserve">
          <source>Developer translation for %1</source>
          <target>Udvikleroversættelse for %1</target>
          <note from="Developer" annotates="general" priority="2">%1 is extension name</note>
          <note from="Xliff Generator" annotates="general" priority="3">PageExtension - PageExtension</note>
        </trans-unit>
      </group>
    </body>
  </file>
</xliff>
```

> [!NOTE]  
> You can have only one .xlf file per language. If you translate your extension to multiple languages, you must have a translation file per language. There is no enforced naming on the file, but it's a good practice to name it `<extensionname>.<language>.xlf`.

When the extension is built and published, you can change the language of [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] to view the UI in the translated language.

## Translating other extensions

To translate other extensions, for example, when adding translations to the Base Application, you must reference the project to be translated using the `dependencies` section in the `app.json` file. For more information, see [JSON Files](devenv-json-files.md). When the dependencies are set, you can add xliff files in your current project that translates the object captions of the referenced extension. Create a directory named **Translations**, in the root of the extension, and place the translated xliff file there. When your extension is then built and published, change the language of [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] to view the UI in the translated language. 

> [!NOTE]  
> When translating other extensions, make sure that the attribute `original` in the `<file>` element in the xliff file is **not** set to the name of the current app. Otherwise, translations are only used to translate labels in the same app.
>
> For apps where translations are meant to translate the current app, the generated xliff file will have the correct value of the app name.


### Use the `<trans-unit id>` of the label where it was defined

In order to translate other apps, you must use the `<trans-unit id>` of the original property, not the one of an extension object as that might have been modified.

If `MyPage` is defined as:

```al
page 50000 MyPage {
  Caption = 'Base Page'
}
```

and it has `<trans-unit id>` for the page corresponding to `Page 2931038265 - Property 2879900210`.

And if the following page extension of `MyPage` called `MyPageExtension`:

```al
pageextension 50000 MyPageExtension extends MyPage
{
    Caption = 'Extension Page';
}
```

has `<trans-unit id>` for the page extension corresponding to `PageExtension 1716690578 - Property 2879900210`, then if you want to change the caption on the page, you must use the ID `Page 2931038265 - Property 2879900210`, which is the `<trans-unit id>` of the original property.


<!-- removing bug 394765
## Translation and Localization apps

> [!NOTE]  
> The following section only applies to versions released before Business Central 2019 release wave 2.

The .xlf files approach cannot be used for translating the base application. If you are working on a translation or localization app (for example for a [country/region localization](readiness/readiness-develop-localization.md)), you must take the .txt file containing the base application translation, and place the file in the root folder of your extension. When the extension is compiled, the .txt file is then packaged with the extension. 

We recommend that you use only one .txt file per language. There is no enforced naming on the .txt files, but a suggested good practice is to name it `<extensionname>.<language>.txt`.  

For more information about importing and exporting .txt files, see [How to: Add Translated Strings By Importing and Exporting Multilanguage Files in Dynamics NAV](/dynamics-nav/how-to--add-translated-strings-by-importing-and-exporting-multilanguage-files).
-->

## Related information

[Working with labels](devenv-using-labels.md)  
[Working with multiple AL project folders within one workspace](devenv-multiroot-workspaces.md)  
[JSON Files](devenv-json-files.md)  
[Translate user interface files using the Dynamics 365 Translation Service](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/use-translation-service)  
