---
title: Onboard new users with the Welcome banner
description: Learn about the banner that displays when a user signs into a new company for the first time.
ms.date: 06/19/2023
ms.topic: conceptual
ms.reviewer: solsen
author: sorenfriisalexandersen
ms.author: soalex
---

# Onboard new users with the Welcome banner

When a user signs in to a new company for the first time, [!INCLUDE [prod_short](../includes/prod_short.md)] shows a welcome banner that provides a clear call-to-action.  

:::image type="content" source="../media/onboarding-banner.png" alt-text="illustration of Business Central with welcome banner with a clear call-to-action for where to get started.":::

The purpose of the banner is to give users a warm and personal welcome, reduce noise, provide a clear call to action to the get started tasks, without blocking users that wish to explore the product first.  

The welcome banner works slightly different in CRONUS evaluation companies and in non-evaluation companies, including My Company, because the banner serves different purposes in evaluation and non-evaluation companies. The following sections outline the differences.  

## The welcome banner in CRONUS evaluation companies

In a CRONUS evaluation company, the banner serves the purpose of highlighting core capabilities of [!INCLUDE [prod_short](../includes/prod_short.md)] to make the prospect excited and get them closer to subscribing to [!INCLUDE [prod_short](../includes/prod_short.md)]. By default, the welcome banner points to capabilities that Microsoft has chosen to highlight in [!INCLUDE [prod_short](../includes/prod_short.md)], such as a tour of the Role Center and spotlight tours of integrations with Excel and Teams. Consider adding other key selling point features to the checklist in CRONUS to aid you in selling [!INCLUDE [prod_short](../includes/prod_short.md)]. In CRONUS evaluation companies, the banner can't be hidden, only minimized. The banner is shown for the *Business Manager Evaluation* role, which is the default profile for the person who signs into [!INCLUDE [prod_short](../includes/prod_short.md)] online. If that user doesn't want to see the banner in CRONUS, they can switch to the *Business Manager* role. This switch happens automatically when the user chooses to start the trial with their own data in My Company.  

> [!IMPORTANT]
> The *Business Manager Evaluation* role was created specifically for the design of the CRONUS evaluation experience. The experience that is tied to this role through page customization or other directly impacted experiences *may change* from release to release, unlike other code-related changes that are goverened by our breaking change rules.
> 
>  We recommend that you build your own evaluation and demo experiences on another role if you want to make sure that your scenarios are not impacted by these changes. For example, elements on the *Business Manager* Role Center has been hidden for the *Business Manager Evaluation* role through page customization that is saved to the *Business Manager Evaluation* role. More changes for the Role Center or other pages may come in the future for the *Business Manager Evaluation* role based on Microsoft's need to pivot the CRONUS evaluation experience from the My Company experience.

## The welcome banner in My Company and other non-evaluation companies

In My Company and other non-evaluation companies, the welcome banner serves the purpose of letting the customer self-serve the last-mile setup of [!INCLUDE [prod_short](../includes/prod_short.md)]. Accordingly, the checklist tasks are more focused on guiding the user through various elements of setup. Consider how you structure the checklist for your customers with the goal of getting them set up and onboarded as fast as possible.  
For more information, see the [Get Users Started with the Checklist](onboarding-checklist.md) article.  

## Modifying the texts on the welcome banner to greet the current user

You can modify the banner texts dynamically from code. This is done by subscribing to the event **OnBeforeUpdateBannerLabels**.
Here you can set the banner texts dynamically. This is especially useful if you have profiled the customer/prospect before signing them into [!INCLUDE [prod_short](../includes/prod_short.md)]. This is done using the sign-up context, where you can get more information about the prospect before sign-up and pass that information into [!INCLUDE [prod_short](../includes/prod_short.md)] and react on that information on the welcome banner and in the checklist. For more information about pivoting the experience to become more customer-centric, see [Create customer-centric onboarding experiences using SignupContext](onboarding-signupcontext.md). The welcome banner and the checklist are great stages on which you can greet the prospect/customer according to their expectation. For example, if you have profiled the prospect to be interested in a given business area, consider setting text on the welcome banner and provide checklist content that revolves around that area.

## See also

[Get Users Started with the Checklist](onboarding-checklist.md)  
[Teaching tips and in-app tours for onboarding users](onboarding-teaching-tips-tours.md)  
[Onboarding experiences in Business Central](onboarding-experiences.md)  
