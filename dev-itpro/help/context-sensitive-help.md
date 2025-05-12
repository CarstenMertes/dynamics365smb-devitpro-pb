---
title: Configure context-sensitive help
description: Learn about how to add context-sensitive help to your Business Central solution, both as an app publisher, an administrator, and as a developer.
author: SusanneWindfeldPedersen
ms.topic: how-to
ms.author: solsen
ms.date: 01/03/2024
ms.reviewer: solsen
---

# Configure context-sensitive help

A key pillar of helping users help themselves is to give them access to Help for the particular part of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] that they're working in. When you build an app for [!INCLUDE [prod_short](../includes/prod_short.md)] online, we expect you to provide Help for your solution that can be accessed from the *Learn more* links on tooltips. For more information, see [Help users learn more](../user-assistance.md#help-users-learn-more).  

Starting in 2022 release wave 1, version 20, the *Learn more* links open the Help pane. The same mechanism makes sure that your page-level links are available in the Help pane.

The *Learn more* links are generated based on two configuration settings:

* App-level configuration of the URL
* Page-level configuration of page-specific article

## App-level configuration

Specify where the Help for your functionality is published in the *contextSensitiveHelpUrl* property in the app.json file. For example, if you publish your content to `https://mysite.com/documentation`:

```json
  "contextSensitiveHelpUrl": "https://mysite.com/documentation/",

```

In this example, when the user is using your app's functionality, the *contextSensitiveHelpUrl* property specifies that the links to Help will go to the *mysite.com* site. When the user is using functionality from the base application, then the Help calls will go to the *learn.microsoft.com* site.  

If your app only supports a limited number of locales, you can specify that and shown in the following example:

```json
  "contextSensitiveHelpUrl": "https://mysite.com/{0}/documentation/",
  "supportedLocales": [
    "en-GB", "en-IE
  ],
```

The *contextSensitiveHelpUrl* and *supportedLocales* properties specify that the links to the Help for page objects in this app must go to the *mysite.com* site, but that the site only supports those two languages. All other Help calls from objects in this app will go to the default locale on the specified webserver, in this case the equivalent of `https://mysite.com/en-GB/documentation/my-feature`.  

> [!TIP]
> For tips and tricks for how to deploy content to your own website, see the [Configuring the Help Experience for [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](../deployment/configure-help.md).

Help calls for Microsoft objects will continue to go to the *learn.microsoft.com* site.  

### Localization apps

Specifically for localization apps that translate [!INCLUDE [prod_short](../developer/includes/prod_short.md)] into languages that aren't offered by Microsoft, the app.json file must be set to specify the destination of links to Help as shown in the following example:

```json
  "helpBaseUrl": "https://mysite.com/{0}/documentation/",
  "supportedLocales": [
    "ca-es"
  ],
```

The `helpBaseUrl` property represents the URL that will be used to overwrite the default Microsoft help link, which is `(/{0}/dynamics365/business-central)`. The value of the property must contain a placeholder for the user's locale culture, `{0}`.  

The `supportedLocales` property specifies the list of locales that are supported by the URL specified in the `helpBaseUrl` property and used in the translation app. If the user's current locale is among the `supportedLocales` of the extension, the user will be redirected to the help base URL that you specified.  

In this example, the *helpBaseUrl* and *supportedLocales* properties specify that the links to the Help must go to the *mysite.com* site when the user is using the product in Catalan. If the user switches the application language to English (US), then the Help calls will go to the *learn.microsoft.com* site.  

## Page-level configuration

Your target website is expected to have a default page that will display if nothing else is specified. But for each page or page extension in your app, you can specify the Help page that describes this page or the fields that the page extension adds to the page. You can do that using the *ContextSensitiveHelpPage* property as shown in the following example:

```AL
page 50101 "Reward Card"
{
    PageType = Card;
    SourceTable = Reward;
    ContextSensitiveHelpPage = 'sales-rewards';

}
```

In this example, the app contains a page object that is mapped to the *sales-rewards* Help file on the website that the app.json specifies. As a result, the *Learn more* link in the tooltips for this page will go to the equivalent of `https://mysite.com/documentation/sales-rewards`.  

Similarly, the following code example shows a page extension object that sets the *ContextSensitiveHelpPage* property so that the *Learn more* link in tooltips for the fields that this page extension adds to the Customer Card will go to the `https://mysite.com/documentation/sales-rewards` rather than the default location at learn.microsoft.com:

```AL
pageextension 50104 "Customer Card Ext" extends "Customer Card"
{
    ContextSensitiveHelpPage = 'sales-rewards';
    layout
    {...}
}
```

Starting in Business Central 2023 release wave 1, version 22, you can set the *ContextSensitiveHelpPage* property on report request pages, which will in turn show the report help link in the Help pane:

```AL
report 50105 MyReport
{
    ...

    requestpage
    {
    ...

    // This property defines the help page for this report.
    // Remember to also set contextSensitiveHelpUrl in the app.json
    ContextSensitiveHelpPage = 'business-central/sales-reports';
    }
}
```

You can use the [ContextSensitiveHelpPage property](../developer/properties/devenv-contextsensitivehelppage-property.md) to direct help calls from multiple page objects or actions to the same article. For example, Microsoft has chosen to group the context-sensitive links depending on the granularity of the help for specific area in the base application. If the help for a specific area is made more granular, then the context-sensitive help mapping is updated accordingly.

Your target website is expected to have a default page that will display if no other page is appropriate. For every page where *ContextSensitiveHelpPage* isn't set, this default help page will be shown.  

For page extensions, the value of the *ContextSensitiveHelpPage* property applies only to the controls that the page extension adds to the extended page objects. For example, if your page extension adds two new controls to the base application's Customer Card page, then the *Learn more* links in the tooltips for those two controls will go to the help page that you've specified. The *Learn more* links in the rest of the controls will go to the default help that is specified in the base application. This way, multiple apps can extend the same page object and each apply their own content-sensitive help link without overwriting the context-sensitive links for other apps.  

> [!NOTE]  
> The app.json file also contains a *help* property that is used by AppSource to specify the link that describes the app or solution.  

## UI-to-help mapping for the base application

In the current version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)], the context-sensitive links to help for the base application is based on a different UI-to-help mapping that is stored in table 2000000198 **Page Documentation**. In this table, all page objects in the default version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] are listed, and have a target help article associated with each of them. Multiple page objects can be associated with the same help article, such as when a specific workflow involves multiple pages.  

