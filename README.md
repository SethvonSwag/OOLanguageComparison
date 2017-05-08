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

* Definition
    * Classes are defined in the same manner in Java and C#. A modifier keyword is followed by the 'class' keyword and then the name of the class follows, i.e:
```java
modifier class ClassName {
    fields and methods
}
```

* New Instances
    * Instantiation is also similar between the two languages. The basic syntax for that is to call the 'new' keyword followed by the name of the class. i.e. ``` new NewClass()```

* Constructing/Initializing
    * Both Java and C# use constructors to create instances. The constructors are public methods with the same name as the class. These methods however, can be overloaded to create objects with only the properties they need. 
```java
public class Dog{
    public string name;
    public int age;
    
    public Dog(){
        this.name = "Fido";
        this.age = 3;
    }
    
    public Dog(string name){
        this.name = name;
        this.age = 3;
    }
    
    public Dog(string name, int age){
        this.name = name;
        this.age = age;
    }
}
```

* Destructing/De-Initializing
    * Java has a garbage collector that destroys objects in an unpredictable manner. Because of the collector, there is no destructor in Java. While destructors do exist in C#, there are invoked automatically, thus do not need to be called. The syntax of the function that is called is ``` ~ClassName()```. Notice, there is no modifier and the method takes no parameters.

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

In Java an interface is like a class, and is of a reference type. Interfaces in Java may contain methods, default method implementations, constants, static methods, as well as nested types. Methods in general, should not have concrete implementations, and should be abstract. However, in a new version of Java default implemenations have allowed developers to give methods in an interface a basic implemenation that can be used if one wishes to not implement it themselves. Java allows for a class to implement multiple interfaces at a time. In order for a class to be concrete and instantiable, it must implement all methods that do not have a default implementation.

```java
interface Animal {
   public void eat();
   public void travel();
}
public class MammalInt implements Animal {

   public void eat() {
      System.out.println("Mammal eats");
   }

   public void travel() {
      System.out.println("Mammal travels");
   } 
}
```

***
Interfaces are also a part of C#. Interfaces in C# include properties, methods, indexers and events. Nothing in the interface class can be implemented. Implementation must be left to the class that the interface is being imposed upon. It is important to note that interfaces can't be static and are understood to always be public. There is not limit to the number of interfaces that a single class can implement. 

```c#
interface Car {
    void Drive();
}

public class Nissan : Car {
    public void Drive(){
        //some fancy implementation here that makes the car go fast..
    }
}
```

### Inheritance/Extension

Java allows for classes to inherit from one another. The limitation is that a class can only have one parent class that it inherits from. To inherit from a clas syou must you the ```extends``` keyword after defining the class name. A base class has access to all nonprivate members of the superclass. To talk to the superclass's constructor you must call upon it by using ```super();``` To access superclass methods simple use ```super.baseClassMethod();```.

```java
public class Rectangle {
    public int numberOfSides;
    
    public Rectangle(int NumberOfSides){
        this.numberOfSides = numberOfSides;
    }
}

public class Square extends Rectangle {
    public Square(){
        super(4);
    };
}
```

***
Inheritance in C# is native feature. In it you can simply create a new class, and after having defined its parent class, and use the Subclass : Superclass syntax to show that subclass inherits from superclass. Unlike Java, to reference the superclass's constructor you must you the SublcassConstructor : base() syntax. Here, base references the superclass constructor. This was done with the intention of relieving issues concerning when the superclass constructor should be called (before or after doing work in the subclass constructor), because in C# it is always called before the subclass one. It is also important to note that C# does not support multiple inheritance, but it does allow for extension.

```c#
public class Rectangle {
    public int NumberOfSides;
    
    public Rectangle(int NumberOfSides){
        this.NumberOfSides = NumberOfSides;
    }
}

public class Square : Rectangle {
    public Square() : base(4){};
}
```

### Reflection
Reflection is supported in Java. There are methods in the reflect package that allow you to inspect a class and learn about its class, constructors, methods, fields, as well as many additional pieces of information. It is important to note that relfection can only see public members.

```java
OOIsDead burntToast = new OOIsDead();
Class burntToaster = burntToast.getClass();
```
Here you could have substituted Class and getClass for constructors, methods, or fields.

***

In C# the same is true about reflection. A noteable difference is that C# inspects private and protected members in addition to public ones. 

### Memory Management
Java manages memory with garbage collection. Objects are ready to be collected when all references to that object no longer exist. As mentioned before, garbage collection is unpredictable, running periodically, so it is not possible to tell exactly when an object will be destroyed. 

In C#, the Common Language Runtime actually handles memory. Like Java though, garbage collection is used to remove unreferenced objects.

### Comparisons of References and Values
Java supports both comparison by reference and by value. The ```==``` operator compares two values.
```java
int a = 0;
int b = 0;
if (a == b){
    // do something
    }
```
The ```==``` operator can also be used in Java to check if two objects hold the same reference.
   * This should not however be used to check the values inside that reference. The ```.equals()``` method should instead be used.
   ```java 
   String a = "hello";
   String b = "hi";
   if (a.equals(b)){
    // do something
   }
   ```
Like in Java, the ``` ==``` is used in C# to compare two value types. ```.equals()``` also works to compare two values. For reference types, the ```==``` operator checks if two references are the same and ```.equals()``` compares the values of the references, like Java.

### Null/Nil References
Java uses the notion of ```null``` references. A reference is null when it contains no link to memory. Unfortunately Java has no native features to deal with the handling of null references gracefully and cleanly. Instead we must rely upon the knowledge and competence of the developer to check for it. 

```java
String name = null;
String legalName = null;
if(name!=null) {
    legalName = name;
}
else {
    legalName = "John Doe"
}
```

***

C# also uses the term ```null``` to represent the lack of a reference to memory. It is by default the value of all variables that utilize references. Important to note is that types line DateTime and boolean can never be set to null. C# has a way of handling nulls called null propogation. It allows you to use the syntax ```?.``` at the end of an object instead of just ```.```. This checks to see if the object you are referencing first is null or not, and if the first object is null will not try and access its member after which would normally cause and exception. This saves us time using an ```if(something == null){};``` that we all dread. Another feature of C# surrounding nulls is the idea of the null-coalescing operator ```??```. It is a conditional statement that checks for null and allows you to assign another value if the intended one is null.

```c#
String Name = null;
String LegalName = Name ?? "John Doe";
```

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

### Multithreading
-Devun
