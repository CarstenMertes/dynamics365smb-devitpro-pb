---
title: Multifactor authentication for Business Central
description: This article explains how to add multifactor authentication when your solution uses Microsoft Entra ID as authentication mechanism.
author: jswymer
ms.custom: bap-template
ms.reviewer: na

ms.topic: conceptual
ms.author: jswymer
ms.date: 11/13/2023
---
# Multifactor authentication for Business Central  

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

When using Microsoft Entra authentication with [!INCLUDE[prod_short](../developer/includes/prod_short.md)], we recommend you take advantage of Microsoft Entra multifactor authentication (MFA). MFA further safeguards access to the application and data. It delivers single sign-on authentication through a range of verification options, like:

- Phone call
- Text message
- Mobile app notification
- One-time password

It can be used both on-premises and in the cloud to add security for accessing Microsoft online services, remote access applications, and more. For more information, see the [How it works: Microsoft Entra multifactor authentication](/azure/active-directory/authentication/concept-mfa-howitworks).

## Conditional access support

Conditional Access in Microsoft Entra ID provides a more granular control of MFA through policies that specify specific Cloud applications that require MFA. When creating Conditional Access policies, consider the following information:

- For Business Central online, you can select Dynamics 365 Business Central as a Cloud app to apply access policies to.

- For Business Central on-premises, you assign Business Central as a Cloud App by selecting the Microsoft Entra app registration that's used for Business Central authentication.

For more information about creating policies, see [Conditional Access: Cloud apps, actions, and authentication context](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps).


## See Also

[Security and Protection](security-and-protection.md)  
[On-Premises Security](security-onpremises.md)  
