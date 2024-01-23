---
title: "AppSourceCop Analyzer"
description: "AppSourceCop is an analyzer that enforces rules that must be respected by extensions meant to be published to Microsoft AppSource."
ms.author: solsen
ms.custom: na
ms.date: 12/22/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Analyzer Rules
AppSourceCop is an analyzer that enforces rules that must be respected by extensions meant to be published to Microsoft AppSource.

## Rules

|Id|Title|Category|Default Severity|
|--|-----------|--------|----------------|
|[AS0001](appsourcecop-as0001.md)|Tables and table extensions that have been published must not be deleted.|Upgrade|Error|
|[AS0002](appsourcecop-as0002.md)|Fields must not be deleted.|Upgrade|Error|
|[AS0003](appsourcecop-as0003.md)|The previous version of the extension could not be found.|Upgrade|Error|
|[AS0004](appsourcecop-as0004.md)|Fields must not change type, since dependent extensions may break|Upgrade|Error|
|[AS0005](appsourcecop-as0005.md)|Fields must not change name|Upgrade|Error|
|[AS0006](appsourcecop-as0006.md)|Tables that have been published must not change name.|Upgrade|Error|
|[AS0007](appsourcecop-as0007.md)|Objects that have been published must not change namespace.|Upgrade|Error|
|[AS0008](appsourcecop-as0008.md)|Defining reserved namespaces is not allowed.|Configuration|Error|
|[AS0009](appsourcecop-as0009.md)|Key fields must not be changed|Upgrade|Error|
|[AS0010](appsourcecop-as0010.md)|Keys must not be deleted|Upgrade|Error|
|[AS0011](appsourcecop-as0011.md)|An affix is required|Extensibility|Error|
|[AS0013](appsourcecop-as0013.md)|The field identifier must be within the allowed range|Extensibility|Error|
|[AS0014](appsourcecop-as0014.md)|The project manifest must contain the allocated identifier range|Extensibility|Error|
|[AS0015](appsourcecop-as0015.md)|TranslationFile must be enabled.|Extensibility|Error|
|[AS0016](appsourcecop-as0016.md)|Fields of field class 'Normal' must use the DataClassification property and its value should be different from ToBeClassified|Extensibility|Error|
|[AS0018](appsourcecop-as0018.md)|A procedure belonging to the public API cannot be removed|Upgrade|Error|
|[AS0019](appsourcecop-as0019.md)|Event attributes cannot be removed|Upgrade|Error|
|[AS0020](appsourcecop-as0020.md)|The type of events cannot be changed.|Upgrade|Error|
|[AS0021](appsourcecop-as0021.md)|An argument in an event attribute cannot be changed to false.|Upgrade|Error|
|[AS0022](appsourcecop-as0022.md)|An external scope cannot be removed|Upgrade|Error|
|[AS0023](appsourcecop-as0023.md)|A return type cannot be modified in external procedures|Upgrade|Error|
|[AS0024](appsourcecop-as0024.md)|Parameters cannot be removed or added in external procedures|Upgrade|Error|
|[AS0025](appsourcecop-as0025.md)|Parameters cannot be modified, renamed, or removed from events.|Upgrade|Error|
|[AS0026](appsourcecop-as0026.md)|The type and subtype of parameters cannot be modified in events and external procedures|Upgrade|Error|
|[AS0027](appsourcecop-as0027.md)|Modifying the array size of a parameter in events and external procedures is not allowed|Upgrade|Error|
|[AS0028](appsourcecop-as0028.md)|Reducing the array size of a parameter in events and external procedures is not allowed|Upgrade|Error|
|[AS0029](appsourcecop-as0029.md)|Pages and PageExtensions that have been published must not be deleted, since dependent extensions may break|Upgrade|Error|
|[AS0030](appsourcecop-as0030.md)|Pages that have been published must not be renamed.|Upgrade|Error|
|[AS0031](appsourcecop-as0031.md)|Actions that have been published must not be deleted.|Upgrade|Error|
|[AS0032](appsourcecop-as0032.md)|Controls that have been published must not be deleted.|Upgrade|Error|
|[AS0033](appsourcecop-as0033.md)|Views that have been published must not be deleted.|Upgrade|Error|
|[AS0034](appsourcecop-as0034.md)|Unsupported table property change|Upgrade|Error|
|[AS0035](appsourcecop-as0035.md)|Unsupported page property change|Upgrade|Warning|
|[AS0036](appsourcecop-as0036.md)|Unsupported table field property change|Upgrade|Error|
|[AS0038](appsourcecop-as0038.md)|Unsupported table key property change|Upgrade|Error|
|[AS0039](appsourcecop-as0039.md)|Removing properties that cause destructive changes is not allowed|Upgrade|Error|
|[AS0040](appsourcecop-as0040.md)|Removing properties that cause destructive changes is not allowed|Upgrade|Warning|
|[AS0041](appsourcecop-as0041.md)|Table field property changes that cause destructive changes must not be removed|Upgrade|Error|
|[AS0042](appsourcecop-as0042.md)|Table key property changes that cause destructive changes must not be removed|Upgrade|Error|
|[AS0043](appsourcecop-as0043.md)|The clustered key must not be deleted|Upgrade|Error|
|[AS0044](appsourcecop-as0044.md)|Property changes that cause destructive changes are not allowed|Upgrade|Error|
|[AS0047](appsourcecop-as0047.md)|The extension name is too long.|Extensibility|Error|
|[AS0048](appsourcecop-as0048.md)|The publisher name is too long.|Extensibility|Error|
|[AS0049](appsourcecop-as0049.md)|The access modifier of an application object cannot be changed to a value that provides less access.|Extensibility|Error|
|[AS0050](appsourcecop-as0050.md)|The extensibility of an application object cannot be removed|Extensibility|Error|
|[AS0051](appsourcecop-as0051.md)|Manifest property is required for AppSource submission|Extensibility|Error|
|[AS0052](appsourcecop-as0052.md)|The property 'url' must be set to a valid URL|Extensibility|Error|
|[AS0053](appsourcecop-as0053.md)|The compilation target of an application must be a value that is allowed in a multi-tenant SaaS environment|Extensibility|Error|
|[AS0054](appsourcecop-as0054.md)|The AppSourceCop configuration must specify the set of affixes used by the application|Configuration|Error|
|[AS0055](appsourcecop-as0055.md)|The AppSourceCop configuration must specify the list of countries/regions targeted by the application|Configuration|Hidden|
|[AS0056](appsourcecop-as0056.md)|The country/region codes specified in the 'supportedCountries' property must be valid ISO 3166-1 alpha-2 codes|Configuration|Warning|
|[AS0057](appsourcecop-as0057.md)|Translations must be provided for all the locales in which the application will be available|Extensibility|Hidden|
|[AS0058](appsourcecop-as0058.md)|Only use AssertError in Test Codeunits|Extensibility|Error|
|[AS0059](appsourcecop-as0059.md)|Reserved database tables are read-only in a multi-tenant environment|Extensibility|Error|
|[AS0060](appsourcecop-as0060.md)|Unsafe methods cannot be invoked in an AppSource application|Extensibility|Error|
|[AS0061](appsourcecop-as0061.md)|Procedures must not subscribe to CompanyOpen events|Extensibility|Error|
|[AS0062](appsourcecop-as0062.md)|Page controls and actions must use the ApplicationArea property|Extensibility|Error|
|[AS0063](appsourcecop-as0063.md)|Removing a var modifier in events is not allowed|Upgrade|Error|
|[AS0064](appsourcecop-as0064.md)|Interface implementations that have been published must not be deleted.|Upgrade|Error|
|[AS0065](appsourcecop-as0065.md)|Interfaces that have been published must not be deleted.|Upgrade|Error|
|[AS0066](appsourcecop-as0066.md)|A new method to an interface that has been published must not be added.|Upgrade|Error|
|[AS0067](appsourcecop-as0067.md)|Adding an interface to an enum that has been published must have a default implementation.|Upgrade|Error|
|[AS0068](appsourcecop-as0068.md)|Changing a table extension's target is not allowed.|Upgrade|Error|
|[AS0069](appsourcecop-as0069.md)|An enum field replacing an option field should have at least the same number of members.|Upgrade|Error|
|[AS0070](appsourcecop-as0070.md)|An enum field replacing an option field should preserve the member names.|Upgrade|Error|
|[AS0071](appsourcecop-as0071.md)|An enum field replacing an option field should preserve the member ordinal values.|Upgrade|Error|
|[AS0072](appsourcecop-as0072.md)|The ObsoleteTag property and the Tag in the Obsolete attribute must be set to the next release version.|Design|Hidden|
|[AS0073](appsourcecop-as0073.md)|Obsolete Tag must be set.|Design|Hidden|
|[AS0074](appsourcecop-as0074.md)|The Obsolete Tag must be the same across branches.|Design|Hidden|
|[AS0075](appsourcecop-as0075.md)|Obsolete Reason must be set.|Design|Warning|
|[AS0076](appsourcecop-as0076.md)|Obsolete Tag format.|Design|Hidden|
|[AS0077](appsourcecop-as0077.md)|Adding a var modifier in events is not allowed|Upgrade|Error|
|[AS0078](appsourcecop-as0078.md)|Adding or removing a var modifier in external procedures is not allowed|Upgrade|Error|
|[AS0079](appsourcecop-as0079.md)|An affix is required for procedures defined in extension objects.|Extensibility|Warning|
|[AS0080](appsourcecop-as0080.md)|Fields must not decrease in length|Upgrade|Error|
|[AS0081](appsourcecop-as0081.md)|InternalsVisibleTo should not be used as a security feature.|Extensibility|Warning|
|[AS0082](appsourcecop-as0082.md)|It is not allowed to rename an enum value.|Upgrade|Error|
|[AS0083](appsourcecop-as0083.md)|It is not allowed to delete a value from an enum.|Upgrade|Error|
|[AS0084](appsourcecop-as0084.md)|The ID range assigned to the extension must be within the allowed range|Extensibility|Error|
|[AS0085](appsourcecop-as0085.md)|Use the 'application' property instead of specifying explicit dependencies.|Extensibility|Warning|
|[AS0086](appsourcecop-as0086.md)|Fields must not increase in length|Upgrade|Warning|
|[AS0087](appsourcecop-as0087.md)|Translations of enum value captions must not contain commas|Extensibility|Warning|
|[AS0088](appsourcecop-as0088.md)|Objects with an ID that can be referenced and which have been published must not be deleted.|Upgrade|Error|
|[AS0089](appsourcecop-as0089.md)|Objects that can be referenced and which have been published must not be deleted.|Upgrade|Error|
|[AS0090](appsourcecop-as0090.md)|Objects that can be referenced and which have been published must not be renamed.|Upgrade|Error|
|[AS0091](appsourcecop-as0091.md)|One or more dependencies of the previous version of the extension could not be found.|Upgrade|Error|
|[AS0092](appsourcecop-as0092.md)|The app.json file must specify an Azure Application Insights resource.|Configuration|Warning|
|[AS0094](appsourcecop-as0094.md)|Permission Sets should not be defined in XML files.|Configuration|Warning|
|[AS0095](appsourcecop-as0095.md)|The access modifier of a table field cannot be changed to a value that provides less access.|Configuration|Error|
|[AS0096](appsourcecop-as0096.md)|The name of an extension cannot be changed.|Configuration|Error|
|[AS0097](appsourcecop-as0097.md)|The publisher name of an extension cannot be changed.|Configuration|Error|
|[AS0098](appsourcecop-as0098.md)|An affix is needed.|Extensibility|Warning|
|[AS0099](appsourcecop-as0099.md)|The member ID should be within the allowed range|Extensibility|Info|
|[AS0100](appsourcecop-as0100.md)|The 'application' property must be specified in the app.json file.|Extensibility|Error|
|[AS0101](appsourcecop-as0101.md)|The 'Isolated' argument cannot be changed, added, or removed.|Upgrade|Error|
|[AS0102](appsourcecop-as0102.md)|Cannot add a return value to a procedure|Upgrade|Error|
|[AS0103](appsourcecop-as0103.md)|Table definitions must have a matching permission set.|Configuration|Warning|
|[AS0104](appsourcecop-as0104.md)|The extension name is not valid.|Extensibility|Error|
|[AS0105](appsourcecop-as0105.md)|Object pending obsoletion contains an expired ObsoleteTag.|Design|Error|
|[AS0106](appsourcecop-as0106.md)|A variable belonging to the public API cannot be removed.|Design|Error|
|[AS0107](appsourcecop-as0107.md)|The access modifier of a variable that belongs to the public API cannot be changed to a value that provides less access.|Design|Error|
|[AS0108](appsourcecop-as0108.md)|The type of a variable belonging to the public API cannot be changed.|Design|Error|
|[AS0109](appsourcecop-as0109.md)|The type of the table has changed from Normal to Temporary.|Upgrade|Warning|
|[AS0110](appsourcecop-as0110.md)|Permission set extensions should not include permissions for objects defined in another application.|Extensibility|Warning|
|[AS0111](appsourcecop-as0111.md)|Permission set extensions should not include permission sets defined in another application.|Extensibility|Warning|
|[AS0112](appsourcecop-as0112.md)|Permission set extensions should not include permission sets which include permissions for objects defined in another application.|Extensibility|Warning|
|[AS0113](appsourcecop-as0113.md)|Permission set extensions should not include wildcard permissions.|Extensibility|Warning|
|[AS0114](appsourcecop-as0114.md)|The name of an external business event cannot be changed.|Upgrade|Error|
|[AS0115](appsourcecop-as0115.md)|The obsolete state cannot change directly from 'No' to 'Removed'.|Upgrade|Error|
|[AS0116](appsourcecop-as0116.md)|Source application for the moved symbol cannot be found.|Upgrade|Warning|
|[AS0117](appsourcecop-as0117.md)|Application object is moved without the use of PendingMove.|Upgrade|Warning|
|[AS0118](appsourcecop-as0118.md)|The length of a field part of the primary key cannot change.|Upgrade|Error|
|[AS0119](appsourcecop-as0119.md)|The value of the MovedTo property in the source symbol does not match the destination AppId.|Upgrade|Warning|
|[AS0120](appsourcecop-as0120.md)|The value of the MovedFrom property in the destination object does not match the source AppId.|Upgrade|Warning|
|[AS0121](appsourcecop-as0121.md)|When a symbol is moved the name must remain the same.|Upgrade|Error|
|[AS0122](appsourcecop-as0122.md)|Source symbol for the moved symbol cannot be found in the package with the given AppId.|Upgrade|Warning|
|[AS0123](appsourcecop-as0123.md)|A key cannot be declared as clustered on an existing table.|Upgrade|Error|
|[AS0124](appsourcecop-as0124.md)|Changing an extension object's target is not allowed.|Upgrade|Error|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

