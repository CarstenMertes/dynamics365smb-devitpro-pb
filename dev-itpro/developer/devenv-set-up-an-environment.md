---
title: "Set Up an Environment for Developing a Module"
description: Learn how to set up the tools you need to build a module in the System Application.
ms.author: bholtorf
ms.date: 07/29/2021
ms.reviewer: bholtorf
ms.topic: how-to
author: bholtorf
---

# Set Up an Environment for Developing a Module

This topic describes how to set up an environment for developing a module in the System Application.

## Requirements

- You must have a GitHub account.
- You are familiar with the basics of [Git](https://git-scm.com/), and have the application available. You will use Git to access the GitHub repository.
- [Docker](https://www.docker.com/) is installed. You will use it to run Business Central as a self-contained application.
- [BcContainerHelper](https://www.powershellgallery.com/packages/BcContainerHelper/) is installed. You will use it to create a Docker container.
- Demo or Partner license for Business Central

## Get the Repository On Your Local Machine

1. Open the [BCApps Repository](https://github.com/microsoft/BCApps), and choose **Fork** to create a fork of the repository.
2. Choose **Code**, and then copy the URL under code to clone the forked repository.

    The URL looks like `https://github.com/<*username*\>/BCApps.git`, and <*username*> is your GitHub username.
3. Open PowerShell, and then open the directory in which you want to keep the repository files.
4. Run the **git clone \<URL>** command. Replace \<URL> with the URL you copied in step 3.
5. Open Visual Studio Code, and then go to the **src/System Application/App** folder in the cloned repository.
6. In the folder from step 5, open the **app.json** and note the **version** that is listed. You will need that in step 3 in the process of setting up a Docker container.
7. Modify the settings.json file in Visual Studio Code to include paths to .NET assemblies. The following is an example of how to set the `"al.assemblyProbingPaths"` parameter. The path to the assemblies can differ, for example, depending on where you keep them or the version you want to use.

    ```json
    "al.assemblyProbingPaths": [
        "C:/Windows/Microsoft.NET/Framework64/v4.0.30319",
        "C:/bcartifacts.cache/onprem/19.0.29894.30693",
        "C:/WINDOWS/assembly"
    ],
    ```

    For more information about the settings.json, see [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings).

## Set Up a Business Central Docker Container

1. In PowerShell, import the **BcContainerHelper** module by running the **Import-Module BcContainerHelper** command. This loads the functions from the module.
2. Run the **New-BcContainerWizard** command. This opens a new PowerShell window and allows you to configure your [!INCLUDE[d365_dev_long_md](includes/d365_dev_long_md.md)] container.
3. Complete the steps in the wizard. Make the following changes to the default values.

    1. On the **Local Docker Container or Azure VM** step, choose a local docker container.
    2. On the **Authentication, Username/Password Authentication** step, choose options **a**, **b** or **c**.
    3. On the **Container Name** step, enter a name.
    4. On the **Version** step, choose options **e** or **f**, depending on whether you want a sandbox or on-premises build.

        - Enter the version from `BCApps/src/System Application/App/app.json` after selecting option **e** or **f**.
    5. Country, US is fine.
    6. Test Toolkit, if you have a partner license, you may choose any option. If you only have a demo license, choose option **d**, **No Test Toolkit**.
    7. Premium Plan, not required.
    8. Create Test Users, not required.
    9. AL Base App Development, we will need this as we will work on the System Application.
    10. Export AL Base App, not required as we will not be working on BaseApp.
    11. AL Language Extension, not required.
    12. License, put in the path to your license file.
    13. Database, default option a.
    14. Multitenant, non-multitenant setup.
    15. We will then put in **!** to use the default option choices for the rest of the options.
4. At the end of the configuration, you should be presented with the following script:

    ```powershell
        $containerName = 'mydemo'
        $password = 'P@ssw0rd'
        $securePassword = ConvertTo-SecureString -String $password -AsPlainText -Force
        $credential = New-Object pscredential 'admin', $securePassword
        $auth = 'UserPassword'
        $artifactUrl = Get-BcArtifactUrl -type 'OnPrem' -country 'w1' -select 'Latest'
        $licenseFile = '<Path to license file>'
        New-BcContainer -accept_eula `
            -containerName $containerName `
            -credential $credential `
            -auth $auth `
            -artifactUrl $artifactUrl `
            -includeTestToolkit `
            -includeTestLibrariesOnly `
            -licenseFile $licenseFile `
            -includeAL -doNotExportObjectsToText `
            -updateHosts
    ```

   > [!NOTE]
   > If you copy the script, remember to update the path to the license file ($licenseFile). Also, if you are using a demo license, remove the **-includeTestToolkit** and **-includeTestLibrariesOnly** options.
5. Run the script to create the Docker container. This can take some time if you are running it for the first time.

## Related information
[Getting Started with Modules](devenv-getting-started.md)  
[Create a New Module in the System Application](devenv-new-module.md)  
[Module Architecture](devenv-blueprint.md)  
