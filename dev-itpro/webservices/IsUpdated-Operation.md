---
title: "IsUpdated operation"
ms.date: 12/22/2023
ms.topic: article
description: Discover Dynamics 365 Business Central's IsUpdated Operation - check object updates, manage concurrency, and prevent record change failures.
---
# IsUpdated operation
Checks if an object has been updated since the key was obtained. This operation returns **true** if the object has been updated by any user; otherwise, **false**. Concurrency management prevents a record being changed if it has been subsequently updated. This check proactively prevents that failure.  
  
## Method signature  
 `bool IsUpdated(string key)`  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|*key*|Type: String<br /><br /> The bookmark of the record, including both primary key and concurrency information.|  
  
## Results  
  
|Result name|Description|  
|-----------------|-----------------|  
|IsUpdated\_Result|Type: Boolean<br /><br /> Returns **true** if and only if another user has modified the record.|  
  
## Faults  
  
|SOAP fault message|Description|  
|------------------------|-----------------|  
|\[*record name*\] \[*field*\] \[*value*\] doesn't exist.|Indicates that the record has been deleted by another user or process after it has been retrieved for this operation.|  
  
## Usage example  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace ConsoleApplication  
{  
    // Imports newly generated web service proxy.  
    using WebService;   
  
    class Program  
    {  
       static void Main(string[] args)  
           {  
              // Creates instance of service and sets credentials.  
              Customer_Service service = new Customer_Service();  
              service.UseDefaultCredentials = true;  
  
              Customer cust = new Customer();  
              cust.Name = "Customer Name";  
              service.Create(ref cust);  
              cust = service.Read(cust.No);  
              if (!service.IsUpdated(cust.Key))  
           {  
              // Add code here to modify record.  
           }  
        }  
    }  
}  
```  
  
## Related information  
 [Basic Page Operations](Basic-Page-Operations.md)