The base URL to the location of the target articles that are listed in table 2000000198 **Page Documentation** is specified at the app level as [/dynamics365/business-central/](/dynamics365/business-central/). In an extension, you can overrule this URL so that all calls for help go to your site instead. This is especially important for localization apps where all context-sensitive help calls for that app's language must go to the provider's website. For more information, see [Configuring the Help Experience](../deployment/configure-help.md).  

### Adding page-level UI-to-help mapping to the system table

You can run a script that populates the **Page Documentation** table with a mapping for Microsoft's page objects and your own page objects. This is useful if you want to reuse legacy [!INCLUDE [navnow_md](../developer/includes/navnow_md.md)] help for your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises deployment.  

> [!CAUTION]
> While it is possible to reuse the [!INCLUDE [navnow_md](../developer/includes/navnow_md.md)] legacy help with the legacy [!INCLUDE [navnow_md](../developer/includes/navnow_md.md)] help server, and to populate the system table, **Page Documentation**, we recommend that you convert any existing content to the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] format, and that you fork our GitHub repos. For more information, see [Contribute to the Help for [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](contributor-guide.md) and [Migrate Legacy Help to the [!INCLUDE[prod_long](../developer/includes/prod_long.md)] Format](../upgrade/migrate-help.md).  

In the following example, you have chosen not to apply context-sensitive help links to your page objects and instead you want to overwrite the UI-to-help mapping that Microsoft has made in the system table.  

Let's assume that the current mapping is:

|Page ID  |Page Name  |Region/Country  |Relative Path  |
|---------|-----------|----------------|---------------|
|4     |Payment Terms |W1              |sales-manage-sales|
|11300 |Financial Journal  |BE         |how-to-create-financial-journals |

You want to replace the values of the fields in the **Relative Path** column with classic page-level help files:

|Page ID  |Page Name  |Region/Country  |Relative Path  |
|---------|-----------|----------------|---------------|
|4     |Payment Terms |W1              |N_4|
|11300 |Financial Journal  |BE         |N_11300 |

Once you've done this mapping, you can apply it to the **Page Documentation** table by using a script that updates the table in the SQL Server database, for example.  

You can find a couple of suggestions for how to go about this in our blog post, [Reusing classic object-based Help on your Dynamics 365 Business Central Help Server](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/13/reusing-classic-object-based-help-dynamics-365-business-central-help-server/).

## Related information

[User assistance model](../user-assistance.md)  
[Resources for help and support for [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](../help-and-support.md)  
[Adding help links from pages, reports, and XMLports](../developer/devenv-adding-help-links-from-pages-tables-xmlports.md)  
[Migrate legacy help to the Business Central format](../upgrade/migrate-help.md)    
[Building your first sample extension with extension objects, install code, and upgrade code](../developer/devenv-extension-example.md) 
[Building an advanced sample extension](../developer/devenv-extension-advanced-example.md)  
[Development of a localization solution](../developer/readiness/readiness-develop-localization.md)  
[JSON files](../developer/devenv-json-files.md)  
[Blog post: Extending and customizing the Help](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/extending-and-customizing-the-help-in-dynamics-365-business-central)  
[Blog post: Collaborate on content for Business Central](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/collaborate-on-content-for-dynamics-365-business-central/)  
[Blog post: Reusing classic object-based Help on your Dynamics 365 Business Central Help Server](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/13/reusing-classic-object-based-help-dynamics-365-business-central-help-server/)  
[Docs contributor guide](/contribute/)  
[Docs authoring pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  

[!INCLUDE [footer-banner](../includes/footer-banner.md)]
