---
title: "Table modeling"
description: "Relational modeling between Microsoft Dataverse tables used in Business Central"
ms.custom: na
ms.date: 11/13/2023
ms.reviewer: solsen
ms.topic: conceptual
author: solsen
---

# Table modeling for virtual tables

> [!IMPORTANT]  
> This functionality requires version 17 or later of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online while service update 189 is required for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The release information for [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] is published on the [latest version availability page](/dynamics365/released-versions/dynamics-365ce#all-version-availability).

Building an app requires capabilities to perform relational modeling between tables that are being used in the app. In the context of virtual tables, there will be scenarios where virtual tables and native tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] must work together to enable the desired user experience. This article explains concepts of relational modeling that can be implemented using virtual tables for [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

## Generating virtual tables

By default, virtual tables for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] don't exist in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. A user must query the catalog table to view the tables that are available in the linked instance of [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. From the catalog, the user can select one or more tables, and then request that [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] generates the virtual tables. This procedure is explained in later sections.

## Table fields

When a virtual table is generated for a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table, the system tries to create each field in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table in the corresponding virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. In an ideal case, the total number of fields will be the same in both tables, unless there's a mismatch in supported data types between [!INCLUDE[prod_short](../developer/includes/prod_short.md)] and [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. For data types that are supported, the column properties in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] are set based on the properties in [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

The rest of this section describes supported and unsupported data types. For more information about columns in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], see [Columns overview](/powerapps/maker/common-data-service/fields-overview).

| Data type in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] | Modeled data type in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] |
|-------------------------------------|------------------------------------------|
| Real                                | Decimal<br><br>For information about the possible mismatch, see the next table.</p> |
| Long                                | Decimal, where the precision equals 0 (zero) |
| Int                                 | Integer |
| String (non-memo), String (memo)    | String – single line of text, String – multiple lines of text |
| UtcDateTime                         | DateTime (DateTimeFormat.DateAndTime, DateTimeBehavior.TimeZoneIndependent)<br><br>An empty date (January 1, 1900) in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] is surfaced as a null value in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. |
| Date                                | DateTime - (DateTimeFormat.DateOnly, DateTimeBehavior.TimeZoneIndependent)<br><br>An empty date (January 1, 1900) in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] is surfaced as an empty value in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. |
| Enum                                | Picklist<br><br>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] enumerations (enums) are generated as global OptionSets in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. Matching between the systems is done by using the **External Name** property of values. Enum integer values in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] aren't guaranteed to be stable between the systems. Therefore, you shouldn't rely on them, especially for extensible enums in [!INCLUDE[prod_short](../developer/includes/prod_short.md)], because these enums don't have a stable ID either. OptionSet metadata is updated when a table that uses the OptionSet is updated.| 

Fields of the *real* and *long* data types in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] are modeled as the *decimal* data type in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. Because of the mismatch in precision and scale between the two data types, the following behavior must be considered.

| Use case                                     | Resulting behavior |
|----------------------------------------------|--------------------|
| [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] has higher precision.    | This use case should never occur unless the metadata is out of sync. |
| [!INCLUDE[prod_short](../developer/includes/prod_short.md)] has higher precision. | During a read operation, the value is rounded to the closest precision value in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. If the value is edited in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], it's rounded to the closest precision value in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. During a write operation, the value that is specified in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] is written, because [!INCLUDE[prod_short](../developer/includes/prod_short.md)] supports higher precision. |
| [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] has higher scale.        | Not applicable. |
| [!INCLUDE[prod_short](../developer/includes/prod_short.md)] has higher scale.     | [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] shows the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] value, even if it exceeds 100 billion. However, there will be a loss of precision. For example, 987,654,100,000,000,000 is shown in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] as "987,654,099,999,999,900". If the value of this column is edited in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] validation throws an error that the value exceeds the maximum value before that value is sent to [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. |

The following data types in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] aren't supported in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. Fields of these data types in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables won't be made available in the corresponding virtual tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. If fields of these data types are used as parameters in Open Data Protocol (OData) actions, those actions won't be available for use in the corresponding virtual tables. For more information about OData actions, see the [OData actions](powerplat-entity-modeling.md#odata-actions) section later in this article.


