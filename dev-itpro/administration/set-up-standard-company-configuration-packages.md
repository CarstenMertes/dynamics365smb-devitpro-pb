---
title: Set Up Company Configuration Packages
description: Streamline your implementation process by turning a set of company types you use with most customers into company configuration packages available for reuse.
author: jswymer
ms.topic: how-to
ms.devlang: al
ms.search.keywords:
ms.search.form: 8610, 8613, 8614, 8615, 8620, 8632
ms.date: 06/20/2025
ms.author: jswymer
ms.reviewer: jswymer
---
# Set up company configuration packages

As you grow your business as a reseller of [!INCLUDE [prod_short](../includes/prod_short.md)], you likely come to rely on a set of company types that you use with most of your [!INCLUDE [prod_short](../includes/prod_short.md)] prospects. You can streamline your implementation process by turning these types into *configuration packages* that are available for reuse.  

After you set up a company in [!INCLUDE [prod_short](../includes/prod_short.md)] that suits your needs, you can create a configuration package that contains relevant setup data from this company. You can then use it when you create a new company that is to be configured in the same way.  

To facilitate the import of master data, such as customer and vendor information, you can use *configuration templates*. Configuration templates contain a set of default settings that are automatically assigned to the records imported into [!INCLUDE[prod_short](../includes/prod_short.md)]. Configuration templates are an alternative to the cloud migration tools that you can use to migrate customer data from supported products. Learn more in [Migrate on-premises data to Business Central online](migrate-data.md).

