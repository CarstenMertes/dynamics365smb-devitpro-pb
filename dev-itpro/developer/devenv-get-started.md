---
title: "Get started with AL"
description: "Description of how to get started with the development environment"
author: SusanneWindfeldPedersen
ms.date: 05/18/2022
ms.reviewer: na
ms.topic: conceptual
ms.author: solsen
ms.collection: get-started
---

# Get started with AL

[!INCLUDE [getstarted-contributions](includes/getstarted-contributions.md)]

To start writing extensions for [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)], you'll need a [!INCLUDE[prod_short](includes/prod_short.md)] tenant, Visual Studio Code, and the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]. Visual Studio Code is a cross-platform editor that you'll use for coding and debugging.

## Steps to set up a sandbox environment and Visual Studio Code

Go through the following steps to set up a sandbox environment. Having set up a sandbox environment, you get sample code that compiles and runs with just a few commands. 

> [!NOTE]  
> If you want to create a container-based sandbox, see [Get started with the Container Sandbox Development Environment](devenv-get-started-container-sandbox.md). For information about which sandboxes you can choose, see [Sandbox Environments for Dynamics 365 Business Central Development](devenv-sandbox-overview.md).

> [!IMPORTANT]  
> It's not supported to publish an extension from Visual Studio Code with the same identifiers as an extension which is already published to AppSource. Identifiers include the combination of appID and version or name, publisher, and version. If you do publish such an extension, it can be removed at any time.

1) Sign up for a [Dynamics 365 Business Central sandbox](https://signup.microsoft.com/signup?sku=6a4a1628-9b9a-424d-bed5-4118f0ede3fd&ru=https%3A%2F%2Fbusinesscentral.dynamics.com%2FSandbox%2F%3FredirectedFromSignup%3D1). 
2) Download [Visual Studio Code](https://code.visualstudio.com/Download).  
3) Download the [[!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]](https://marketplace.visualstudio.com/items?itemName=ms-dynamics-smb.al).
4) Select <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+</kbd>P</kbd> to open the **User Settings** window; here you can modify the [telemetry settings](devenv-get-started.md#telemetry-settings).
5) Select <kbd>Alt</kbd>+A</kbd>, and right after, <kbd>Alt</kbd>+<kbd>L</kbd> to trigger the **AL Go!** command, choose a path to a new empty folder and which version to run. Then choose **Microsoft cloud sandbox** as the server.  
    > [!NOTE]  
    > If you want to change your configuration at a later point in time, you can choose the **Add Configuration** button on the bottom right side, and then choose one of the available options.  
6) Enter the credentials that you provided for the sign-up.
7)   Select <kbd>Ctrl</kbd>+<kbd>F5</kbd> to deploy and run the extension on your online sandbox tenant.  

> [!NOTE]  
> For some users the <kbd>Ctrl</kbd>+<kbd>F5</kbd> shortcut key may not work due to keyboard or other settings. If it doesn't work for you, run your code by choosing **Run Without Debugging** from the **Run** dropdown in Visual Studio Code.

You now have a `HelloWorld` sample that compiles and runs. The JSON files in the project are automatically updated with the settings that allows you to select <kbd>Ctrl</kbd>+<kbd>F5</kbd> to build and deploy the solution to [!INCLUDE[prod_short](includes/prod_short.md)]. For more information, see [JSON Files](devenv-json-files.md).

## Tips and tricks

+ Use <kbd>Ctrl+Space</kbd> to activate IntelliSense at any place in the code, which will help you identify possible options.
+ Always use the `.al` extension on new files.
+ Use the built-in [snippets for code](devenv-syntax.md#ExamplesOfSnippets) by typing `t` and choose the desired snippet from the list.
+ Create objects within the right object ranges, see [Object Ranges in Dynamics 365 Business Central](devenv-object-ranges.md).
+ Build and get inspired by our sample library on [GitHub](https://github.com/Microsoft/bctech).
+ Use <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> and select **AL: Clear credentials cache** to clear the credentials cache if you want to deploy against a different environment.
+ Use <kbd>F2</kbd> to rename objects, types etc. For more information, see [Keyboard Shortcuts](devenv-keyboard-shortcuts.md#editing-in-visual-studio-code).

## JSON file settings

There are three JSON files in the project; the `app.json` file, the `launch.json` file, and the `rad.json`. The files are automatically generated for your project. For more information, see [JSON files](devenv-json-files.md) and [Work with Rapid Application Development (RAD)](devenv-rad-publishing.md).

## AL configuration settings

Use the AL configuration settings to specify general preferences for working with AL projects. For more information, see [AL Language Extension Configuration](devenv-al-extension-configuration.md).

## Telemetry settings

By default, Visual Studio Code is set up with a telemetry system to make sure that data and errors are sent to Microsoft. If you don't want to send telemetry data, you can change the `telemetry.enableTelemetry` setting from `true` to `false`.

To modify the telemetry setting, select <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> in Visual Studio Code and choose **User Settings**, which opens the `settings.json` file, and then add `telemetry.enableTelemetry` and set it to `false` like shown below.
 
```AL
"telemetry.enableTelemetry": false,
```

> [!TIP]  
> The `settings.json` file contains user and workspace settings, these options can be modified to suit your preference. If you want to modify Visual Studio Code editor options and functional behavior settings, see [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings).

## Installing and publishing an extension

To make your extension available to users, the package must be published to a specific [!INCLUDE[prod_short](includes/prod_short.md)] server instance. The extension can be installed for one or more tenants. For more information about how to install and publish an extension, see [How to: Publish and Install an Extension](devenv-how-publish-and-install-an-extension-v2.md). 

## Controlling user access to develop and publish extensions

The access to develop and publish extensions is controlled on a user or user group basis by the **EXTEND. MGT. - ADMIN** permission set. It's important that the **EXTEND. MGT. - ADMIN** isn't specified for a specific company, but left blank.

If you add new permission sets and want to control the access to develop and publish extensions, you must include indirect read and write permissions to the **Published Application** table (read – for downloading symbols, write – for publishing the app) in the permission set.

To prohibit a user from publishing, just remove the user from the **EXTEND. MGT. - ADMIN** permission set.

> [!NOTE]  
> The **EXTEND. MGT. - ADMIN** permission set was introduced in Business Central 2021 release wave 1 as a replacement for the **D365 EXTENSION MGT** permission set in earlier versions.

## Next steps

Now that you have the tools and the `HelloWorld` example up and running, you might want to create a small sample app in AL. This walkthrough guides you to create an app adding objects, code, and publishing the app to your tenant. For more information, see [Build your first sample extension with extension objects, install code, and upgrade code](devenv-extension-example.md).

## See Also

[AL Development Environment](devenv-reference-overview.md)  
[FAQ for Developing in AL](devenv-dev-faq.md)  
[Syntax](devenv-syntax.md)  
[Build your first sample extension with extension objects, install code, and upgrade code](devenv-extension-example.md)  
[AL Language Extension Configuration](devenv-al-extension-configuration.md)  
[XML Comments in Code](devenv-xml-comments.md)
