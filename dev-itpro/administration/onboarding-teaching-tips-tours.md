﻿---
title: Teaching tips and in-app tours for onboarding users
description: Learn about the teaching tips that you can apply to your Business Central to help users get started.
author: sorenfriisalexandersen
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 03/22/2022
ms.author: soalex
---

# Teaching tips and in-app tours for onboarding users

A key element in educating users about [!INCLUDE [prod_short](../includes/prod_short.md)] pages and concepts is the *tour*. A tour is a sequence of *teaching tips*.  

Teaching tips can be defined at the page level, the *page teaching tip*, and be followed by teaching tips at the control level, the *control teaching tips*. Both types of teaching tips are defined by the .AL properties **AboutTitle** and **AboutText** (or their multi-language versions), and an extension can overwrite teaching tips in the default version.

## Page teaching tips

- The primary purpose is to increase the user's chance of success with the page. So, the title and description of the page teaching tip should answer the following hypothetical user questions:

  - **AboutTitle**: *What is this page about*?

  - **AboutText**: *What can I do with this page?*

- Teaching tips explain [!INCLUDE [prod_short](../includes/prod_short.md)] logic that is relevant to the page.

- Teaching tips let users discover and initiate the related tour whenever they are ready for it.

- Allow users to get on with a task right away without blocking them.

- A teaching tip can be defined for any page (including request pages for reports) in [!INCLUDE [prod_short](../developer/includes/prod_short.md)], except the role centers, and dialogs.

- After users dismiss a teaching tip and tour, they can choose or hover over the page title. This action will reopen the teaching tip, and the user can retake the tour, for example.

- On a page that is opened from the checklist, the tour is considered an invited tour, and the page teaching tip has a **Go back** button that takes the user back to the checklist.

The following illustration shows a page teaching tip that explains what the page is about and can invite the user to take a tour. The teaching tip renders in the lower left corner.  

:::image type="content" source="../media/onboarding-teaching-tip-page.png" alt-text="A page in Business Central with a page teaching tip at the lower left corner.":::

The following illustration shows how choosing the page title  will reopen the teaching tip so that the user can retake the tour.  

:::image type="content" source="../media/onboarding-teaching-tip-title.png" alt-text="Illustration of page with a teaching tip pointing to the page title.":::

## How to write page teaching tips

There are different rules for teaching tips for lists versus cards and documents.

| List page with teaching tip | Card page with teaching tip |
|-------------------------|-------------------------|
| :::image type="content" source="../media/onboarding-teaching-tip-list.png" alt-text="illustration of List Page with teaching tip.":::| :::image type="content" source="../media/onboarding-teaching-tip-card.png" alt-text="illustration of Entity Page with teaching tip.":::|
|**AboutTitle**: About sales invoices</br>**AboutText**: Sales invoices appear in this list until they're finalized and posted. After an invoice is posted, find it again in the Posted Sales Invoices list. |**AboutTitle**: About sales invoice details</br>**AboutText**: You can update and add to the sales invoice until you post it. If you leave the invoice without posting, you can return to it later from the list of ongoing invoices. |
| Answers the following questions:</br><ul></br><li>What can I do on this page in general?</li></br><li>Is there a related entity I should know about?</li></br><li>The title for a list page teaching tip will typically use the plural form, such as *About sales invoices*</li></br></ul> | Answers the following questions:</br><ul></br><li>What can I do on this page with this particular field or action?</li></br><li>What is the desired outcome of the task in this page?</li></br><li>The title for a card or document page teaching tip will typically be [entity name] + *details*,  such as *About sales invoice details*</li></br></ul> |

## What you should know about tours

- Tours are sequential teaching tips describing functionality while pointing to elements in the UI.

- The tour guides the user around the page.

- Tours can be initiated from the page teaching tip

- During a tour, a page with input fields will be in read mode.

- Tours show where to find something, what it is, what it means, what you can do with it, and what it affects.

- A control teaching tip can point out a value that the user must check to know their next step.

  - Example: The **Status** field on an invoice. When the status is open, the user can edit the invoice.

- A control teaching tip can describe the relevant timing for when to use a field or action.

  - Example: The **Post** action: When done editing, then post and send.

