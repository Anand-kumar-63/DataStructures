# Inheritance
# Polymorphism 
- Compile time polymorphism 


- Runtime or Dynamic Polymorphism
[*overriding is done at run time after the compilation*]
```java
public class Rectangle extends shape {  
    @Override  
    void area() {  
        System.out.println("This is the area of the Rectangle");  
    }  
}

public class Circle extends shape{  
    @Override  
    void area() {  
        System.out.println("This is the area of the Circle");  
    }  
}

public class shape {  
    void area(){  
        System.out.println("Hey there this is shapes area");  
    }  
}

public class Square extends shape {  
    @Override  
    void area() {  
        System.out.println("This is the area of the Square");  
    }  
}
```

```java
package OOPs.Polymorphism;  
import java.awt.*;  
public class Main {  
    public static void main(String[] args) {  
        shape one = new shape();  
        shape two = new Circle();  
        shape three = new Square();  
        shape four = new Rectangle();  
        one.area();  
        two.area();  
        three.area();  
        four.area();  
    }  
}  
// In this reference Varaiable is of type shape and object  
// variable has different types  
// then how java decides at the run time using dynamic method dispatch  
// that which method to run??
```
- Reference type defines which one to access but the object type define which one to run.
- Means reference type that is parent has some methods which are overridden by the Childs so those methods which are overridden by the Childs are the only methods that can be executed by forming the objects that is why - [Reference type defines which one to access but the object type define which one to run.]
- reference variable tells which all things you can access 
- When an overridden superclass methods is called using a superclass reference variable java determines which version of that methods to execute based on the type of the object hence this determination is done at run time using dynamic methods dispatch
### final keyword
- To stop the overriding of the methods prevent overriding using the final keyword
- *This is also called as [Early Binding*]
- you can also use it to prevent inheritance sometimes you would want to prevent a class from being inherited so you can make that class final 
```java
 public class shape{
  // you cannot override the final methods in subclasses
  final void area(){
     System.out.println("Hey there!");
   }
 } 
```

## static Methods 
- Static methods cannot be overridden  you can inherit but cannot override the static methods
![[WhatsApp Image 2026-02-04 at 7.14.16 PM.jpeg]]
- The only one that is present in the main class will be used all over the placed be it using the object of the main class or the subclass that is inheritance property
# Encapsulation
- Encapsulation focuses on hiding the complexity of the system.
- In this we use [getters] and [setters] and classes and stuff. 
# Abstraction 
- We use abstract classes and interfaces.
- Data hiding is focused on Insecurity