## Table key - primary key

In [!INCLUDE[prod_short](../developer/includes/prod_short.md)], tables use the SystemId (GUID) as the primary key, which uniquely identifies a record in a [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. In [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], the SystemId exposed by the table is used as the primary key.

## Primary column/field

In [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], each table must have a primary column. This column must be a single column of the string type. The primary column is used in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] in the following scenarios:

- The default views that are created for a table include the primary column.
- The quick view form for a table includes the primary column.
- A lookup to another table is added to a page and shows the data from the primary column.

The primary field for a virtual table for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] is designed to use **displayname** field on table if present. If this field isn't present the first string field is chosen as the primary field.

## Relations

> [!IMPORTANT]  
> A write transaction that spans a virtual table and a native table is not supported. Using this form of transaction is not recommended, as there is no way to ensure consistency.

Relations in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables are modeled as one-to-many (1:n) or many-to-one (n:1) relations. These relations are modeled as relationships in the virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. Many-to-many (n:n) relations aren't supported in [!INCLUDE[prod_short](../developer/includes/prod_short.md)].

For example, in [!INCLUDE[prod_short](../developer/includes/prod_short.md)], if table A has a foreign key to table B, this relation will be modeled as an n:1 relationship in virtual table A in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The schema name of this relationship in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] uses the naming convention **dyn365bc\_\<source table name\>\_\<target_table name\>**. This naming convention has a maximum string length of 120 characters. Any relation where the schema name will produce a name that exceeds 120 characters won't be generated in the virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. It's required that the foreign key is a SystemId (GUID). If the foreign key is of a different type, then the relation won't be generated.

The external name of this relationship uses the naming convention **\<relation name\>**. The external name is used to determine the relation in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] when the query that is sent to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] is built.

When a relationship is generated for a virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], a new column of the lookup type is also added to the source table. In the preceding example, when the relationship is created, a new lookup column that uses the naming convention **dyn365bc\_\<target\_table\>\_id** is added to source table A. Because there can be several relations in a table in [!INCLUDE[prod_short](../developer/includes/prod_short.md)], the same number of lookup fields (one per related table) will be created in the source virtual table. When this lookup field is added to a page or a view, it will show the primary field value from the related table.

A relationship in the virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] will be generated only if the related table in the relation already exists as a virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. In the preceding example, if table B doesn't exist as a virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], the relation to table B won't be created in table A when table A is generated as a virtual table. This relation will be added to table A only when table B is generated as a virtual table. Therefore, when a virtual table is generated for [!INCLUDE[prod_short](../developer/includes/prod_short.md)], validations are done to ensure that only relationships that are complete and functional are generated in the virtual table.

