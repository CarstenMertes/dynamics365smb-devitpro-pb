---
title: Serializing .NET framework types
description: How to serialize .NET framework types
author: SusanneWindfeldPedersen
ms.date: 04/01/2021
ms.topic: how-to
ms.author: solsen
ms.reviewer: solsen
---

# Serializing .NET framework types

In Microsoft .NET Framework, serialization is the process of converting an object into a format that can be transmitted across a network connection. Microsoft .NET Framework interoperability uses serialization for communication between client-side .NET Framework objects and server-side .NET Framework objects. When you configure DotNet variables in a [!INCLUDE[prod_long](includes/prod_long.md)] object, you can specify .NET Framework objects to target either the Business Central Windows client or [!INCLUDE[server](includes/server.md)]. In some cases, a client-side object and a server-side object must communicate and share data, such as return values and parameters. The serialization occurs when the following conditions are true:  

- When a server-side object is assigned to a client-side object, and vice-versa.  

- When a server-side object is passed as a parameter in a method call from the server to a client-side object, and vice-versa.  

Serialization requires that the .NET Framework types that are used by the DotNet variables are serializable. Many types in the Microsoft .NET Framework class library are already serializable. If you are using a .NET Framework type that cannot be serialized, then you must modify the type to make it serializable.  

> [!IMPORTANT]  
> For the [!INCLUDE[webclient](includes/webclient.md)], you cannot implement Microsoft .NET Framework interoperability objects that target the client.  

## Making a type serializable

There are two ways that you can make a .NET Framework type serializable. You can implement basic serialization by applying the [System.SerializableAttribute](/dotnet/api/system.serializableattribute) attribute to the type or you can implement custom serialization by using [System.Runtime.Serialization.ISerializable](/dotnet/api/system.runtime.serialization.iserializable) interface.  

### Basic serialization using SerializableAttribute

Basic serialization uses the .NET Framework to automatically serialize an object. To implement basic serialization on a type, you decorate the type with the [SerializableAttribute](/dotnet/api/system.serializableattribute) class as shown in the following example.  


```al
[Serializable]  
public class MyObject  
{  
    code   
}  
```

This method requires that you have access to the source code of the .NET Framework assembly.  

#### Basic serialization of date fields

You can use basic serialization only if all data fields in the type are serializable. Fields that are calculated at runtime cannot be serialized. If a field cannot be serialized, then at runtime, the serialization process will throw an exception and the AL code execution will fail. 

You can exclude fields from the serialization process by decorating the field with the [System.NonSerializedAttribute](/dotnet/api/system.nonserializedattribute) class.  

### Custom serialization using ISerializable interface

With custom serialization, you can create an object that controls the serialization of types in another object. This method is useful when you do not have access to the source code of the assembly that contains the .NET Framework types that you are implementing with .NET Framework interoperability. The custom object specifies which types will be serialized and how serialization will be done.  

To implement custom serialization, you create a class that implements the [ISerializable](/dotnet/api/system.runtime.serialization.iserializable) interface, and decorate the class with [SerializableAttribute](/dotnet/api/system.serializableattribute). In most cases, you must also implement the [System.Runtime.Serialization.ISerializable.GetObjectData](/dotnet/api/system.runtime.serialization.iserializable.getobjectdata) method and a special constructor that is used when the source object is deserialized. You use the **GetObjectData** method to populate the [SerializationInfo](/dotnet/api/system.runtime.serialization.serializationinfo) the data that is required to serialize the source object at runtime.  

The common language runtime calls the constructor during deserialization to construct a replica of the source object. The constructor takes two parameters, a **SerializationInfo** type and a [System.Runtime.Serialization.StreamingContext](/dotnet/api/system.runtime.serialization.streamingcontext) type. The **StreamingContext** parameter describes the source and destination of a given serialized stream.  

### Custom serialization example

The following code example demonstrates a custom serialization object that implements the basic functionality that is required for compliance with the **ISerializable** interface. In the first procedure of this example, you create a .NET Framework assembly that includes a serializable type. In the second procedure, in the [!INCLUDE[prod_short](includes/prod_short.md)] development environment, you create a codeunit that includes two DotNet variables for the serializable type. You set one variable to target the Business Central Windows client and the other to target the [!INCLUDE[server](includes/server.md)]. In AL code, you add code that transfers the value for the DotNet variable on the [!INCLUDE[server](includes/server.md)] to the Business Central Windows client. You will also add code that verifies that the data transfer is successful.  

##### To create the custom serialization object

1.  In Microsoft Visual Studio, create a C\# Class Library project called *SerializationSample*.  

2.  Add the following code.  

