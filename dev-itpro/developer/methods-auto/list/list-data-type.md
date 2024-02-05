---
title: "List Data Type"
description: "Represents a strongly typed list of ordered objects that can be accessed by index."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# List Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents a strongly typed list of ordered objects that can be accessed by index. Contrary to the Array data type, a List is unbounded, such that its dimension does not need to be specified upon declaration.



## Instance methods
The following methods are available on instances of the List data type.

|Method name|Description|
|-----------|-----------|
|[Add(T)](list-add-method.md)|Adds a value to the end of the List.|
|[AddRange(T [, T,...])](list-addrange-t-t-method.md)|Adds the elements of the specified collection to the end of the list.|
|[AddRange(List of [T])](list-addrange-list[t]-method.md)|Adds the elements of the specified collection to the end of the list.|
|[Contains(T)](list-contains-method.md)|Determines whether an element is in the List.|
|[Count()](list-count-method.md)|Gets the number of elements contained in the List.|
|[Get(Integer, var T)](list-get-integer-t-method.md)|Gets the element at the specified index.|
|[Get(Integer)](list-get-integer-method.md)|Gets the element at the specified index. This method will raise an error if the index is outside the valid range.|
|[GetRange(Integer, Integer)](list-getrange-integer-integer-method.md)|Get a shallow copy of a range of elements in the source.|
|[GetRange(Integer, Integer, var List of [T])](list-getrange-integer-integer-list[t]-method.md)|Get a shallow copy of a range of elements in the source.|
|[IndexOf(T)](list-indexof-method.md)|Searches for the specified value and returns the one-based index of the first occurrence within the entire List.|
|[Insert(Integer, T)](list-insert-method.md)|Inserts an element into the List at the specified index.|
|[LastIndexOf(T)](list-lastindexof-method.md)|Searches for the specified value and returns the one-based index of the last occurrence within the entire List.|
|[Remove(T)](list-remove-method.md)|Removes the first occurrence of a specified value from the List.|
|[RemoveAt(Integer)](list-removeat-method.md)|Removes the element at the specified index of the List.|
|[RemoveRange(Integer, Integer)](list-removerange-method.md)|Removes a range of elements from the List.|
|[Reverse()](list-reverse-method.md)|Reverses the order of the elements in the entire List.|
|[Set(Integer, T)](list-set-integer-t-method.md)|Sets the element at the specified index.|
|[Set(Integer, T, var T)](list-set-integer-t-t-method.md)|Sets the element at the specified index.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

The List can only be used with simple types i.e. you can have a List of [Integer] but cannot have a List of [Blob]. Similarly, the List data type does not support holding instantiated records. For this purpose, use temporary tables.

Lists are 1-based indexed, that is, the indexing of a List begins with 1.

A List is a reference type, so assigning an instance of a list to another variable or passing as a method parameter by value (for example without var), creates a second variable that reads/writes the same list. *It does not create a new list*.

To create a new list that contains the same values as the original list, you can do the following to perform a *shallow copy*:

```al
trigger OnRun()
    var
        l1: List of [Integer];
        l2: List of [Integer];
    begin
        l2 := l1.GetRange(1, l1.Count);
    end;
```

A shallow copy does not copy the elements within the list, only the list itself, so if the elements within the list are reference types as well, for example a list of lists, they will still be the same lists as in the original list.

To perform a *deep copy*, meaning to copy reference types within reference types, you will need to apply the same approach to the elements of the list:

```al
trigger OnRun()
    var
        innerlist: List of [Integer];
        l1: List of [List of [Integer]];
        l2: List of [List of [Integer]];
    begin
        foreach innerlist in l1 do begin
            l2.Add(innerlist.GetRange(1, innerlist.Count));
        end;
    end;
```


> [!WARNING]  
> Previously in C/AL, one would have typically used an in-memory temporary table to create an unbounded "array" data structure, as shown in the code below. In AL you use the List Data Type instead.
> 
> ```al
> listRec.Value := ‘Some Value’;​
> listRec.Insert();​
> ```

## Example

In the following example, the variable `CustomerNames` is a list of Text values which represent customer names. The procedure `WorkWithListOfCustomers` displays how one would work with the List data type. The `Add` method is used to add the string `'John'` to the `CustomerNames` list. The `Contains` method is used to check whether the list contains the specified value, in this case, the string `'John'`. We continue by using the Message procedure to display a relevant message. 

```al
procedure WorkWithListOfCustomers();
var
    customerNames : List of [Text];
begin
    // Adding an element to the list
    customerNames.Add('John');

    // Checking if the list contains an element
    if customerNames.Contains('John') then
        Message('John is in the list')
    else 
        Message('John is not in the list')
end;

```  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Dictionary Data Type](../dictionary/dictionary-data-type.md)