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
Java supports primitive and reference types. The primitive types are boolean, byte, short, char, int, long, float, and double. Reference types are all classes, including arrays and references. 

C# supports value and reference types. Reference types include classes, delegate, arrays, and interfaces. Value types include sbyte, byte, short, ushort, int, uint, long, float, double, bool, char, decimal, enum, and structs.
### Classes

### Instance Reference Name in Data Type

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
