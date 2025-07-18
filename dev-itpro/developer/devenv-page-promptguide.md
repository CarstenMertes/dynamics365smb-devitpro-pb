---
title: Prompting Using a Prompt Guide
description: Learn how to build a prompt guide for your PromptDialog pages in Business Central.
author: SusanneWindfeldPedersen
ms.author: solsen
ms.topic: overview
ms.collection:
  - bap-ai-copilot
ms.date: 06/19/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: solsen
---

# Prompting using a prompt guide

> [!NOTE]
> The prompt guide is a new feature in [!INCLUDE [prod_short](includes/prod_short.md)] 2024 release wave 1 and runtime 13 and is part of the `PromptDialog` page type for [!INCLUDE [prod_short](includes/prod_short.md)] introduced with runtime 12.1.

Learn how to enhance user interactions with Copilot in [!INCLUDE [prod_short](includes/prod_short.md)] by leveraging the prompt guide feature. A prompt guide is a predefined list of prompt texts that users can choose from when they open a `PromptDialog` page. The prompt guide helps users by providing one or more predefined prompt texts to use as input to generate content, rather than having to write up a prompt themselves. The user can choose a prompt text from the list, and the selected prompt is then inserted into the prompt input field so that the user can update it before sending to Copilot. Having prompt guides can help users to understand the different ways in which they can phrase their question or instruction to Copilot, reveal different categories of prompts, or inspire different ways of prompting to achieve similar outcomes.

## Predefined prompts

A prompt guide is implemented by using a specific action area on `PromptDialog` pages, called `PromptGuide`. The `PromptGuide` area is then defined by a list of predefined prompts that are shown to the user when the `PromptDialog` page is opened. You define these predefined prompts as questions or statements that the user can select from. Examples of predefined prompts could be "How can I...?" or "Show me the latest..." to inspire the user to ask for help or to get the latest information. The following example from the **Analyze Bank Account Reconciliations** shows how a prompt guide is implemented with the options to modify the analysis view. 

:::image type="content" source="media/promptdialog-analyze-bank.png" alt-text="Promptdialog for analyze bank account reconciliation":::

### Keep in mind

There are a couple of things to keep in mind when adding prompt guides to your `PromptDialog` pages:

- Prompt guides are optional but recommended. You can add one or many prompt guides to your prompt dialog as needed.
- Prompt texts might be organized into groups.
- When a user chooses a prompt text from the guide, this should insert the prompt text into the prompt input box. The prompt text isn't automatically sent, so that users have the opportunity to first adapt it to their unique needs.
- Using square brackets in the prompt text can be used to represent placeholders where users insert their preferred value to complete the prompt.
- The prompt text shown in the prompt guide menu might be different to the actual text that is inserted into the prompt input box.
- The AL logic for prompt guides must compute and insert the prompt text into the prompt input. This might include computed values such as dates.

## Syntax

The syntax of the `PromptGuide` area is as illustrated in the following example. The PromptGuide is an area specific to the PromptDialog page type, and it's defined in the `actions` section of the page object. The `PromptGuide` area is defined by a list of predefined prompts that are shown to the user when the `PromptDialog` page is opened. The user can select a prompt from the list, and the selected prompt is then inserted into the prompt input field so that the user can update it before sending to Copilot.

```al
actions
{
    area(PromptGuide)
    {
        action(MyPromptAction)
        {
            Caption = 'How can I...?';
            ToolTip = 'Ask Copilot for help with a specific task.';
        }
    }
}
```

The prompt guide can have groups of prompts, and each group can have a title. The following example shows how to define a group of prompts.

```al
actions
{
    area(PromptGuide)
    {
        group("Getting started")
        {
            action(MyPromptAction)
            {
                Caption = 'How can I...?';
                ToolTip = 'Ask Copilot for help with a specific task.';
            }
            
            action(MyNextPromptAction)
            {
                Caption = 'Find all [customers]?';
                ToolTip = 'Ask Copilot to help find something.';
            }
        }
    }
}
```

For a complete example of how to implement a prompt guide, learn more in [The PromptDialog page type](devenv-page-type-promptdialog.md). For nudging users to use relevant Copilot built-in features, learn more in [Prompting using a floating action bar](devenv-page-prompting-floating-actionbar.md).

## Related information

[The PromptDialog page type](devenv-page-type-promptdialog.md)  
[Prompting using a floating action bar](devenv-page-prompting-floating-actionbar.md)  
[Error handling in prompt dialogs](devenv-page-prompt-error-handling.md)
