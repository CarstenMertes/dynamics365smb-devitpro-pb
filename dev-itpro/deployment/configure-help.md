---
title: Configure the Help experience
description: Learn how to give your customers access to the right Help content for Business Central online and on-premises.
author: SusanneWindfeldPedersen
ms.topic: conceptual
ms.date: 01/08/2025
ms.author: solsen
ms.reviewer: solsen
---

# Configuring the help experience for [!INCLUDE[prod_long](../developer/includes/prod_long.md)]

The default version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] comes with conceptual overviews and other articles that publish to the [learn.microsoft.com/dynamics365/business-central/](/dynamics365/business-central/) site. This location is accessible from the Help menu and through the **Learn More** links in all tooltips. Each extension that you add will include its own tooltips and links to Help that can be accessed through the Learn More links and the <kbd>Ctrl</kbd>+<kbd>F1</kbd> keyboard shortcut.

But what if you want to deploy [!INCLUDE[prod_short](../developer/includes/prod_short.md)] locally? Or, if you have a vertical solution and want to refer your customers to your own website for Help? Or if you have a legacy Help collection based on the Dynamics NAV Help Server? These and other scenarios are also supported in [!INCLUDE[prod_short](../developer/includes/prod_short.md)].  

## Apps for online tenants

When you build an app for [!INCLUDE [prod_short](../developer/includes/prod_short.md)] using the AL developer experience, you're expected to apply tooltips and context-sensitive links to Help content on a website in accordance with the user assistance model. Learn more in the [Deploy content to your website](#deploy-content-to-your-website) section and in the [Configure Context-Sensitive Help](../help/context-sensitive-help.md) article.  
  
> [!TIP]
> The website doesn't have to be publicly accessible, but it must be accessible to all users of the solution that it supports.

You can add Microsoft's content to your website, or you can deploy just your own content. The choice is yours and depends on the requirements of your users, the size of your app, and the amount of customization you want to make.  

For inspiration for how to create a website that can host your content, explore [this tutorial](/azure/search/tutorial-python-overview). The tutorial demonstrates how to create a static web app and add a search service in a few relatively straightforward steps.  

## On-premises deployments

For deploying [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises, you can choose between using any online website or the legacy Dynamics NAV Help Server, and you can configure different Help experience for each [!INCLUDE[webserver](../developer/includes/webserver.md)] instance. For supported versions, the legacy Dynamics NAV Help Server component is a simple website that requires your Help to be in a specific format (HTML files). Other types of websites can host any content that you want to make available. Your choice depends on the needs of your solution and your users. If you add configuration for an online library, you must remove any settings for Help Server.  

> [!IMPORTANT]
> The legacy Dynamics NAV Help Server component was deprecated and removed in 2021 release wave 1 (version 18). We recommend that you invest in a different type of website. Learn more in [deprecation notice](../upgrade/deprecated-features-platform.md#the-help-server-component).

> [!TIP]
> The content on the [learn.microsoft.com/dynamics365/business-central/](/dynamics365/business-central/) site and in the various GitHub repos reflects the latest version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)], unless otherwise specified.
>
> If, for some reason, you need a copy of Microsoft's content, then get it close to the time the subsequent major version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] becomes available. For example, if you're deploying version 19.4, you could have taken a snapshot of the content in GitHub before version 20.0 became available.

[!INCLUDE [ua-github-releases](../includes/ua-github-releases.md)]

### Online library

To display content from a website that hosts your user assistance content, specify the URL in the settings for the [!INCLUDE[webserver](../developer/includes/webserver.md)]. The `navsettings.json` file must contain the following setting in the `ApplicationIdSettings` element:

```json
{
  "NAVWebSettings": {
    // [...more keys]
  },
  "ApplicationIdSettings": {
    //BaseHelpUrl:  The location of Help for this application.,
    "BaseHelpUrl": "https://mysite.com/{0}/documentation/",
     // [...more keys]
  }
}
```

> [!NOTE]
> Replace the value of the `BaseHelpUrl` key with the URL for your own website. The parameter, {0}, represents the locale of the browser that the user is using, such as en-us or da-dk, and is set automatically at runtime.

Learn more in [Configuring [!INCLUDE[webserver](../developer/includes/webserver.md)] Instances](../administration/configure-web-server.md).  

> [!TIP]
> The website doesn't have to be publicly accessible, but it must be accessible to all users of the solution that it supports.  

[!INCLUDE [ua-toolkit-onprem](../includes/ua-toolkit-onprem.md)]

### Legacy Help Server

> **APPLIES TO**: 2020 release wave 2 and earlier versions

If you want to use Help Server, then you must specify the server and port in the installation options. The Help Server website can also serve as a starting point for adding a library to your existing website, for example.  

> [!IMPORTANT]
> In version 18 and later versions, if you use the legacy Dynamics NAV Help Server component as a standalone website, then you must use the settings for the online library that is described in the previous section.

Learn more in [Configuring Microsoft Dynamics NAV Help Server](/dynamics-nav/configuring-microsoft-dynamics-nav-help-server) in the developer and administration content for [!INCLUDE[navnow_md](../developer/includes/navnow_md.md)].  

> [!IMPORTANT]
> If you use Help Server, context-sensitive Help doesn't work anymore. Neither the UI-to-Help mapping functionality that is described in [Configure Context-Sensitive Help](../help/context-sensitive-help.md), nor the original Help lookup mechanism that was based on filenames that reflected the object IDs, such as N_123.htm for the page object with the ID 123. Learn more in this blog post [Reusing classic object-based Help on your Dynamics 365 Business Central Help Server](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/13/reusing-classic-object-based-help-dynamics-365-business-central-help-server?target=_blank).