> [!NOTE]  
> Several rules enforced by the AppSourceCop analyzer are incompatible with rules enforced by the PerTenantExtensionCop. Make sure to enable only one of these at a time.

> [!NOTE]  
> Failing to comply with the rules whose default severity is set to `Error` will fail the submission of your extension to the AppSource marketplace. It is recommended, but not mandatory to comply with the rules whose severity is marked as `Warning` or `Info`. 

## Configuration
    
The AppSourceCop analyzer can be further configured by adding a file named `AppSourceCop.json` in the project's root folder. The AL Language extension will offer IntelliSense for this file.

The following table describes the settings in the `AppSourceCop.json` file:

|Setting|Mandatory|Value|
|-------|---------|-----|
|name|No|The name of a previous version of this package with which you want to compare the current package for breaking changes.|
|publisher|No|The publisher of a previous version of this package with which you want to compare the current package for breaking changes.|
|version|Yes|The version of a previous version of this package with which you want to compare the current package for breaking changes.|
|mandatoryAffixes|No|Affixes that must be prepended or appended to the name of all new application objects, extension objects, and fields.|
|supportedCountries|No|The set of country codes, in the alpha-2 ISO 3166 format, in which the application will be available.|
|targetVersion|No|Specifies the next Major.Minor version of the extension in the current branch in order to validate the ObsoleteTag values with [AS0072](appsourcecop-as0072.md). This is only relevant when the default obsoleteTagPattern '(\\d+)\\.(\\d+)' is used. This property is being deprecated in favor of obsoleteTagVersion.|
|obsoleteTagVersion|No|Specifies the next Major.Minor version of the extension in the current branch in order to validate the ObsoleteTag values with AS0072. This is only relevant when the default obsoleteTagPattern '(\\d+)\\.(\\d+)' is used.|
|obsoleteTagPattern|No|The Obsolete tag pattern used by AS0076. This should be a valid regular expression. By default, the pattern '(\\d+)\\.(\\d+)' is used.|
|obsoleteTagPatternDescription|No|A human-readable description for the ObsoleteTagPattern regular expression. This is used in diagnostics reported by AS0076. By default, 'Major.Minor' is used.|
|obsoleteTagAllowedVersions|No|A comma-separated list of Major.Minor versions that will be allowed as ObsoleteTag values by [AS0072](appsourcecop-as0072.md). This is only relevant when the default obsoleteTagPattern '(\\d+)\\.(\\d+)' is used.|
|baselinePackageCachePath|No|The path to the folder containing the baseline and its dependencies with which you want to compare the current package for breaking changes. By default, the package cache path for the current project is used (see 'al.packageCachePath' setting).|
|obsoleteTagMinAllowedMajorMinor|No|The minimum version of ObsoleteTag (Major.Minor) allowed during compilation. Referencing an obsolete pending object with an obsolete tag lower than the specified version will trigger the rule [AS0105](appsourcecop-as0105.md). Note that enabling this setting has a performance impact.|