## How to write teaching tips for controls

There are different rules for teaching tips for input fields and actions.

| Teaching tip pointing to an input field | Teaching tip pointing to an action |
|-------------------------|-------------------------|
| :::image type="content" source="../media/onboarding-teaching-tip-field.png" alt-text="Illustration of teaching tip pointing to an input field."::: | :::image type="content" source="../media/onboarding-teaching-tip-action.png" alt-text="Illustration of teaching tip pointing to an action.":::|
|**AboutTitle:** Who you are selling to</h3></br>**AboutText:** This can be an existing customer, or you can register a new from here. Customers can have special prices and discounts that are automatically used when you enter the sales lines.|Content example for the **Post** action:</br>**AboutTitle:** When all is set, you post</br>**AboutText:** After entering the sales lines and other information, you post the invoice to make it count.​ After posting, the sales invoice is moved to the Posted Sales Invoices list. |
| <ul></br><li>The teaching tip can point to a field that may or may not have data.</li></br><li>A control teaching tip can explain an important value's meaning, such as what leaving the field blank does.</li></br><li>Avoid stating the obvious and avoid action language that tells users to do something that isn't active during the tour. For example, don't say *Enter the customer name here.* Instead, explain what to be aware of when adding a customer.</li></br></ul> | <ul></br><li>With multiple similar actions,such as **Post** and **Post & New**, call out the simplest version only.</li></br><li>Avoid action language that tells users to do something that isn't active during the tour. Don't say: *Now post the invoice*. Instead, explain what to be aware of when posting.</li></br></ul> |

## Teaching tips for FactBoxes

[!INCLUDE [2021_releasewave2](../includes/2021_releasewave2.md)]

You can add teaching tips for FactBoxes just like pages by using the **AboutTitle** and **AboutText** properties is AL.

### Adding teaching tips to FactBoxes

Teaching tips are supported on all page types that are supported in FactBoxes, including pages that display cues. Specifically, you can add teaching tips to following elements:  

- On the part control that contains the page or cue.
- The page or cue that is included in the part control.
- Controls, like fields, on the page or cue.

When adding teaching tips, consider the following limitations:

- You can't add teaching tips to actions or control add-ins in FactBoxes.
- For FactBox teaching tips to activate, the hosting page must have a page teaching tip. The page doesn't need any control teaching tips.

### How FactBox teaching tips fit into tours

