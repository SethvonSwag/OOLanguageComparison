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
class Employee
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

### Interfaces/Protocols

### Inheritance/Extension

### Reflection

### Memory Management

### Comparisons of References and Values

### Null/Nil References

### Errors and Exception Handling

### Lambda Expressions, Closures, or Functions as Types

### Implementation of Listeners and Event Handlers

### Singleton

### Procedural Programming

### Functional Programming

### Multitheading
