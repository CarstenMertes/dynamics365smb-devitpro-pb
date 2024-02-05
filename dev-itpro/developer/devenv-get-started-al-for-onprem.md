---
title: Get started with C/SIDE and AL side-by-side for on-premises
description: Description of how to get started with the new development environment along with C/SIDE.
author: SusanneWindfeldPedersen
ms.date: 01/04/2024
ms.reviewer: jswymer
ms.topic: conceptual
ms.author: solsen
ms.collection: get-started
ms.service: dynamics-365-op
---

# Get started with C/SIDE and AL for on-premises

To get started with a mixed development environment of C/SIDE and AL, you must follow the steps below.

## Steps to install Business Central on-premises with C/SIDE and AL development environment

1. Install [!INCLUDE[prod_short](../includes/prod_short.md)] on-premises and make sure to include the **AL Development Environment**.
2. Download [Visual Studio Code](https://code.visualstudio.com/Download).  
3. From Visual Studio Code, locate **Extensions** in the left navigation bar, and then choose **Install from vsix**. 
4. Browse to the equivalent folder of `C:\Program Files (x86)\Microsoft Dynamics 365 Business Central\160\AL Development Environment` and then choose **Install**.
5. Now, select <kbd>Alt</kbd>+<kbd>A</kbd>, <kbd>Alt</kbd>+<kbd>L</kbd> to trigger the **AL Go!** command, choose a project, the target platform, and then choose **Your own server**.  
6. Authenticate with the credentials you use for signing into [!INCLUDE[prod_short](../includes/prod_short.md)] on-premises.  
7. In the launch.json file, update the `"server": "https://localhost"` setting with the URL for server running [!INCLUDE[prod_short](../includes/prod_short.md)] on-premises and save the file.
8. In the app.json file, add the `"target": "OnPrem"` setting.
9. Now, use the [!INCLUDE[prod_short](../includes/prod_short.md)] Administration Console to ensure that the settings on the **Development** tab are set as follows: 
    - **Allowed Extension Target Level** is set to **OnPrem**.
    - **Enable Developer Service Endpoint** checkbox is selected. 
    - **Enable Loading Application Symbol References at Server Startup** checkbox is selected.
10. Make sure to read and ensure any additional settings here [Running C/SIDE and AL Side-by-Side](devenv-running-cside-and-al-side-by-side.md).

> [!TIP]  
> For information about which sandboxes you can choose, see [Sandbox Environments for Dynamics 365 Business Central Development](devenv-sandbox-overview.md).

> [!NOTE]  
> Build and get inspired by our sample library on [GitHub](https://github.com/Microsoft/al).

## See also 
[AL Development Environment](devenv-reference-overview.md)    
[FAQ for Developing in AL](devenv-dev-faq.md)  
