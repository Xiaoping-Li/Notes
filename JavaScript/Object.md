# Object

## Object Basics
We define the following:

* _Object_: A collection of properties.
* _Property_: An association between a _name_ (i.e., _key_) and a _value_. Note that when the value associated with a key is a function, we call the property a _method_. A property name can be any valid **string**, or anything that can be converted into a string (including the empty string).

An object has properties associated with it, and we explain an object's properties as variables that are part of the object. We can think of an object's properties as a set of regular variables specific to that object that define its characteristics.

Let's say we have an object named **objectName** and a property named **propertyName**. We can access this property in the following ways:

1. _Dot Notation_: Call `objectName.propertyName`.
1. _Bracket Notation_: Call `objectName['propertyName']`. Note that **propertyName** must be enclosed in string quotes and is _case-sensitive_. Any property name that's not a valid JavaScript identifier (e.g., starts with a number, contains a space or hyphen, etc.) can only be accessed using bracket notation. This type of notation is also good to use when property names are dynamically determined (i.e., not known until runtime).

We can _add a new property to an existing object_ by assigning a value to it using either dot or bracket notation.