The teaching tips for FactBoxes become part of the tour on the hosting page. For more information, see [Teaching tips flow](#flow).

## Teaching tips for reports
You can add teaching tips for report request pages just like normal pages by using the **AboutTitle** and **AboutText** properties in AL.

Reports must be documented because they help users take data-driven decisions and are therefore key for users to run their business processes. With teaching tips, you can help explain logic that is relevant to the report therefore allowing users to get on with their reporting task right away without blocking them. After users dismiss a teaching tip, they can choose or hover over the report title in the request page. This action will reopen the teaching tip.

The following illustration shows a report request page teaching tip that explains what the report is about. The teaching tip renders in the lower left corner.  

:::image type="content" source="../media/onboarding-teaching-tip-report.png" alt-text="A report in Business Central with a request page teaching tip at the lower left corner.":::


## <a name="flow"></a> Teaching tips flow

When designing teaching tips for a tour, it's important to understand the order in which teaching tips appear. The flow is as follows:

1. Content area of the main page
    1. Page teaching tip
    2. Control teaching tips
2. Action bar of the main page  
3. FactBoxes
    1. Part control teaching tip
    2. Page teaching tip
    3. Control teaching tips
4. System teaching tips. These teaching tips are for standard features that added are added by the platform and aren't controlled by AL.

## Rich text guidelines for teaching tips

[!INCLUDE [2022_releasewave1](../includes/2022_releasewave1.md)]

2022 release wave 1 adds support for rich text formatting for teaching tips. In this section, we take a look at the rules and guidelines to follow when using rich text in teaching tips, such as bold, italic, or links.  

### Bold

Bolded text can call out the most important points, such as

- Page names, such as **Customer Card**

- Key features, such as **Search**

- Field names, such as **Customer**

- Keyboard shortcuts, such as <kbd>Alt</kbd>+<kbd>Q</kbd>

#### Best practices for use of bolded text

- Use bolded text sparsely to avoid "shouting".

- If a page name or key feature is title cased, it might be a candidate. However, consider if using bold is needed to help understanding the message.

- Consider the difference between a page name such as the `**Posted Sales Invoices**` list (bolded and capitalized page name) as opposed to what the list contains such as `the list of posted invoices` (not capitalized and not bolded).

- If the feature is already mentioned in the title, consider if it's necessary to highlight the word again in the body text. Bolding a word once in a tip is usually enough.

  ![Example of Page Teaching Tip mentioning a page name highlighted with bold text ](../media/onboarding-teaching-tip-page-bold.png)

### Italics

Italic text can be used to bring attention to key terms or field values, such as the following:

- Key term, such as *general ledger*

- Field value, such as *Closed*

![Example of Tour Teaching Tip describing the field value Closed marked with italic ](../media/onboarding-teaching-tip-page-italics.png)

### Links to open pages

Adding links to page teaching tips can be relevant in the following cases:  

- Links can be added to page teaching tips, to help users discover a key related page in [!INCLUDE [prod_short](../includes/prod_short.md)], such as linking to the **Item Templates** page from a teaching tip on the **Items** list page.  

#### Best practices for use of links

- Use links sparsely and use only in page teaching tips. It may be confusing to send users elsewhere.

- Don't use links in tour teaching tips, as it will disrupt the tour experience.

The following illustration shows a page teaching tip with a link to guide users to a related page in [!INCLUDE [prod_short](../includes/prod_short.md)], such as the **Posted Sales Invoices** list, that users might be looking for in the **Sales Invoices** list.

![Example of a Page Teaching Tip with a link to guide users to a related page object, such as the Posted Sales Invoices list, that users might be looking for ](../media/onboarding-teaching-tip-page-link.png)

### Common pitfalls

- When you want to call out page names with bold, make sure only the caption is marked, such as `**Sales Invoice** page` or `**Sales Invoices** list`. In these examples, "page" and "list" don't have and shouldn't have rich text applied.

- Don't apply multiple rich text styles to the same word. Apply one type of formatting only, bold, italic, or a link.

## Tooltips and control teaching tips are complementary

[!INCLUDE [ua-tooltips-teachingtips](../includes/ua-tooltips-teachingtips.md)]

For more information about tooltips, see [Help users get unblocked](../user-assistance.md#help-users-get-unblocked).  

## Best practices for teaching tips and tours

- Not all pages and reports in [!INCLUDE [prod_short](../includes/prod_short.md)] need teaching tips and tours. Use teaching tips where they provide value.

- A teaching tip says *what can be done* (outcome), not *how to do it* (steps)

- A teaching tip is short, and easily read. Usually just two or three short sentences.

### Do

- Use easy to understand titles that are relevant to the element being pointed to.

- Be concise with the information you provide in a teaching tip. Short sentences or sentence fragments are best.

- Keep the tour as short as possible with 1-4 steps.

- Titles with a question are OK to use, but use them sparingly.

- Use positive cases, *don't tell what you can't do*.

- Follow [Microsoft voice guidelines](/style-guide/welcome/)

### Don't

- Don't provide how-to (steps) or instructional guidance in teaching tips. That content lives on learn.microsoft.com or in your own documentation.

- Don't use large, unformatted blocks of text in a teaching tip.

- Don't put obvious tip text, or text that simply repeats what is already on the screen.

- If you can't find anything to say, maybe reevaluate if this teaching tip is needed.

## See also

[Get Users Started with the Checklist](onboarding-checklist.md)  
[Guidelines for tooltip text](../user-assistance.md#guidelines-for-tooltip-text)  
[Onboarding experiences in Business Central](onboarding-experiences.md)  
[AboutTitle Property](../developer/properties/devenv-abouttitle-property.md)  
[AboutTitleML Property](../developer/properties/devenv-abouttitleml-property.md)   
[AboutText Property](../developer/properties/devenv-abouttext-property.md)  
[AboutTextML Property](../developer/properties/devenv-abouttextml-property.md)   

