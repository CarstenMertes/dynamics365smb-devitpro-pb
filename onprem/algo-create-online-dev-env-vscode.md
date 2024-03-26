---
title: "Create an online development environment from Visual Studio Code"
description: "Create an online development environment from Visual Studio Code for AL-Go for Business Central."
author: freddyk
ms.custom: na
ms.date: 01/21/2022
ms.reviewer: solsen
ms.topic: conceptual
ms.service: dynamics-365-business-central
ms.author: solsen
---

# Create an online development environment from Visual Studio Code

> *The prerequisite for this how to is that you have completed the [Use Azure KeyVault for secrets with AL-Go](algo-use-azure-keyvault-for-secrets.md) instructions.*

## Steps

1. Locate the `App1` project that you created in a previous how to, and open it in Visual Studio Code.
1. Open the `cloudDevEnv.ps1` file in your `.AL-Go` folder and run the script in the **Terminal** window. The script asks for an environment name if it isn’t specified and it asks whether you want to reuse or recreate the environment if it already exists. After, the script will need access to the admin center API and will initiate a device code sign-in for this purpose.
1. Open a browser window and enter this URL `https://aka.ms/devicelogin`, then paste in the code provided, sign in and accept that you're trying to sign in with PowerShell.
1. Wait for the script to finish. All apps are compiled and published to the online environment using the development scope and Visual Studio Code is now ready for RAD development.
1. Modify your app, select <kbd>F5</kbd> and in the drop-down, select the Cloud Sandbox with your new name.
1. Your online [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment now includes your newest app changes.
1. The `launch.json` file is updated with your new environment in Visual Studio Code. You can decide whether you want to check in the changes to the repo or only use it locally.


## Next step

You can also choose to [Create Online Development Environment from GitHub](algo-create-online-dev-env-github.md).


## See also

[AL-Go Overview](algo-overview.md)  