```c#  
 using System;  
 using System.Runtime.Serialization;  

 [Serializable]  
 public class SerializeWithInterface : ISerializable  
 {  
      // Defines a field that will not be serialized.  
      [NonSerialized]  
      private string notSerializedField;  
      // Defines two fields that will be serialized.  
      private int serializedIntField;  
      private string serializedStringField;  
      // Specifies literal field names.  
      private const string serializedIntFieldName = “serializedIntField”;  
      private const string serializedStringFieldName = “serializeStringField”;  

      // Defines a default constructor that initializes the object with default values.  
      public SerializeWithInterface()  
      {  
           this.serializedIntField = 1;  
           this.notSerializedField = string.Empty;  
           this.serializedStringField = string.Empty;  
      }  

      // Defines the protected constructor that is required by the ISerializable interface.  
      // Data is stored in the SerializationInfo argument and is extracted using the GetValue method.  
      protected SerializeWithInterface(SerializationInfo si, StreamingContext context)  
      {  
           this.serializedStringField = (string)si.GetValue(serializedStringFieldName, typeof(string));  
           this.serializedIntField = (int)si.GetValue(serializedIntFieldName, typeof(int));  
      }  

      // Fills the SerializationInfo object with data that must to be sent to the replicated object.  
      // Data is stored in the dictionary using the AddValue method.   
      // The SerializationInfo object is a key/value dictionary.  
      // The name you use to store the value must match the name used in the constructor.  
      // For this reason, a string constant is used.  
      public void GetObjectData(SerializationInfo info, StreamingContext context)  
      {  
           info.AddValue(serializedStringFieldName, this.serializedStringField);  
           info.AddValue(serializedIntFieldName, this.serializedIntField);  
      }  

      // Remaining class implementation is irrelevant for the serialization process.  
      // The SerializedStringField property is used by AL code to verify that the contained data is transferred between the server and client.  
      // SerializedStringField gets or sets the internal serialized string field.  
      public string SerializedStringField  
      {  
           get { return this.serializedStringField; }  
           set { this.serializedStringField = value; }  
      }  
 }
```  

3. Build the project.  

4. Copy the SerializationSample.dll to the **Add-ins** folder of the Business Central Windows client and [!INCLUDE[server](includes/server.md)] installation folders.  

By default, the path of the Business Central Windows client installation folder is [!INCLUDE[navnow_x86install](includes/navnow_x86install_md.md)]\\RoleTailored Client\\Add-ins.    

By default, the path of the [!INCLUDE[server](includes/server.md)] installation folder is [!INCLUDE[navnow_install](includes/navnow_install_md.md)]\\Service\\Add-ins.  


##### To test the serialization object

1.  In the AL Development Environment, add the following code.

```al
dotnet
{
     assembly(SerializationSample)
     {
          type(SerializationSample.SerializeWithInterface; SerializeWithInterface){}
     }
}

codeunit 50101 SerializationSample
{
    procedure Testing()
    var
        ServerObject: DotNet SerializeWithInterface;
        ClientObject: DotNet SerializeWithInterface;

    begin
        // Constructor that instantiates the ServerObject object on the server.  
        ServerObject := ServerObject.SerializeWithInterface();  
        // Constructor that instantiates the ClientObject object on the server.  
        ClientObject := ClientObject.SerializeWithInterface();  
        // Assign unique values to the data members in the two objects.  
        ServerObject.SerializedStringField := ‘ServerSide’;  
        ClientObject.SerializedStringField := ‘ClientSide’;  
        // Transfer the server object to the client object using serialization.  
        ClientObject := ServerObject;  
        // Test if the objects contain the same data.  
        If ClientObject.SerializedStringField <> ServerObject.SerializedStringField then  
            Error(‘Client object does not match the server object.’);  
            Message(‘Server data has been serialized to the client object.’);
    end;
}
``` 

The line that contains assignment of the **ServerObject** to the **ClientObject** causes the serialization process to run. When completed, the message **Server data has been serialized to the client object** appears, which verifies that the server object has been transferred to the client object.  

## Related information

[Get started with AL](devenv-get-started.md)    
[Getting started with Microsoft .NET interoperability from AL](devenv-get-started-call-dotnet-from-al.md)
[Migrating from .NET framework to .NET standard](devenv-migrate-from-dotnet-framework-to-dotnet-standard.md)    
[.NET control add-ins](devenv-dotnet-controladdins.md)    
[Subscribing to events in a .NET framework type](devenv-dotnet-subscribe-to-events.md)  
[Use Designer](devenv-inclient-designer.md)  
[AL Language extension configuration](devenv-al-extension-configuration.md)
