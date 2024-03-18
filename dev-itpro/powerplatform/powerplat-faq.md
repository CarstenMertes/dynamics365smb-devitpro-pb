---
title: "Business Central virtual tables FAQ"
description: "Frequently asked questions for working with Business Central virtual tables"
ms.custom: na
ms.date: 11/13/2023
ms.reviewer: solsen
ms.topic: conceptual
author: solsen
---

# Business Central Virtual Tables FAQ

> [!IMPORTANT]  
> This functionality requires version 17 or later of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online while service update 189 is required for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The release information for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] is published on the [latest version availability page](/dynamics365/released-versions/dynamics-365ce#all-version-availability).

This article is a collection of frequently asked questions about [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables. 

### What version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] do I need?

Version 17.0 of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online is needed. Version 17 contains v2.0 of the standard APIs and improvements to the OData stack that enable APIs to be exposed and consumed as virtual tables.  

### Can a solution from an independent software vendor (ISV) take a dependency on virtual tables? What does the application lifecycle management (ALM) look like?

Yes. The virtual tables are all generated in the **MicrosoftBusinessCentralERPVE** solution, which is API-managed. In other words, the items in the solution change as you make tables visible or hidden, but the solution is still a managed solution that you can take dependency on. The standard ALM flow just takes a standard reference to a virtual table from this solution with the **Add existing** option in the ISV solution. Missing dependency of the solution will be checked when the solution is imported and during import, if a specified virtual table doesn't yet exist, the virtual table is automatically made visible.

### Which tables from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] do users see in the catalog in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]?

Generally, users see all tables exposed as API pages except for Microsoft legacy API pages: beta and v1.0.

### Do all Microsoft Power Platform users have to be users in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]?

Any user of Microsoft Power Platform who tries to access [!INCLUDE[prod_short](../developer/includes/prod_short.md)] data through a virtual table must also exist as a user in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. Therefore, technically, not *all* users have to be users in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. Only those users who access [!INCLUDE[prod_short](../developer/includes/prod_short.md)] data through virtual tables must be users in [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

### Where do I find the catalog table?

In the **Advanced find** window, the table is named **Available [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables**.

### Can I change the prefix for the virtual tables?

No. All [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables should be generated in the **MicrosoftBusinessCentralERPVE** solution, and they all have the "dyn365bc\_" prefix. This prefix won't be changed.

### How can I show, in the same grid, data from multiple virtual tables that are joined to a physical table record in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]?

This approach isn't currently possible in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)].

### If I want a default value to be entered in a column during pre-create, will an initValue on the data table then work?

Yes. Here's the order of calls:

1. [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] sends a create or update message.
2. All the existing logic on the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table and backing tables is invoked. This logic includes default value entry that might change values.
3. [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] sends another Retrieve (single) message to get the latest copy of the data, including any columns that default values were entered for.

## See Also

[Overview - Integrating Business Central with Microsoft Dataverse](../developer/dataverse-integration-overview.md)  
[Microsoft Power Platform Integration with Business Central](powerplat-overview.md)  
[Table Modeling](powerplat-entity-modeling.md)  
[Business Central and [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] Admin Reference](powerplat-admin-reference.md)  
[Application Lifecycle Management for Solutions that use Virtual tables](powerplat-app-lifecycle-management.md)