In summary, a relationship to another [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual table might not exist in the virtual table for either of the following reasons:

- The [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table that is participating in the relationship doesn't exist as a virtual table.
- The foreign key isn't SystemId (GUID).
- The length of the name of the relationship exceeds 120 characters.

> [!NOTE]  
> If an error is encountered when any part of a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual table is generated in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], the virtual table will not be created at all. If relationships do not exist for either of the preceding reasons, the situation is not considered an error.

### Native table–to–native table relationships

Native table–to–native table relationships are the standard [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] functionality, where relationships are resolved by using the GUID of the related table. This GUID is the table key. The GUID identifies the unique table record in the related table.

### Virtual table–to–virtual table relationships

The relationships between two [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables are driven by the relation metadata in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables. As explained earlier, these relations are generated as relationships in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] when the virtual table is generated. Just like the behavior of native tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], these relationships use the GUID to identify the unique record of the table in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. Semantically, the GUID on the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual table behaves like the GUID on the native [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] table. For information about the implementation of the GUID in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual tables, see the [table key/primary key](powerplat-entity-modeling.md#table-key---primary-key) section earlier in this article.

In the preceding example, the GUID of the related table is the table key of table B and will be used to build queries to identify a record in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. The relation that table A has to table B will be used.

Therefore, in effect, the table name is the only information that is used in a relation that comes from [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. The table name gives access to the primary field in the related table, so that it can be shown in the lookup. It also gives access to the GUID of the related table, so that it can be used in other queries, as explained earlier.

### Virtual table–to–native table relationship

Consider an example where you want to show sales orders from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] for Account A in Dataverse. A foreign key relation is needed between the native table **Account** and the virtual table **dyn365bc_salesorder_v2_0**. Once the relation is established, a virtual table can be used on pages, like other related tables. To set up a virtual table to native table relation, follow these steps:

1. Go to the native table that you want to create a relation to and add a **Key**. Choose the column(s) needed for the relation. 1 to 3 columns can be used in the native to virtual table relation.
2. Add a new record to the **Business Central Table Relation** table.  
    1. On the **General** tab, provide **Relation Name**, **Native Table**, and **Native Table Key** which is the name of the key specified in step 1, and the **Virtual Table** name. For **Native Table** and **Virtual Table**, make sure to use the table name, and not the table display name.
    2. On the **Mapping** tab, provide column mapping between the native table and the virtual table column(s). All columns included in the table key (defined in step 1) must be mapped.  
3. Press **Save**. Validation will be performed on save.

To follow the example from above, where a relation between the native table **Account** and the virtual table **dyn365bc_salesorder_v2_0** is needed:

1. Create a key on the **Account** table. Choose **Account Number**. Name is 'prefix_**accountkey**'.
2. Make sure that **dyn365bc_salesorder_v2_0** is generated.
3. Add a new record to the **Business Central Table Relation** table.
    - On the **General** tab set the following:
        - **Relation Name** to **dyn365bc_account2salesorder**
        - **Native Table** to **account**
        - **Native Table Key** to **prefix_accountkey**
        - **Virtual Table** to **dyn365bc_salesorder_v2_0**
    - On the **Mappings** tab set first row as follows:
        - **Native columns** to **accountnumber**
        - **Virtual columns** to **dyn365bc_customernumber**
4. Save the **Business Central Table Relation** record.
5. Open the main page of **Account**. Add a sub grid and choose the **Sales Orders (accountid)** relation.
6. Save and publish.

**Account** now contains the relation, and **Sales Orders** are shown on the main page if any sales orders exist for the account.

#### Synchronizing master data

To create native-to-virtual table relations a shared key is needed in order to establish a foreign key relationship. In the Account and Sales Order scenario, the Account Number in the Account table must be identical to the Customer Number in the [!INCLUDE[prod_short](../includes/prod_short.md)] Customer table.

To set up synchronization between Microsoft Dataverse and [!INCLUDE[prod_short](../includes/prod_short.md)], follow the [guide](/dynamics365/business-central/admin-how-to-set-up-a-dynamics-crm-connection). To get started use the **Dataverse Connection Setup** assisted setup guide in [!INCLUDE[prod_short](../includes/prod_short.md)].

A customization to the synchronization is needed, because the customer number isn't synced with Dataverse by default. The code in the example below adds the field mapping to the synchronization. In this snippet, the synchronization is uni-directional. In this case, [!INCLUDE[prod_short](../includes/prod_short.md)] will be the main, pushing account number to Microsoft Dataverse.

```al
codeunit 50100 SyncAdditionalFields
{
    [EventSubscriber(ObjectType::Codeunit, Codeunit::"CDS Setup Defaults", 'OnAfterResetCustomerAccountMapping', '', true, true)]
    local procedure HandleOnAfterResetCustomerAccountMapping(IntegrationTableMappingName: Code[20])
    var
        IntegrationFieldMapping: Record "Integration Field Mapping";
        Customer: Record Customer;
        CRMAccount: Record "CRM Account";
    begin
        InsertIntegrationFieldMapping(
          IntegrationTableMappingName,
          Customer.FieldNo("No."),
          CRMAccount.FieldNo(AccountNumber),
          IntegrationFieldMapping.Direction::ToIntegrationTable,
          '', false, false);
    end;

    procedure InsertIntegrationFieldMapping(IntegrationTableMappingName: Code[20]; TableFieldNo: Integer; IntegrationTableFieldNo: Integer; SynchDirection: Option; ConstValue: Text; ValidateField: Boolean; ValidateIntegrationTableField: Boolean)
    var
        IntegrationFieldMapping: Record "Integration Field Mapping";
    begin
        IntegrationFieldMapping.CreateRecord(IntegrationTableMappingName, TableFieldNo, IntegrationTableFieldNo, SynchDirection,
            ConstValue, ValidateField, ValidateIntegrationTableField);
    end;
}
```

For more information, see [Customizing an Integration with Microsoft Dataverse](../administration/administration-custom-cds-integration.md).

### Native table–to–virtual table relationships

Native table–to–virtual table relationships work much like virtual table–to–native table relationships. Once a relation has been set up between the native table and the virtual table, sub grids or Quick Views can be added, showing related native table information.

## Enums

Enums in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] are modeled as OptionSets in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. When a virtual table for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] is generated, the required enums are generated as OptionSets. If an OptionSet already exists, it is used instead.

