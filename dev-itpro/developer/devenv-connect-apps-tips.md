---
title: "Tips for working with the APIs"
description: Provides some tips about working with Business Central API.
author: SusanneWindfeldPedersen
ms.author: solsen
ms.custom: bap-template
ms.date: 07/03/2023
ms.reviewer: na

ms.topic: conceptual
---

# Tips for working with APIs

## GET

+ Call (GET) the endpoint to list all the API
+ Call (GET) the endpoint with `$metadata` to list all metadata for the API

<!--
+ Call (GET) the endpoint with the `odata.track-changes` preference to obtain a [deltaLink](devenv-connect-apps-delta.md) to return the records that have changed in the data set since the last query
+ Call (GET) the endpoint with `$filter` to list all the records within the specified range by providing [Filters](devenv-connect-apps-filtering.md)
-->

+ Calling a resource API (GET) will return a list of all instances of the resource type
+ Each resource is uniquely identified through an ID, see the following example:  

    ```json
    {
        "@odata.context": "<endpoint>/$metadata#companies",
        "value": [
            {
                "id": "bb6d48b6-c7b2-4a38-9a93-ad5506407f12",
                "systemVersion": "18453",
                "name": "CRONUS USA, Inc.",
                "displayName": "CRONUS USA, Inc.",
                "businessProfileId": ""
            }
        ]
    }
    ```

+ The resource ID must be provided in the URL when trying to read or modify a resource or any of its children. The ID is provided in () after the API endpoint. For example, to GET the "CRONUS USA, Inc." company details, you must call `<endpoint>/companies(bb6d48b6-c7b2-4a38-9a93-ad5506407f12)/`
+ All resources live in the context of a parent company, which means that the company ID must be provided in the URL for all resource API calls. For example, to GET all customers in the "CRONUS USA, Inc." company, you must call `<endpoint>/companies(bb6d48b6-c7b2-4a38-9a93-ad5506407f12)/customers`

## <a name="AcceptLanguage"></a>Accept-Language HTTP header

By specifying `Accept-Language` in the request header, you can set a specific language for your web service response. It's recommended to use this setting, if your app is dependent on a web service response to be in a specific language. If `Accept-Language` is set, it will override default settings. This setting also controls the regional formatting settings, affecting behavior such as how date and time will be formatted.

One of the most common examples is showing error messages to the users in their language. To see which possible error messages to display, see [Error Codes](../api-reference/v2.0/dynamics-error-codes.md). Another common example is displaying reports in a specific language, see the example below for how to specify `Accept-Language`. The following example sets the language to always be `en-US`.

### Example

`GET businesscentralPrefix/companies({id})/salesInvoices({salesInvoiceId})/pdfDocument({salesInvoiceId})/content`

#### Request headers
|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Accept-Language|en-US|

#### Request body
Don't supply a request body for this method.

#### Response
If successful, this method returns a `200 OK` response code and a report PDF file in the response body.

## <a name="batch"></a>OData transactional $batch requests

> **APPLIES TO:** Business Central 2020 release wave 2 (version 17.1) and later

It's possible to specify that all inner requests in a certain OData $batch request are processed in a transactional way. If one of the inner requests fails after another request (or requests) has committed changes, all changes within a batch will be reverted as if the batch request never happened. Transactional $batch requests are useful in scenarios where a single business operation spans multiple requests, because they prevent adverse effects if parts of the operation fail. Also, they can improve performance by reducing the number of requests the client needs to do when errors occur.

To enable transactional batch behavior, include the `Isolation: snapshot` header with the $batch request.

For more information, see [Using OData Transactional $batch Requests](../webservices/use-odata-batch.md)

## <a name="DataAccessIntent"></a>Specifying Data Access Intent for GET requests

By specifying HTTP request header `Data-Access-Intent`, it's possible to override data access intent of the API page or query that has been defined with [DataAccessIntent property](properties/devenv-dataaccessintent-property.md). 

[!INCLUDE[database_access_intent_note](../includes/include-database-access-intent-note.md)]

### Possible header values

|Value|Description|
|-----------|---------------------------------------|
|**ReadOnly**|Intent to access records, but not to modify them. The page or query reads data from a replica of the database (if available), reducing the load on the primary database, but prevents modifications to the database records.|
|**ReadWrite**|Intent to access and modify records.|

When request header is specified, the value of the DataAccessIntent property defined on the object, if any, is ignored. Overrides that are specified on the page **9880 Database Access Intent List**  take higher precedence than the value in the request header.

Modification requests (like POST, PUT, or DELETE) only support `ReadWrite` as a value for data access intent. Trying to specify `Data-Access-Intent: ReadOnly` for such requests will result in an error.

### Example

`GET businesscentralPrefix/companies({id})/salesInvoices({salesInvoiceId})/pdfDocument({salesInvoiceId})/content`

#### Request headers
|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Data-Access-Intent|ReadOnly|

#### Request body
Don't supply a request body for this method.

#### Response
If successful, this method returns a `200 OK` response code and a report PDF file in the response body.

## See Also
<!-- [Using Deltas With APIs](devenv-connect-apps-delta.md)-->  
[Using Filtering With APIs](devenv-connect-apps-filtering.md)  
[API performance](../webservices/web-service-performance.md)   
[Performance Articles For Developers](../performance/performance-developer.md)  
[DataAccessIntent property](properties/devenv-dataaccessintent-property.md)