> [!TIP]
> Use these capabilities to scale your business as a reseller. Most of the relevant pages apply to both [!INCLUDE [prod_short](../includes/prod_short.md)] online and on-premises. However, some processes rely on access to the underlying database and are too complex to use for [!INCLUDE [prod_short](../includes/prod_short.md)] online. For [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises, you probably want to use Windows PowerShell to help you deploy. Learn more in [Administration of Business Central on-premises](administration.md) and [Administration of Business Central online](tenant-administration.md), respectively.  

## Configuration packages

By default, [!INCLUDE [prod_short](../includes/prod_short.md)] online comes with one configuration package for Microsoft's default application, including local functionality. You can copy that and make relevant changes in the copy.  

Many of our reselling partners create a configuration package for each functional area. For example, create a package for the manufacturing functionality and another for sales. That lets you apply and set up new areas in a company as you need them.  

Create configuration packages with most setup tables filled in, so you only need to change a few settings for each customer. For example, when you create a new company, the **No. Series** and the **No. Series Line** tables are filled in with a set of number series and starting numbers. The corresponding **No. Series** fields in the setup tables are also filled in automatically. You don't have to do the work of entering number series and other basic setup data. You can also manually change all default data that is used with RapidStart Services by using the *configuration worksheet*.  

Another approach is to create a package that includes the tables that define setup, such as:  

- General Ledger Setup  
- General Posting Setup  
- VAT Posting Setup  
- Inventory Posting Setup  
- Purchases and Payables Setup  
- Sales and Receivables Setup  
- Warehouse Setup  
- Inventory Setup  
- Manufacturing Setup  
- Fixed Asset Setup  
- Marketing Setup  
- Service Setup  

To view a complete list of setup tables in [!INCLUDE [prod_short](../includes/prod_short.md)], select the :::image type="icon" source="../developer/media/search-icon.png" border="false"::: icon, enter **Manual Setup**, and then select the related link.  

> [!TIP]
> Optionally, use the configuration worksheet to gather together and categorize the information that you want to use to configure a new company, and arrange tables in a logical way. Formatting in the worksheet is based on a simple hierarchy: *areas* contain *groups*, which in turn contain *tables*. Areas and groups are optional but useful. You can then add the worksheet lines to a new configuration package.  

## Before you create a configuration package

There are some things to consider before you create a configuration package because they affect you or your customer's ability to import it.  

### Tables that contain posted entries

You can't import data to tables that contain posted entries, like the customer, vendor, and item ledger entries tables. Don't include this data in your configuration package. You can add entries to these tables after you import the configuration package by using journals to post the entries. Learn more in [Posting documents and journals](/dynamics365/business-central/ui-post-documents-journals) in the business functionality content.

### Table names that contain special characters

Use caution if you have tables or fields that have the same temporal name but are differentiated by special characters, such as `%`, `&`, `<`, `>`, and `,`. For example, a table might contain the **Field 1** and **Field 1%** fields.

The XML processor that generates the .rapidstart files accepts only some special characters, and removes the characters it doesn't. If removing a special character, such as the `%` sign in "Field 1%," results in two or more tables or fields with the same name, an error occurs when you export or import a configuration package.  

### Permissions

The process of creating and importing a configuration package involves the following effective permissions for all tables in the package:  

- The user who exports data for the configuration package must have **Direct Read** effective permissions.
- The user who imports the configuration package must have **Direct Insert** and **Direct Modify** effective permissions.

> [!NOTE]
> The user must have direct effective permissions to the tables that are imported or exported. Indirect permissions aren't sufficient.
>
> Also, some tables don't support direct read, insert, or modify permissions. You can't include such tables in configuration packages.

### Database schema

When you export and import configuration packages between two company databases, both databases need the same schema so all data transfers successfully. The databases should have the same table and field structure, in which the tables have the same primary keys and fields have the same IDs and data types. Your configuration package must use the same version of [!INCLUDE [prod_short](../includes/prod_short.md)] as the customer environments you want to apply it to.

You can import a configuration package exported from a database with a different schema than the target database. However, any tables or fields in the configuration package that are missing in the target database aren't imported. Tables with different primary keys and fields with different data types will also not successfully import. For example, if the configuration pack includes table **50000, Customer** that has primary key **Code20** and the database to which you import the pack includes table **50000, Customer Bank Account** that has the primary key **Code20 + Code 20**, then data isn't imported.  

## Create a custom company configuration package

1. Create a new company. Learn more in [Create new companies in Business Central](/dynamics365/business-central/about-new-company) in the business functionality content.  
1. Set up the new company in the way you need. Fill in all required setup tables.  

    Optionally, use the default configuration package in the Cronus demonstration company to set up the base application. Then, add your own best practices on top.  

    Next, you add this setup to a configuration package. You can set up the tables that you want to add to the package in the **Configuration Worksheet** page and then add a configuration package to the lines in that worksheet. Or you can add the tables directly to the package in the **Configuration Package** page. The following steps assume that you prefer to set up things in the worksheet, but you don't have to.
1. Open the **Configuration Worksheet** page.  
1. Add a new line of the type **Area**, and then add groups and the tables that you want to transfer to another company to the package. [!INCLUDE [tooltip-inline-tip_md](../includes/tooltip-inline-tip_md.md)]  

    > [!TIP]  
    > Take a look at the default configuration package for the demonstration company for inspiration for how to set up the configuration.

    1. Select the **Get Tables** action. On the **Get Config. Tables** request page, specify the types of tables that you want to add to the configuration, and set the relevant filters. Then select the **OK** button.  

        To exclude the configuration questionnaires, configuration templates, and configuration worksheet tables from the package, select the **Exclude Configuration Tables** check box on the **Config Package Card** page. Otherwise, these tables are added to the list of package tables automatically when you export the package.  

    1. To add related tables, select the **Get Related Tables** action.  

        > [!NOTE]  
        > Related tables aren't added with the **Get Related Tables** action if either of the following is true:
        >
        > - The relation is conditional.  
        >     Example: If you get related tables for the **Customer** table, then the **Location** table isn't added, because it relates only conditionally to the **Customer** table, namely if the **Location Code** field in the **Customer** table is filled in.  
        > - The related table is filtered.  
        >     Example: A field in the related table has a WHERE clause. The reason for this is that the involved relations information is stored in the **Field** system table, which isn't fully accessible to the application.  
        > You must add such types of tables manually.

        For each table, you can specify which fields to exclude, and you can modify the default processing order for each field. [!INCLUDE [prod_short](../includes/prod_short.md)] checks if there are related fields that you must configure in the **Config. Package Fields** page.
    1. Optionally, for each table, modify which fields must be included in the package.

        Select a table for which you want to specify field information, and on the **Actions** tab, in the **Show** group, select **Fields**.

        - To select just the fields you want to include, select the **Clear Included** action. To add all fields, select the **Set Included** action.  
        - To specify that the field data shouldn't be validated, clear the **Validate Field** check box for the field.  
1. Assign the worksheet lines to an existing package.  

    1. Select the relevant lines, select the **Assign Package** action, and then, in the **Configuration Packages** page, select the relevant package, or create a new one.

        If the package doesn't include a table, it adds one. The package code field on the worksheet line is filled in with the code of the package that the table is assigned to.  
        If you select an existing package, you can see how many tables are already in the package by reviewing the information in the **No. of Tables** field.
1. Optionally, create a questionnaire for the most frequently used setup tables to get specific information from your prospects and customers. This information helps you set up their [!INCLUDE [prod_short](../includes/prod_short.md)].  

    1. On the **Configuration Questionnaire** page, add a new questionnaire, and then select the **Questions Areas** action.  
    1. In the **Config. Question Area** page, in the **Table ID** field, select the ID of the table for which you want to collect information. The **Table Name** field is automatically filled in.  
    1. Select the **Update Questions** action. Each field in the table is added to the questionnaire with a question mark following its caption in the **Question** field.

        You can rephrase the question to make it clear that it's a question that should be answered. For example, if a field is called **Name**, you could edit the related question to state *What is the name of the account.* You can also provide guidance in the **Reference** field, including a URL to a page that provides additional information for example.  

        You can also delete any questions that you don't want to include in the questionnaire.  

        > [!NOTE]  
        > The **Answer Option** field describes the format that the answer to the question must meet, such as *Code* or *Text*.
        >
        >  As needed, you can also define default answers in the **Answer** field. These values are used by default for custom setup. However, the person filling in the questionnaire can modify and update the answer.  

    1. Repeat steps 2 and 3 for any other areas that you want to add to the questionnaire, and then return to the **Configuration Questionnaire** page.

        Optionally, export the questionnaire to Excel. Then, you can use the Excel workbook to get answers from your prospects and customers. Each question area in the questionnaire has a worksheet.

        > [!NOTE]  
        > You might encounter the following error when you run an English version of Excel, but have your regional settings configured for a non-English language: *Old format or invalid type library.* To fix this error, make sure that the language pack for the non-English language is installed.
1. Optionally, create configuration templates to make it easier to import master data, such as customers, vendors, contacts, or items.  

    Use the built-in configuration templates, or create your own templates in the **Configuration Templates** page. Templates are useful if you're going to migrate customer data to [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises and then switch to the cloud. Learn more in [Apply company configuration packages](apply-company-configuration-packages.md).  

    You can export the templates as Excel workbooks so that you can work with customer data in Excel.  
1. Export your package as a .rapidstart file, or export it to Excel.  

The next time you're going to set up [!INCLUDE [prod_short](../includes/prod_short.md)] for a new customer, you can apply your configuration packages and get started fast. Learn more in [Apply company configuration packages](apply-company-configuration-packages.md).  

## Related information

[Apply company configuration packages](apply-company-configuration-packages.md)  

[Migrate on-premises data to Business Central online](migrate-data.md)  

[FAQ about migrating to Business Central online from on-premises solutions](faq-migrate-data.md)  

[Administration of Business Central online](tenant-administration.md)  

[Administration of Business Central on-premises](administration.md)  

[Get started as a reseller of Business Central online](get-started-online.md)  

[Onboarding experiences in Business Central](onboarding-experiences.md)  