## Company

If [!INCLUDE[prod_short](../developer/includes/prod_short.md)] has multiple companies, the default company must be selected. This can be done either on a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] virtual table configuration page or on a User table page.

Furthermore, every virtual table for a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table have a relationship to the cdm\_company table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The cdm\_company table is a native table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] and is part of the Dynamics365Company solution. As always, when a relationship is created, a lookup column is also created in the virtual table for the related table (cdm\_company in this case). This lookup column is named **Company**, and it must be used to provide an optimal user experience where users can select a value in a list or go to the details of the related record. A column that is named **Company Code** is also added in the virtual table. This column must be used in programming. A Virtual Table can only interact with one Company at a time. Connection to other Companies can be made in either the connection setup page or overridden on the individual user.   
 
## OData actions

OData actions in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables are made available as custom actions in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. For more information about custom actions and what they enable in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)], see [Custom actions](/powerapps/developer/common-data-service/custom-actions).

OData actions generated for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] have only one parameter, which is the table. There's no output parameter.

## Labels and localization

Labels that are defined on metadata, such as table names and field names in [!INCLUDE[prod_short](../developer/includes/prod_short.md)], are retrieved when virtual tables are generated in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. The labels are retrieved using an API on [!INCLUDE[prod_short](../developer/includes/prod_short.md)] called **entityDefinitions**. This API is available on every API route, and will serve translations and other table metadata, not suited for OData `$metadata`. But with both the entityDefinition and `$metadata` [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] has all it needs to generate localized virtual tables.  

Any runtime labels are returned in the language of the current user context. In other words, they're returned in the language that is specified on that user's UserInfo record in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. This behavior also applies to error messages.

## Error handling

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] create, read, update, and delete (CRUD) business logic on tables and backing tables is run when it's called through the virtual table in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)]. If any exception is thrown on the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] side, the last message in the error log is returned to [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] and is thrown as an InvalidPluginExecutionException exception that contains the message from [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. Because the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] code runs in the context of the user, the language of the error message is based on the language that is specified on the UserInfo record in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. If any messages that are written to the info login [!INCLUDE[prod_short](../developer/includes/prod_short.md)] don't result in an exception, they aren't shown in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)].

## Calculated/unmapped fields

Calculated and unmapped fields in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tables are also available in the corresponding virtual tables in [!INCLUDE[cds_long_md](../includes/cds_long_md.md)].

## See Also

[Overview - Integrating Business Central with Microsoft Dataverse](../developer/dataverse-integration-overview.md)  
[Microsoft Power Platform Integration with Business Central](powerplat-overview.md)  
[Application Lifecycle Management for Solutions that use Virtual tables](powerplat-app-lifecycle-management.md)  
[Business Central and [!INCLUDE[cds_long_md](../includes/cds_long_md.md)] Admin Reference](powerplat-admin-reference.md)  
[FAQ](powerplat-faq.md)
