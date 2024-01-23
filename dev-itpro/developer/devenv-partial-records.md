---
title: Using partial records
description: Describes the partial records capability in Business Central.
ms.author: jswymer
ms.custom: bap-template
ms.date: 09/27/2023
ms.reviewer: na

ms.topic: conceptual
author: jswymer
---
# Using partial records

[!INCLUDE[d365fin_long_md](../includes/2020_releasewave2.md)]

The partial records capability in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] allows for loading a subset of normal table fields when accessing a SQL based data source. Using partial records improves performance of objects like reports and OData pages - objects whose source code loops through records. It's particularly beneficial when table extensions are used in the application.  

Accessing a data source from AL code is typically done by using the record's methods [Get, Find, Next](devenv-get-find-and-next-methods.md), and so on. Without using partial records, the runtime loads all normal fields when accessing the data source. Using the partial records API, you can now select a set of fields and only load them.

## API Overview

To accommodate partial record loading, the following methods are available on both the RecordRef and Record data type in AL. These methods operate on the record instance that they're called on, changing the set of fields to load until otherwise altered. The methods are divided into two groups: methods that pertain to subsequent loads and methods that pertain to the currently loaded record.

**Subsequent load methods**

|Method|Description|See more|
|------|-----------|--------|
|SetLoadFields|Specifies a set of fields to be initially loaded when the record is retrieved from its data source. A call to this method will overwrite any fields that were previously set to load.|[Record.SetLoadFields](methods-auto/record/record-setloadfields-method.md)<br /><br />[RecordRef.SetLoadFields](methods-auto/recordref/recordref-setloadfields-method.md)|
|SetBaseLoadFields|Adds all fields from the base table to be initially loaded when the record is retrieved from its data source. A call to this method will overwrite any fields that were previously set to load. |[Record.SetBaseLoadFields](methods-auto/record/record-setbaseloadfields-method.md)<br /><br />**Note:** The SetBaseLoadFields method was added in Business Central 2023 release wave 2.|
|AddLoadFields|Adds fields to the current set of fields to be initially loaded when the record is retrieved from its data source. Subsequent calls to this method won't overwrite fields that were previously selected for loading.|[Record.AddLoadFields](methods-auto/record/record-addloadfields-method.md)<br /><br />[RecordRef.AddLoadFields](methods-auto/recordref/recordref-addloadfields-method.md)|

**Current load methods**

|Method|Description|See more|
|------|-----------|--------|
|AreFieldsLoaded|Checks whether the specified fields are all initially loaded.|[Record.AreFieldsLoaded](methods-auto/record/record-arefieldsloaded-method.md)<br /><br />[RecordRef.AreFieldsLoaded](methods-auto/recordref/recordref-arefieldsloaded-method.md)|
|LoadFields|Accesses the table's corresponding data source to load the specified fields.|[Record.LoadFields](methods-auto/record/record-loadfields-method.md)<br /><br />[RecordRef.LoadFields](methods-auto/recordref/recordref-loadfields-method.md)|

A record instance that has been previously loaded with fields can be reset to a non-partial load either by calling [Record.SetLoadFields](methods-auto/record/record-setloadfields-method.md) without any parameters, or by calling [Reset](methods-auto/record/record-reset-method.md). After being reset, subsequent loads will behave as if SetLoadFields hadn't previously been called on the record instance.

## Example

The following code shows a way to load only a single field from the **Item** table for computing the arithmetic mean.

```AL
procedure ComputeArithmeticMean(): Decimal;
var
    Item: Record Item;
    SumTotal: Decimal;
    Counter: Integer;
begin
    Item.SetLoadFields(Item."Standard Cost");
    if Item.FindSet() then begin
        repeat
            SumTotal += Item."Standard Cost";
            Counter += 1;
        until Item.Next() = 0;
        exit(SumTotal / Counter);
    end;
end
```

Notice that the call to [SetLoadFields](methods-auto/record/record-setloadfields-method.md) occurs before the data fetching operations. This call determines which fields are needed for the FindSet call. You use the same pattern for [AddLoadFields](methods-auto/record/record-addloadfields-method.md) calls.