> [!TIP]
> If you're upgrading from [!INCLUDE [navsicily_md](../developer/includes/navsicily_md.md)] or later, you can reuse your existing Help Server content by replacing the product name and make any other changes that apply to your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] environment. But we encourage you to deploy the content to another website.

[!INCLUDE [nav2017classichelp](../developer/includes/nav2017classichelp.md)]

## Deploy content to your website

Currently, [!INCLUDE [prod_short](../developer/includes/prod_short.md)] has no firm requirements for the website that hosts your online library for your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online or on-premises. You can deploy your content using any tool and process including the following:

* [Azure Static Web Apps](/azure/static-web-apps/)  
* [Azure App Service](/azure/app-service/quickstart-html)  
* Third-party services  

You can explore an example of how to deploy content to an Azure web app in the article [Deploy custom help to Azure](/dynamics365/fin-ops-core/dev-itpro/help/walkthrough-help-azure). That article also describes how you can build a search service for your website. Another example is in the [Overview of adding search to a website with Python](/azure/search/tutorial-python-overview) tutorial in the Azure docs. The step for adding a search service is currently not relevant for [!INCLUDE [prod_short](../developer/includes/prod_short.md)], but you might find the guidance helpful anyway.  

> [!IMPORTANT]
> Currently, search in the [!INCLUDE [prod_short](../includes/prod_short.md)] Help pane can't access sites other than the *learn.microsoft.com* site, including Microsoft Learn.
>
> However, to help prepare for the day when partner-provided and customer-provided content can also be indexed and found by in-product search and the help pane, get your content deployed to a website and make it discoverable.

In versions older than 2022 release wave 1, the in-product search includes searching content on the [learn.microsoft.com/dynamics365/business-central](/dynamics365/business-central/index) site. In 2022 release wave 1 and later, this search is replaced by the search capabilities of the Help pane. But the restrictions remain the same.  

### Optional: Get Microsoft's content

If you deploy a solution that customizes Microsoft's default application, then you might want to include a customized version of Microsoft's business functionality content on your website. In most other cases, such as if you build an add-on app, you don't need Microsoft's content. Your own content supplements Microsoft's content in the same way that your code supplements Microsoft's code. For more information, see [Configure Context-Sensitive Help](../help/context-sensitive-help.md).  

> [!IMPORTANT]
> The remainder of this section is for those people who need a copy of Microsoft's content to deploy to a website along with their own content. In many cases, you don't need to customize Microsoft's content, and this section is irrelevant for you. However, if you deploy a customized solution on-premises or in a closed environment, then you might need to include Microsoft's content in your Help website.

[!INCLUDE [ua-robots](../includes/ua-robots.md)]

Microsoft's source files are available as downloadable packages for each major release in the [https://github.com/MicrosoftDocs/dynamics365smb-docs/](https://github.com/MicrosoftDocs/dynamics365smb-docs/releases) GitHub repo in English (US) only.

> [!TIP]
> The content on the [learn.microsoft.com/dynamics365/business-central/](/dynamics365/business-central/) site and in the various GitHub repos reflects the latest version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)], unless otherwise specified.
>
> [!INCLUDE [ua-github-releases](../includes/ua-github-releases.md)]

Use any tool or script that you prefer.

> [!IMPORTANT]
> [!INCLUDE [ua-robots](../includes/ua-robots.md)]

We suggest that your website clearly indicates what is under Microsoft's copyright and what is under your own copyright. You're still welcome to make any relevant customizations of Microsoft's content, and to deploy this customized content to your own website. But to help users clearly identify whether a given search result applies to their [!INCLUDE [prod_short](../includes/prod_short.md)] experience or not, don't apply a title suffix such as *Microsoft Docs*. We also discourage reproduction of the visual styling of the *learn.microsoft.com* site for the same reason.

## Fork the Microsoft repos, and customize or extend the content

If you want to customize or extend the Microsoft Help, you can fork our public repo for the source repo in English (US) at [https://github.com/MicrosoftDocs/dynamics365smb-docs](https://github.com/MicrosoftDocs/dynamics365smb-docs). For more information, see [Contribute to the Help](../help/contributor-guide.md).  

## Related information

[User Assistance Model](../user-assistance.md)  
[Adding Help Links from Pages, Reports, and XMLports](../developer/devenv-adding-help-links-from-pages-tables-xmlports.md)  
[Migrate Legacy Help to the Business Central Format](../upgrade/migrate-help.md)  
[Build your first sample extension with extension objects, install code, and upgrade code](../developer/devenv-extension-example.md)  
[Building an Advanced Sample Extension](../developer/devenv-extension-advanced-example.md)  
[Development of a Localization Solution](../developer/readiness/readiness-develop-localization.md)  
[Resources for Help and Support](../help-and-support.md)  
[Blog post: Extending and customizing the Help](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/extending-and-customizing-the-help-in-dynamics-365-business-central/)  
[Blog post: Collaborate on content for Business Central](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/collaborate-on-content-for-dynamics-365-business-central/)  
[Blog post: Reusing classic object-based Help on your Dynamics 365 Business Central Help Server](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/13/reusing-classic-object-based-help-dynamics-365-business-central-help-server/)  
[Working with Dynamics NAV Help Server](/dynamics-nav/microsoft-dynamics-nav-help-server)  
[Docs Contributor Guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  

[!INCLUDE [footer-banner](../includes/footer-banner.md)]
