---
title: Token counting in AI
description: Learn how to count the number of tokens in your input before sending a request to Azure OpenAI
author: SusanneWindfeldPedersen
ms.author: solsen
ms.topic: reference
ms.collection:
  - get-started
  - bap-ai-copilot
ms.date: 04/01/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: jswymer
---

# Token counting in AI

Large Language Models (LLMs) operate using tokens, which are representations of ASCII or other encoded characters, rather than directly processing these characters as input or output. Token counting is the process of determining the number of tokens that will be used by your input before sending an actual request to Azure OpenAI (AOAI).

A simple way to illustrate token counting is the following example:

**Input:** "Tell me about the solar system."  
**Tokens:** 41551 757 922 279 13238 1887 13  
**Number of tokens:** 7

> [!NOTE]  
> The spacing between the numbers in the example is added purely for readability. In reality, the tokens aren't separated by spaces.

Being able to evaluate the number of tokens in your input is important because it helps you understand the cost of your request and the limitations of the model. When you evaluate the number of tokens it takes for your request, you can determine the following:

- Estimate your potential cost of your copilot. Learn more in [Azure OpenAI Service pricing overview](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/). 
- How to split up your generation into multiple generations, because models have limited context sizes and you might have more data than what fits the context size.

## Token counting - using the "AOAI Token" codeunit

In the [!INCLUDE [prod_short](includes/prod_short.md)] system application, you find the "AOAI Token" codeunit. It's located on GitHub in the following path: [https://github.com/microsoft/BCApps/blob/main/src/System%20Application/App/AI/src/Azure%20OpenAI/AOAIToken.Codeunit.al](https://github.com/microsoft/BCApps/blob/main/src/System%20Application/App/AI/src/Azure%20OpenAI/AOAIToken.Codeunit.al). 

Learn more in [“AOAI Token” codeunit](/dynamics365/business-central/application/system-application/codeunit/system.ai.aoai-token).

The AOAIToken codeunit has the following methods to support token counting:

- [GetGPT35TokenCount(Input):Integer](/dynamics365/business-central/application/system-application/codeunit/system.ai.aoai-token#getgpt35tokencount)  
- [GetGPT4TokenCount(Input):Integer](/dynamics365/business-central/application/system-application/codeunit/system.ai.aoai-token#getgpt4tokencount)  
- [GetGPTAdaTokenCount(Input):Integer](/dynamics365/business-central/application/system-application/codeunit/system.ai.aoai-token#getadatokencount)  
- [GetGPTDavinciTokenCount(Input):Integer](/dynamics365/business-central/application/system-application/codeunit/system.ai.aoai-token#getdavincitokencount)

These methods are version agnostic. For example, `GetGPT4TokenCount` works for GPT4 0613, GPT4 0125, and all versions. 

## Related information

[Get set up with Azure OpenAI Service](ai-dev-tools-get-started.md)  
[Function calling in AI](ai-system-app-function-calling.md)  