## Usage guidelines

This feature gives you the ability to limit the fields that load for a record to only those fields that are necessary. In general, loading fewer fields will make operations faster. But the most significant performance gains can be seen with table extensions - by not loading unnecessary fields in table extensions. Table extensions that don't have any fields for loading won't be part of the data join, which saves time.

<!--
The main goal of the feature is to provide the ability to limit the number of fields that are necessary to load. In general, loading fewer fields will make operations more performant. But the most significant performance gain  gain more importantly, limiting the set of fields needed to not load any fields from other table extensions is where the majority gain will be seen. Some of the performance issues that customers have observed with many table extensions on a base table will go away with this optimization.
-->

> [!TIP]
> Testing on the previous example code showed that the execution time for loading only the "Standard Cost" field was nine times faster than loading all normal fields. Your performance numbers will vary depending on the machine and the setup with the SQL database.

For performance reasons, it's not recommended to use partial records on a record that will do inserts, deletes, renames, field transfers, or copies to temporary records. All these operations require that all fields on the record are loaded, so the platform will emit a JIT load if they're not already loaded. A JIT load requires to access the data source again, this cost is larger than the gains of loading fewer fields. For this reason, the feature is especially advantageous in reading-based scenarios.

## <a name="jit"></a>Just-in-time (JIT) loading

When a record is loaded as a partial record, the obvious question is: What happens when accessing a field that hasn't been selected for loading? The answer is JIT loading. The platform, in such a case, does an implicit [Get](methods-auto/record/record-get-method.md) on the record and loads out the missing field.

When JIT loading occurs, another access to the data source is required. These operations tend to be fast because they're Get calls. Get calls can often be served by the server's data cache or can be resolved as a clustered index operation on the database.

A JIT load may fail for multiple reasons, like:

- The record has been modified between the original load and the subsequent JIT load.
- The record has been deleted between the original load and the subsequent JIT load.
- The record has been renamed between the original load and the subsequent JIT load.

## Iterating over records

When iterating over records in the database, an enumerator is created based on selected fields. Then, a row is fetched when [Next](methods-auto/record/record-next-method.md) is called. This behavior is an optimization that allows for large parts of the operation to be done only once.

Certain operations will invalidate the enumerator and force the creation of a new one, which adds some overhead. As long as the enumerator isn't invalidated too frequently, this model is an effective optimization. When accessing fields that aren't loaded, the platform does a JIT load, followed by an update of the enumerator. This process eliminates the need to trigger a JIT load on subsequent iterations.

