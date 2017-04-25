# OOLanguageComparison
## Contributors
* Devun Schmutzler
* Seth vonSeggern

## Languages
* Java 
* C Sharp

### Language Purpose/ Genesis

### Unique Features

### Name Spaces

In C#, namespaces are similar to those in C++. Unlike package names in Java, a namespace is not in any way tied to the location of the source file. While it is not strictly necessary for a Java source file location to mirror its package directory structure, it is the conventional organization.

***

Java uses packages. They are used to organize files or public types to avoid type conflicts. Package constructs can be mapped to a file system.
    
```java 
System.Security.Cryptography.AsymmetricAlgorithm aa; //may be replaced:
import System.Security.Crypography; 
class xxx { ... AsymmetricAlgorithm aa; ... }
```

There is no alias for packages. You have to use import statement or fully-qualified name to mention the specific type.

```java
pacakge N1.N2;
class A {}
class B {}
or
package N1.N2;
class A {}

//another source file
package N1.N2;
class B {}
```
Package cannot be nested. One source file can only have one package statement.

***

C# uses namespaces. They are used to organize programs, both as an "internal" organization system for a program, and as an "external" organization system.

```c#
System.Security.Cryptography.AsymmetricAlgorithm aa; //may be replaced:
using System.Security.Crypography; 
AsymmetricAlgorithm aa;
```
Alternatively, one could specify an alias for the the namespace, eg. :
```c#
using myAlias = System.Security.Crypography; //and then refer to the class with 
myAlias.AsymmetricAlgorithm 
```
Additional Example:
```c#
namespace N1.N2
{
    class A {}
    class B {}
}
or
namespace N1
{
    namespace N2
    {
        class A {}
        class B {}
    }
}
```
### Types
Java supports primitive and reference types. The primitive types are boolean, byte, short, char, int, long, float, and double. Reference types are all classes, including arrays and references. Java does not support creating new value types.

C# supports value and reference types. Reference types include classes, delegate, arrays, and interfaces. Value types include sbyte, byte, short, ushort, int, uint, long, float, double, bool, char, decimal, enum, and structs. Unlike Java, new value types can be defined using structs, i.e.:
```c#
struct Point
{
    public int x, y;
    public Point(int x, int y) {
    this.x = x;
    this.y = y;
    }
}
```
### Classes

### Instance Reference Name in Data Type

The keyword "this" is a Java language keyword that represents the current instance of the class in which it appears. It is used to access class variables and methods.

Since all instance methods are virtual in Java, this can never be null.

```java
public class Point {
    public int x = 0;
    public int y = 0;
        
    //constructor
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

***

The keyword this in C# works the same way as in Java, for reference types. However, within C# value types, this has quite different semantics, being similar to an ordinary mutable variable reference, and can even occur on the left side of an assignment.

One use of this in C# is to allow reference to an outer field variable within a method that contains a local variable that has the same name. In such a situation, for example, the statement ```c# var n = localAndFieldname;``` within the method will assign the type and value of the local variable localAndFieldname to n, whereas the statement ```c# var n = this.localAndFieldname;``` will assign the type and value of the outer field variable to n.

```c#
public class Employee
    {
        private string name;
        private string alias;
        private decimal salary = 3000.00m;

        // Constructor:
        public Employee(string name, string alias)
        {
            // Use this to qualify the fields, name and alias:
            this.name = name;
            this.alias = alias;
        }
    }
```

### Properties

Java does not have property getters and setters built into the language. Instead you must define your own methods to read and write. Therefore there are now backing variables to utilize. As for computed properties, simply by defining our own getter method we have inherently created a computed property that is recalculated ever time we call the method.

```java
public class User {
    private String name;

    public String getName() { return this.name; }
    public void setName(String name) { this.name = name; }
}
```

***
C# however, has built in properties get and set. Recent C# versions also allow "auto-implemented properties" where the backing field for the property is generated by the compiler during compilation. This means that the property must have a setter, however it can be private. However, you can use the notion of backing variables to manipulate what you do when getting or setting a variable, such as a computed property that requires some complex logic.

Example without backing variables:
```c#
public class User {
    public string Name { get; set; }
}
```
Example with backing variables:
```c#
public class User {
    public string Name
    {
        get { return _name; } //this allows you to manipulate what is being returned if you so choose
        set { _name = value; }
    }
}
```

### Interfaces/Protocols
-Devun

### Inheritance/Extension
-Devun

### Reflection
-Devun

### Memory Management
-Seth

### Comparisons of References and Values
-Seth

### Null/Nil References
-Devun

### Errors and Exception Handling
-Seth

### Lambda Expressions, Closures, or Functions as Types
-Devun

### Implementation of Listeners and Event Handlers
-Seth

### Singleton
-Devun

### Procedural Programming
-Devun

### Functional Programming
-Seth

### Multitheading
-Devun
