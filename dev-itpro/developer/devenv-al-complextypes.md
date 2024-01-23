---
title: AL complex types
description: With AL complex types, you can return most types from procedures in AL for Business Central
ms.custom: na
ms.date: 09/29/2023
ms.reviewer: solsen
ms.topic: conceptual
author: esbenk
ms.collection: get-started
---

# AL complex types

[!INCLUDE[2021_releasewave1.md](../includes/2021_releasewave1.md)]

With the latest version of [!INCLUDE[prod_short](includes/prod_short.md)], it's possible to return most types from procedures - both user-defined types and most built-in types.

The method in the example below, will take a name, and return the first customer record that matches the name. The signature specifies the return type at the end of the procedure declaration, and the procedure exits by returning the found customer record.

```al
/// <summary> 
/// Get the first customer with name starting with <paramref name="Name"/> 
/// </summary> 
/// <param name="Name">Name filter</param> 
/// <returns>First customer</returns> 

procedure GetCustomerByName(Name: Text): Record Customer
var
    Customer: Record Customer;
begin
    Customer.SetFilter(Name, '@' + Name + '*');
    Customer.FindFirst();
    exit(Customer);
end;
```
 
It's also possible to use a named return value. Internally, the exit-statement as seen in the example above causes an assignment to an allocated return value. The assignment will have a small performance cost based on the type. Since the record type is treated as a value-type, it's better.  

```al
procedure GetCustomerByName(Name: Text) Customer: Record Customer
begin 
   Customer.SetFilter(Name, '@' + Name + '*'); 
   Customer.FindFirst(); 
end; 
```
 
The method `GetCustomerByName()` returns a Customer record. It can be used as you would expect in the following example.

```al
// Get the first customer with name starting with 'spo' 

Customer := GetCustomerByName('spo'); 
```

The returned value doesn't have to be used in an assignment statement. It can be used as part of an expression like in the following example.

```al
// Use the returned value as an expression. 

DoSomethingWithSales(GetCustomerByName('spo').GetSalesLCY()); 
```
 
It doesn't only work for user-defined types like records, codeunits, etc., but also for built-in types. For example, when using the [HttpClient Data Type](methods-auto/httpclient/httpclient-data-type.md), it's possible to write code as illustrated below.

```al

/// <summary> 
/// Returns a bing-ready HttpClient 
/// </summary> 
/// <returns>Bing HttpClient</returns> 
procedure GetBingClient() Result: HttpClient
begin
    Result.SetBaseAddress('https://www.bing.com');
end;

/// <summary> 
/// Get the response from a request to bing. 
/// </summary> 
/// <returns>The response message</returns> 

procedure GetBingResponse() Response: HttpResponseMessage
begin
    GetBingClient().Get('', Response)
end;

/// <summary> 
/// Get the response from www.bing.com as an html-string.  
/// </summary> 
/// <returns>string with html</returns> 
procedure GetBingHtml() Result: Text
begin
    GetBingResponse().Content().ReadAs(Result);
end;
```

## See Also

[Programming in AL](devenv-programming-in-al.md)  
[AL Simple Statements](devenv-al-simple-statements.md)  
[Directives in AL](directives/devenv-directives-in-al.md)  
[AL Essential Methods](devenv-essential-al-methods.md)  
[HttpClient Data Type](methods-auto/httpclient/httpclient-data-type.md)
