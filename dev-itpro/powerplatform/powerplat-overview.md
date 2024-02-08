---
title: Microsoft Power Platform integration with Business Central via virtual tables
description: Learn about integration of Power Platform with Business Central via virtual tables.
ms.custom: na
ms.date: 11/13/2023
ms.reviewer: solsen
ms.topic: overview
author: solsen
---

# Microsoft Power Platform integration with Business Central via virtual tables

> [!IMPORTANT]  
> This functionality requires version 17 or later of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online while service update 189 is required for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The release information for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] is published on the [latest version availability page](/dynamics365/released-versions/dynamics-365ce#all-version-availability).

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Virtual table, which is published on AppSource, is a virtual data source in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], and enables create, read, update, delete (CRUD) operations from [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] and Microsoft Power Platform. By definition, the data for virtual tables doesn't reside in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. Instead, it continues to reside in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. To enable operations on [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], tables must be made available as virtual tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)].

## Prerequisite reading

To work with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables, you must understand how [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] and virtual tables work. Therefore, the following documentation is a prerequisite:

- [What is [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]?](/powerapps/maker/data-platform/data-platform-intro)
- [Table overview](/powerapps/maker/data-platform/entity-overview)
- [Table relationships overview](/powerapps/maker/data-platform/create-edit-entity-relationships)
- [Create and edit virtual tables that contain data from an external data source](/powerapps/maker/data-platform/create-edit-virtual-entities)
- [Overview of creating apps in Power Apps](/powerapps/maker/)

## Virtual tables for Business Central

Open Data Protocol (OData) APIs exposed through API Pages in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] can be consumed in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] and virtual tables can be generated. 
Virtual tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] acts as regular tables and therefore also in Power Platform. Makers can now build experiences in customer engagement apps with data directly from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] with full CRUD capability and without copying to [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], and apply all the logic already residing in [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

### Using Custom APIs as basis for virtual tables

Since the virtual tables depend on APIs exposed on [!INCLUDE[prod_short](../developer/includes/prod_short.md)], custom APIs can also be used for generating virtual tables. For more information, see [Developing a Custom API](../developer/devenv-develop-custom-api.md).

## Known limitations

There are known limitations with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables including:

- Virtual tables can't be used in Charts. [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]s doesn't support virtual tables being using in Charts.
- Attachment and Images/Pictures aren't supported for virtual tables.
- BLOB to multiline support isn't supported.
- Advanced search has some limitations. Each query designed translates to an OData query against [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. 
  * The following predicates aren't supported: **Does Not Equal**, **Does Not Contain**, **Does Not Begin With**, **Does Not End With**, **Does Not Contain Data**, and **Contains Data**.
  * Combining **And** and **Or** groups across columns.
  * Filtering on related tables.

## See also

[Overview - Integrating Business Central with Microsoft Dataverse](../developer/dataverse-integration-overview.md)  
[Table Modeling](powerplat-entity-modeling.md)  
[Application Lifecycle Management for Solutions that use Virtual tables](powerplat-app-lifecycle-management.md)  
[Business Central and [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] Admin Reference](powerplat-admin-reference.md)  
[FAQ](powerplat-faq.md)  
[Developing a Custom API](../developer/devenv-develop-custom-api.md)  