The `name`, `publisher`, `version` properties are used for specifying a previous version of the current package. This package must be located in the baseline package cache folder of your extension. This cache can be specified using the `baselinePackageCachePath` property. If this property is not specified, the dependency package cache path of the extension will be used instead. The `al.packageCachePath` setting allows you to specify the path to the folder that will act as the cache for the dependencies symbol files used by your project. AppSourceCop will compare the previous version of your extension with its current version and will report any breaking changes introduced by the current package.

The `mandatoryAffixes` property specifies strings that must be prepended or appended to the names of all new objects, extension objects and fields. By using these affixes, you can prevent clashes between objects added by your extension and objects added by other extensions.

The `supportedCountries` property specifies the codes that correspond to the countries/regions for which the product allows AppSource submissions. For more information, see [Availability and supported Countries/Regions and Translations](../../compliance/apptest-countries-and-translations.md)

The properties `obsoleteTagVersion`, `obsoleteTagPattern`, and `obsoleteTagPatternDescription` can be used to enable additional validation on object obsoletion. These are not required for AppSource submissions.

## Example
In the following example, we will configure AppSourceCop to validate that all new elements have a name that contains one of the specified affixes.

> [!NOTE]  
> Make sure that code analysis is enabled and `${AppSourceCop}` is specified in the list of enabled code analyzers. For more information see [AL Language Extension Configuration](../devenv-al-extension-configuration.md).

