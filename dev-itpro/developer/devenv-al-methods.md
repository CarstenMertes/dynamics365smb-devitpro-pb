---
title: "Working with AL methods"
description: "Methods also known as procedures are a fundamental programming element in AL for Business Central."
ms.custom: na
ms.date: 11/16/2021
ms.reviewer: na
ms.topic: conceptual
author: SusanneWindfeldPedersen
ms.collection: get-started
---

# AL methods

[!INCLUDE [getstarted-contributions](includes/getstarted-contributions.md)]

Like other languages, AL methods are a fundamental programming element. A method, also known as a procedure, is a named group of statements that perform an operation or task. Depending on the scope, methods can be run, or *called*, from the same object in which they are declared or from other parts of the application.  

There are two types of methods: system methods (built-in) and user-defined (custom) methods.

- Built-in methods are part of the platform. Built-in methods can be used for different purposes, such as string handling, text formatting, database handling, and so on. For information about the available built-in methods, see [AL method Reference](methods-auto/library.md) and [Essential AL methods](devenv-essential-al-methods.md). For information about method scope, see [Scope Attribute](attributes/devenv-scope-attribute.md).

- Custom methods are specialized methods for your application to bind the objects, such as tables, pages, and code units, together to form a unified whole. You can create special methods for use anywhere in the database.

> [!TIP]  
> If you already know the name of, for example, a data type, method, property, or trigger, use the **Filter by title** field in the upper left corner, above the table of contents to find the topic faster. Otherwise, you can scan the table of contents to find it.

## Declaring methods

The method declaration defines the method and has the following syntax:

```AL
[Attributes(arguments list)]
local procedure <method_name>(parameter list) <return_value_name> : <data_type>[<length>]
```

### Snippet support

Typing the shortcut `tprocedure` will create the basic structure for a method when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.

### Attributes (optional)

An attribute is a modifier on a method declaration that specifies information that controls the method's use and behavior. Adding an attribute on a method declaration is also known as *decorating* a method. For example, decorating a method with the Integration attribute sets the method to be an event publisher. An attribute can have one or more arguments that set properties for the method instance.

Attributes are placed before the method. For information about the available attributes, see [Method Attributes](attributes/devenv-method-attributes.md).

### Local and global scope

A method can be a *local* method or *global* method. A local method can only be accessed or called from inside the object in which it is declared. A global method can be called from inside the object in which it is declared and from other objects.

To declare a local method, start the declaration with `local`: 

```AL
local procedure Mymethod();
```

To declare a global method, *omit* `local`:

```AL
 procedure Mymethod();
```

### Parameters (optional)

A parameter is one or more variables or expressions that are sent to the method through the method call. The parameter provides information to the method, and the method can modify that information. In the method declaration, you place the parameters in parentheses `()`. If there is more than one parameter, the parameters are separated by semicolons. A parameter is defined by a data type. Some data types, such as `Record`, require an additional subtype. 

For example, the following method declaration includes two parameters: `MyCustomer`and `MyDimension`:

```AL
 procedure MyMethod(MyCustomer : Record Customer; var MyDimension : List of [Boolean])
```

This example also illustrates how parameters can be *passed by value* or *passed by reference*. The `MyCustomer` parameter is passed by value, and the `MyDimension` parameter is passed by reference in the example above. For more information, see the section [Parameters](devenv-al-methods.md#Parameters) below.

### Return values (optional)

A method can return data that can be then coded against. A return value is defined by a name (optional), data type, and optional length depending on the data type. 

For example, if the return value is a Text DataType, the text might have a length of 50.

```AL
    procedure MyMethod() ReturnValue: Text[50]
        var result : Text[50];
    begin
        // do something important where result is calculated
        ReturnValue := result;
    end;
```

## <a name="Callmethod"></a>Calling methods

You can run, or call, a built-in or a custom method by using its name in a method call statement. When a method is called the current application sequence is suspended and the code on the method is run. When the method code is completed, the application code sequence returns to where the method was called from. How the method is called determines what happens when it returns.

A method can be used as part of an expression. For example, the following code uses a
method named `CalculatePrice` as an expression:

```AL
TotalCost := Quantity * CalculatePrice;
```

In this case, the `CalculatePrice` method must return a value that is used in evaluating the expression. This return value is then multiplied by the Quantity variable and that result is assigned to the TotalCost variable.

A method can also be run by using a method call statement. This statement only calls the method and does not return any value. The following is an example of calling a method named `MyRunMethod`:

```AL
if Quantity > 5 then
MyRunMethod;
```

The `MyRunMethod` returns no data back to the calling code.

### <a name="Parameters"></a> Parameters  

In a method call, the parameters are separated by commas, and the optional parameters may be omitted starting from the right. For example, this means that if a method has three optional parameters, then you cannot omit the second parameter without omitting the third parameter.  
  
When passing parameters there are two options; *passing by value*, which is the default behavior, or *passing by reference*, in which case you must specify the `var` keyword.

- If a parameter is *passed by value*, then a copy of the variable is passed to the method. Any changes that the method makes to the value of the variable are local changes that affect only the copy, not the variable itself.  
  
- If a parameter is *passed by reference*, then a reference to the variable is passed to the method. The method can change the value of the variable itself.  

## Example 1  

The following shows the syntax for a method. The first example shows a method with two mandatory parameters.

```AL
method(Parameter1, Parameter2)  
```

Some built-in methods have optional parameters, the syntax is shown below. The optional parameters may be omitted starting from the right.

```AL
method([Optional1] [, Optional2] [, Optional3])  
```  
  
The method that uses the syntax above can be called by using the following code.  

```AL
method(Optional1, Optional2)  
```
  
## Example 2  

`Abs` is an example of an AL method that has a fixed number of parameters (1).  
  
```AL
var
    Value: Integer;
    PositiveValue: Integer;
begin
    Value := -1033; //A negative integer value  
    PositiveValue := Abs(Value); //Calculate the positive value 1033  
end
```  
  
## Example 3  

The method `DMY2Date` is an example of a method that can be called by using a variable number of parameters.  
  
```AL
var
    NewDate: Date;
begin
    NewDate := DMY2Date(5, 11, 1992); // Returns the date November 5, 1992  
end
```  
  
Depending on the use of the `DMY2Date` method, one, two, or three parameters can be passed to the method because the second and third parameters are optional. When the second and third parameters are not used, values from the system date are used as default values.  
  
## Example 4  

You can assign the return value of a method to a variable.  
  
```AL
ReturnVal := MyMethod(Param1);  
```  
  
## Example 5  

In this example, `MyMethod` returns a Boolean value. You can use the return value in a conditional statement.  
  
```AL
if (MyMethod(Param1)) then  
  <Statement1>  
else  
  <Statement2>  
```

## Example 6  
This example also illustrates how parameters can be *passed by value* or *passed by reference*. The following method declaration includes two parameters: `MyCustomer`and `MyDimension`:

```AL
procedure MyMethod(MyCustomer : Record Customer; var MyDimension : List of [Boolean])
```

The `MyCustomer` parameter is passed by value, and the `MyDimension` parameter is passed by reference.

## See Also

[Development Overview](devenv-dev-overview.md)  
[AL Methods](methods-auto/library.md)  
[AL Simple Statements](devenv-al-simple-statements.md)  
[AL Control Statements](devenv-al-control-statements.md)  
