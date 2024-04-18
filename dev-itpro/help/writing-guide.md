---
title: Authoring guide for Business Central
description: Tips and tricks for authoring in MarkDown files when you extend or customize the Help for Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.custom: na
ms.topic: conceptual
ms.date: 09/09/2021
ms.author: solsen
---

# Authoring Guide for [!INCLUDE[prod_long](../developer/includes/prod_long.md)]

If you're contributing to the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] Help, or if you're customizing and extending the Microsoft content for your own solution, you'll probably want to use the same tools, processes, and style guide that Microsoft uses.  

## Resources

- The [Microsoft Style Guide](/style-guide/welcome/) is published online
  
  The content on the learn.microsoft.com site generally follows the Microsoft Style Guide. The content for [!INCLUDE [prod_short](../developer/includes/prod_short.md)] varies in certain ways, partly with product-specific terminology, and a more conservative approach to contractions, for example. Also, since navigation in the [!INCLUDE [prod_short](../includes/prod_short.md)] user interface is different from that of other Dynamics 365 apps, our guidance for steps that describe such navigation is slightly different. For more information, see the [Write for accessibility](#write-for-accessibility) section.  
- [Contribute to the Help](contributor-guide.md) shows you the basics of collaborating on content for [!INCLUDE [prod_short](../developer/includes/prod_short.md)]

- The [Docs Contributor Guide](/contribute/) has many tips and tricks for authoring in MarkDown

- The [Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack) adds productivity tools to Visual Studio Code  

## Write for accessibility

At Microsoft, we write for accessibility, which also means that the same content applies to interactions with the software across devices, regardless of input method, for example. For more information, see [Describing interactions with UI](/style-guide/procedures-instructions/describing-interactions-with-ui) in the Microsoft Style Guide. The product-specific guidance is found in the [Navigation in the product](#navigation-in-the-product) section.  

### Accessible illustrations

The accessibility requirements also impact metadata for illustrations, such as the following:

```markdown
:::image type="content" source="media/illustration.png" alt-text="Text used by screen readers.":::
```

Most of Microsoft's articles use a different MarkDown formatting for illustrations, such as the following:

```markdown
![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do")
```

Both formats are valid MarkDown, and both formats are supported by DocFx.exe. For more information, see [Images](/contribute/markdown-reference#images) in the Docs Contributor Guide.  

### Navigation in the product

The [Describing interactions with UI](/style-guide/procedures-instructions/describing-interactions-with-ui) article in the Microsoft Style Guide also applies to [!INCLUDE [prod_short](../includes/prod_short.md)] content. However, the navigation in [!INCLUDE [prod_short](../includes/prod_short.md)] is different from many other Microsoft products, and users can even pin actions and personalize  their workspace in other ways that change the navigation path.  

As a result, we often choose to be not specific about how to find a given action. We write *Choose the Register Payments action*, rather than try to predict if the user will find that action pinned to their action bar or hidden away under **More options**, for example.  

But we also have written something like this: *To map text on the vendor invoice to a specific debit account, on the Actions tab, in the General group, choose Map Text to Account, and then fill the Text-to-Account Mapping Worksheet page.*. In this example, the guidance is now outdated - the actual action is, in the default configuration of the CRONUS demonstration company, easily discoverable in the **Process** part of the action bar, which is the first place people tend to look for things. In other words, the instructions *Choose the Map Text to Account action* would have made it easier for users to find the action.  

The following table provides examples of how to write about the user interface in a helpful but future proof way, with accessibility in mind.

|Page type  |Example  |Description  |
|---------|---------|---------|
|List | On the **Opportunity List** page, select the opportunity, and then choose the **Assign Sales Quote** action.|Most list pages have relatively few actions, so let's keep things simple. Also, most actions in the action bar for list pages apply to the line entry that you've selected. |
|Card     |On the **General** FastTab, in the **External Document No.** field, enter the invoice number. | Cards can have several FastTabs that each have multiple fields. Telling the user to find a certain field on a specific FastTab can save time.|
|Card |On the **Customer Card** page, choose the **Merge With** action.| This type of action is relatively easy to find in the **Actions** part of the action bar. |
|Document  |On the **Lines** FastTab, in the **Item No.** field, enter the number of an inventory item or service.  |Documents, such as sales orders, have a header section and a lines section, typically. So letting the user know which section the field is in can save time.|

## Authoring in MarkDown

The [!INCLUDE [prod_short](../developer/includes/prod_short.md)] content is styled using a MarkDown syntax as described in the next sections. Extended guidance is available in the [MarkDown Reference](/contribute/markdown-reference) section in the Docs Contributor Guide.

### Headings

Use `#` for headings. For more information, see [Headings](/contribute/markdown-reference#headings) in the Docs Contributor Guide.  

In the source files for the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] content, which publishes as English (US) on the learn.microsoft.com site, the title of an article is expected to use Title Case (capitalize each word, except prepositions) whereas subsequent headings use Sentence case (capitalize the first word, only). The Microsoft Style Guide recommends a different approach.

### Metadata

The content on the learn.microsoft.com site includes metadata that is used by the site and feeds our internal telemetry dashboards. The metadata is required for Microsoft's content but not necessarily for content that extends or customizes Microsoft's content.

However, some metadata is recommended as a best practice as outlined in the following table.

|Metadata tag  |Description  |
|---------|---------|
|title |Used by search engines. Recommended length of 60-70 characters, including spaces. We recommend that the title metadata is the same as the first heading in the article.|
|description|Used by search engines. Recommended length of 100-160 characters, including spaces. |
|author     |GitHub account of the main contributor to the article. |
|ROBOTS|Apply this tag if you customize one of Microsoft's articles and deploy that to your website. By applying the metadata `ROBOTS: NOINDEX, NOFOLLOW`, you help make sure that search engines will find the original article rather than your customized version. Users of your Help will still be able to find the customized article through context-sensitive Help links and other links.  |

### Bulleted lists

Use `-` or `*` to create bullets as shown in the following example:

```MarkDown
The following options are available:

- first option
- second option
- third option
```

> [!TIP]
> It doesn't matter if you use `-` or `*`, but the current version of the Docs Authoring Pack requires each article to use one or the other and not mix them up.

As a best practice, the MarkDown validation in the current version of the Docs Authoring Pack recommends a blank line between options in a bulleted list for better readability in MarkDown.

### Ordered lists

Use numbers for ordered lists. Don't add spaces between the lines.

```MarkDown
1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Payment Journal**, and then choose the related link.
2. In the **Payment Journal** window, on the first journal line, enter the relevant information about the payment entry.
3. To apply a single vendor ledger entry:
4. In the **Applies-to Doc. No.** field, choose the field to open the **Apply Vendor Entries** window.
```

### Bold and italics syntax

Use ```**bold**``` and ```*italics*```

### Tables

For tables in the body, use the markdown syntax. The Docs Authoring Pack for Visual Studio Code has a shortcut for adding a table, and you can also use [Tables Generator](https://tablesgenerator.com/markdown_tables).

```MarkDown
| To   | See                       |
|------|---------------------------|
|<text>|<link>|
| | |
| | |
```

MarkDown syntax for nested tables is limited, so we recommend using HTML-syntax for nested tables in ordered and unordered lists use HTML-syntax.

### Placeholders

Rather than repeating text in two or more articles, use *includes*. For more information, see [Included Markdown files](/contribute/markdown-reference#included-markdown-files).  

For [!INCLUDE [prod_short](../includes/prod_short.md)], we use includes for boilerplate text, for content that is repeated in more than one article, and for the product name. That way, we can make changes in just one location - and so can you.  

> [!TIP]
> In the [dynamics365smb-docs](https://github.com/MicrosoftDocs/dynamics365smb-docs) repo, the includes are in the `business-central\includes` subfolder.
>
> In December 2020, the two placeholders for the product name, prodshort.md and prodlong.md, were renamed to prod_short.md and prod_long.md. The change solved a problem internally at Microsoft, because we have a tool that helps identify spelling error, and that tool generated warnings for prodshort.md and prodlong.md.

### Comment syntax

Useful for sections that aren't ready and won't pass build checks.

```MarkDown
<!-- Comments -->
```

Examples:

```MarkDown
<!-- [Managing Payables](payables-manage-payables.md)-->
<!-- This is a paragraph that spans more lines and I can just put the comment tag
at the beginning and end of it -->
```

### Links

Ordinary link to a different article in the same folder

These links have the format ```[link text](filename.md)```.

Example:
```[Managing Payables](payables-manage-payables.md)```

### Link to a article in a subfolder of the source article

These links have the format ```[link text](subfolder/filename.md)```.

For example, you want to link to payables-manage-payables.md from ui-work-general-journals.md, where the folder structure is as follows:

- articles
    - ui-work-general-journals.md
- ManagePayables
    - payables-manage-payables.md

Here's the link:
```[Manage Payables](ManagePayables/payables-manage-payables.md)```

### Link to a article in a different folder than source article

These links have the format ```[link text](../folder/filename.md)```.

For example, you want to link to payables-manage-payables.md from receivables-manage-receivables.md, where the folder structure is as follows:

- articles
  - ManageReceivables
    - receivables-manage-receivables.md
    - ui-work-general-journals.md
    - ManagePayables
      - payables-manage-payables.md

Here's the link:
```[Manage Payables](../ManagePayables/payables-manage-payables.md)```

### Link to a place in the same article

From within an article, you can create a link to a specific heading in the same article. You can create the link like other links except with the following format:

```[link text](#target-heading)```

target-heading is the text of the heading that you want to link to, except it's all lowercase and spaces between words are replaced with hyphens. For example, here's the link:
```[How Autoscaling Works](#how-autoscaling-works)```

To the heading:
```## How Autoscaling Works```

### Link to a place in a different article

From an article, you can create a link to a specific heading in another article. You can create the link like other links except with the following format:

```[link text](targetarticlename#target-heading)```

*targetarticlename* is the file name of the article, including the .md file type.
target-heading is the text of the heading that you want to link to, except it's all lowercase and spaces between words are replaced with hyphens.

For example, to link to the heading "How autoscaling works" in the article Autoscaling.md, add the following code:
```[How autoscaling works](Autoscaling.md#how-autoscaling-works)```

### <a name="anchorlink"></a>Links to anchors across languages

[!INCLUDE [docslinkanchor](../developer/includes/docslinkanchor.md)]

### Line breaks (soft return)

In the editor, add two blank spaces at the end of the sentence and hit return. This is used in the See Also list. (See Also must be heading 2.)

### Continue steps after a non-step para

Enter four spaces in front of the non-step para. Otherwise, the non-step para will restart the step sequence.

### TOC

The TOC structure of the TOC.md file is as follows:

```MarkDown
#[Overview](overview.md)
 ##[Topic 1](topic-1.md)
 ##[Topic 2](topic-2.md)
 ##[Topic 3](topic-3.md)
 ##[Topic 4](topic-4.md)
```

### Standard phrases

All fields in Business Central have tooltips; therefore, don't document fields in Help. To refer readers to the tooltips, use this standard phrase where relevant:

> "Choose a field to read a short description of the field or link to more information."

For more information, see [Business Central User Assistance Model](../user-assistance.md).

### Recycle content

Rather than copy-pasting content that you want to surface in two or more places, use *includes*. For more information, see [Included Markdown files](/contribute/markdown-reference#included-markdown-files) in the Docs Contributor Guide.  

### Article titles

- Use imperative verb form for step-based articles ("Pay vendors").
- Use gerund verb form for conceptual, non-step articles. ("Paying Vendors")
- Use nouns for highest-level articles. ("Sales")

### File naming

In this section, we describe best practices for file names of MarkDown files that will publish to a website. The guidelines make the files easier to work with and better for search engines to index.

#### Rules

- No spaces or punctuation characters. Use hyphens to separate the words in the file name.
- Use all lowercase letters
- No more than 80 characters - this is a publishing system limit
- Use action verbs that are specific such as develop, buy, build, troubleshoot. No -ing words.
- No small words - don't include a, and, the, in, or, etc.
- All files must be in markdown and use the .md file extension.

    New FAQ files must use YAML format. For an example, see the `https://github.com/MicrosoftDocs/dynamics365smb-docs/blob/live/business-central/faq-copy-paste.yml` file.

#### Examples of file names

|Article title |Naming  |
|------------|--------|
|Select a Company|ui-how-select-company.md|
|Enter Criteria in Filters|ui-enter-criteria-filters.md|
|Troubleshooting: Record Locked by Another User|ui-troubleshoot-record-locked-another-user.md|
|Changing Basic Settings|ui-change-basic-settings.md|
|Sales|sales-manage-sales.md|
|Set Up Currencies|finance-setup-currencies.md|
|Set Up Purchasers|purchases-how-setup-purchasers.md|
|Understanding Session Timeouts|admin-understand-session-timeouts.md|
|Manage Data Encryption|admin-manage-data-encryption.md|

### Country-specific content

To simplify content localization and translation, country-specific articles live in country-specific folders. The TOC entries live under the "Local Functionality" parent node.  

## User interface text

If you're a technical writer, then you're likely to either write or edit user interface text, such as captions, warnings and error messages, tooltips, and teaching tips. In this section, we describe our internal guidance, but you can choose differently.  

### Tooltips

[!INCLUDE [ua-tooltips](../includes/ua-tooltips.md)]

#### Examples of tooltips

[!INCLUDE [ua-tooltips-examples](../includes/ua-tooltips-examples.md)]

### Errors, warnings, and other messages

Messages that users see when they work in [!INCLUDE [prod_short](../developer/includes/prod_short.md)], some as  confirmations, others as warnings, for example, are defined in code. In this section, we describe key things to keep in mind when writing or editing this type of user interface text.

- Be brief but descriptive with clear call to action.

    Especially true for errors and warnings that must help the user unblock themselves.

- Write to be understood worldwide.

  - Write content that's easy to read and translate.  
  - Avoid long, complex sentences. Break them up into shorter sentences that are easier to read and comprehend.
  - Use lists and tables instead of complicated sentences and paragraphs.  
  - Use standard English grammar. In particular, avoid incomplete sentences.  
  - Include words that native English speakers often omit, such as that and the.  

- Only use placeholders for variables and field values where the result depends on context.  

    Write out all static captions, where the value is always known.  

- All placeholders complicate translation, also valid ones, even when they are preceded by code comments.  

    A typical challenge is to determine the gender of the noun that a placeholder represents. This is problematic for target languages such as French, German, and Russian.

    |Use|Instead of  |
    |---------|---------|
    |The document has been posted. | The %1 has been posted. (Translators can't determine the gender.) |
    |The Unit Cost field is updated. | The %1 field is updated. (Where %1 always represents "Unit Cost".)|
    |Document %1 contains invalid characters. (Where %1 represents a given document ID.) ||
    |Option %1 is not supported. (Where %1 represents one of more options.) ||

- Don't place quotation marks around placeholders.

    However, if the placeholder represents free-text user input that is hard to distinguish, such as a payment comment on a bank transaction. The quotation marks then helps to distinguish the user input from other parts of the message.  

    Example: *The payment line with transaction text '%1' is not applied.*, where %1 = `Hi - here is my payment of invoice 1223344`.  

### Teaching tips

[!INCLUDE [2021_releasewave1](../includes/2021_releasewave1.md)]

[!INCLUDE [ua-teaching-tips](../includes/ua-teaching-tips.md)]

## See also

[Business Central User Assistance Model](../user-assistance.md)  
[Contribute to the Help](contributor-guide.md)  
[Configuring the Help Experience](../deployment/configure-help.md)  
[Generating help with the ALDoc tool](help-aldoc-generate-help.md)  
[Docs Contributor Guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)  
[Blog post: Extending and customizing the Help](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/extending-and-customizing-the-help-in-dynamics-365-business-central)  
[Blog post: Collaborate on content for Business Central](https://cloudblogs.microsoft.com/dynamics365/it/2019/08/14/collaborate-on-content-for-dynamics-365-business-central/)  

[!INCLUDE [footer-banner](../includes/footer-banner.md)]