We start by creating the default "Hello world" extension.
```AL
pageextension 50100 CustomerListExt extends "Customer List"
{
    trigger OnOpenPage();
    begin
        begin
            Message('App published: Hello world');
        end;
    end;
}
```

We continue by adding the configuration file `AppSourceCop.json` in the project's root folder and setting its content to the following. 

```json
{
    "mandatoryAffixes": [ "Foo", "Bar" ]
}
```

> [!IMPORTANT]  
> If you are running a multi-root workspace environment, you must have one `AppSourceCop.json` file in the root folder of each of the projects. For more information, see [Working with multiple AL project folders within one workspace](../devenv-multiroot-workspaces.md).


You are immediately greeted by the following error message:
```
AS0011: The identifier 'CustomerListExt' must have at least one of the mandatory affixes 'Foo, Bar'.
```

Prepending **Foo** to the name of the page extension object will fix this error and prevent clashes between this page extension and page extensions added by other developers.

> [!NOTE]  
> It is still possible to use the `mandatoryPrefix` and `mandatorySuffix` properties in the `AppSourceCop.json`. For more information see [AS0011](appsourcecop-as0011.md).

## See Also  
[Using the Code Analysis Tool](../devenv-using-code-analysis-tool.md)  
[Ruleset for the Code Analysis Tool](../devenv-rule-set-syntax-for-code-analysis-tools.md)  
[Using the Code Analysis Tools with the Ruleset](../devenv-using-code-analysis-tool-with-rule-set.md)  