When passing a record by value, without using a [var parameter](devenv-al-methods.md#Parameters), a new copy of the record is created. The original record and its copy don't share filters, fields selected for load, and so on. So accessing an unloaded field will trigger a JIT load. But it won't update the enumerator, which means future iterations will also require JIT load.

There are a few options to remedy this situation:

- Pass the record reference using var parameter allows for updating of enumerator.
- Call [AddLoadFields(fieldnames)](methods-auto/record/record-addloadfields-method.md) on the original record before passing by value.
- Before calling [Get, Find, Next](devenv-get-find-and-next-methods.md), and so on, use the [SetLoadFields(fieldnames)](methods-auto/record/record-setloadfields-method.md) to set all fields needed for load.

## Preventing inconsistent read and JIT loading errors

Seeing the error **Inconsistent read of field(s):…** means that a read record has changed in the database sometime between the initial load and a subsequent load. When a subsequent load (JIT load) occurs, extra fields are loaded, and all previously loaded fields are checked for consistency to verify that they haven't changed. For example, suppose the **Amount** field in a table had the value of 42 on the initial load. But at sometime before the subsequent load, another user changed the value in the database to 9001.

You could categorize this error as a *read skew* consistency error. The platform, in this case, doesn't know whether the previously executed code made decisions based on the value being 42. So, instead of potentially ending up with inconsistent data, the platform invokes error handling by throwing an error.

Another error related to the **Inconsistent read of field(s):...** error is the **JIT loading of field(s): ... failed ...** error. This error is a more generic error that can happen for multiple reasons during a JIT load. But the most frequent cause is that the record has been deleted in the database. It's similar the **Another User has Modified the record** error you'll get when a record is modified, but the platform detects newer data in the database.
All these errors are the result of a race condition, meaning they depend on whether other users are also interacting with the same data concurrently.

To prevent these errors, avoid JIT loads if you can. If there are no subsequent loads (JIT), the previously described race condition will never occur. To avoid JIT loads, follow these guidelines:

- On the first load, select all and only the necessary fields by using [SetLoadFields](methods-auto/record/record-setloadfields-method.md) calls or subsequent [AddLoadFields](methods-auto/record/record-addloadfields-method.md) calls.
- When the platform implicitly uses partial records, add the extra fields by calling AddLoadFields from the [OnPreDataItem trigger](triggers-auto/reportdataitem/devenv-onpredataitem-reportdataitem-trigger.md) on reports or from the [OnOpenPage trigger](triggers-auto/page/devenv-onopenpage-page-trigger.md) on OData pages.

For more information, see [Reports and OData pages](#reports). Optionally, you can add the fields as a data column on reports or fields on OData pages.

## Partial records applied by platform

The platform will automatically apply partial records to certain types of AL objects based on their metadata. This is currently done in four places: reports, OData pages, list and listpart pages, and table relation-based lookups.

### Reports

When loading data for a report, the fields that are referenced in data columns on a data item will automatically be selected for load. This includes references in nested data items. 

Other fields aren't selected for load, even if they may be used in triggers. However, you can add extra fields the following ways:

- Add the field as a column in the data set.
- Add the field to the set of fields to load via the [AddLoadFields](methods-auto/record/record-addloadfields-method.md) method on the [OnPreDataItem](triggers-auto/reportdataitem/devenv-onpredataitem-reportdataitem-trigger.md) trigger.

    The following example code snippet illustrates how to use the AddLoadFields method on a report's OnPreDataItem trigger to add a field for loading: 
    
    ```AL
    trigger OnPreDataItem() 
    begin 
        CurrencyDataItem.AddLoadFields(CurrencyDataItem."ISO Numeric Code"); 
    end; 
    
    trigger OnAfterGetRecord() 
    begin 
        if (CurrencyDataItem."ISO Numeric Code" <> 'DKK') then begin 
            CurrReport.Skip(); 
        end; 
    end; 
    ```

### OData pages

For pages opened by OData service calls, the page's metadata is used to define which fields to show. In this case, the fields referenced in the page’s layout are loaded as a minimum. More fields may be required, for example, to enable subpage linking.

Like with reports, other fields aren't selected for load, even if they may be used in triggers. But you can add extra fields the following ways:

- Add the field to the page layout.
- Add the field to the set of fields to be loaded via the [AddLoadFields](methods-auto/record/record-addloadfields-method.md) method on the [OnFindRecord](triggers-auto/page/devenv-onfindrecord-page-trigger.md) trigger.  

### List and ListPart pages 

Partial records are automatically applied based on the page’s metadata for List and ListPart page types that are opened in the web client. As with OData pages, the page's definition is used to select which fields to load. More fields may be required, for example, to enable subpage linking. 

> [!NOTE]
> OnFindRecord and OnNextRecord triggers conflict with partial record feature with List and ListPart pages, so if these triggers are defined in the metadata, the partial record feature won't be applied.

### Table relation-based lookups

Lookups that are based on table relations and not explicit lookup pages will automatically generate the set of fields to load by using the same logic as for determining which fields to shown. Because these lookups don't have a defined page, it isn’t possible, or necessary, to overrule the set of fields.

## See Also

[FAQ for Partial Records](devenv-partial-records-faq.md)  
[Performance Articles For Developers](../performance/performance-developer.md)  
[Get, Find, and Next Methods](devenv-get-find-and-next-methods.md)  
[Configuring Business Central Server](../administration/configure-server-instance.md)  
