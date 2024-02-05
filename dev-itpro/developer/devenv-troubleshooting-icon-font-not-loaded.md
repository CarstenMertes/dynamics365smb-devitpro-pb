---
title: Troubleshooting Icon Font Not Loaded
description: Learn how to fix icon font issues on client types.
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: troubleshooting
author: blrobl
---

# Troubleshooting Icon Font Not Loaded

The Icon font is missing on the [!INCLUDE[nav_web](includes/nav_web_md.md)], [!INCLUDE[nav_tablet](includes/nav_tablet_md.md)], or [!INCLUDE[nav_phone](includes/nav_phone_md.md)] preventing you from seeing, for example, the plus sign in front of the **New** action.  
  
## Resolution

The reason is that the **Font download** option is disabled in your browser and the resolution is to add the [!INCLUDE[d365_bus_cent_short](includes/d365_bus_cent_short_md.md)] web site to your trusted sites in Windows 10.  
  
1. Launch **Control Plane** on your device.  
  
2. Go to **Network and Internet**, and choose **Internet Options**. A pop up window will appear.
  
3. Select the  **Security** tab, and then choose **Trusted sites** .  
  
4. Choose the **Sites** button and add the [!INCLUDE[prod_short](includes/prod_short.md)] web site.  
  
5. Click on the **Close** button and then on the **OK** button.  
  
## See Also

[Troubleshooting the Business Central Mobile App](devenv-Troubleshooting-the-Mobile-App.md)  