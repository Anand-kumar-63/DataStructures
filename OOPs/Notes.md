- This class can be accessed from the other class within the same package
```java
package OOPs.two;  
public class on {  
    int age;  
    String name;  
    int salary;  
    // This static variable can be accessed without the need to create a new 
    // Object instance and these are global scoped that when you change it once it        will get reflected to all the objects 
    static int population;  
    on(int age, String name , int salary){  
        this.age = age;  
        this.name = name;  
        this.salary = salary;  
        // for example whenever you will create this Object instances this population will increase by one and it wll get changed globally 
        on.population += 1;  
    }  
}
```
for example
```java
package OOPs.two;  
public class tw {  
    public static void main(String[] args) {  
        on hey = new on(12,"Anand",5600);  
        on hey1 = new on(12,"Anand",5600);  
        on hey2 = new on(12,"Anand",5600);  
        System.out.println(on.population); // this will output in 3  
        //System.out.println(hey.name);  
        //System.out.println(hey.age);        
        // you cannot ccess a non-static      
        //greeting();       
    }
    void greeting(){
        System.out.println("he reh ejcb");  
    }  
}
```

## Static Keyword -
- A static method can call only static methods.
- Static method need object instance of the non static variables or methods
- Static methods can be accessed directly by the Classname.
- you Don't need to make a reference of it. or you can say static is not dependent on objects.
- 
### you cannot access any Non-Static method from the Static Context
```java

```
![[Pasted image 20260202184123.png]]

### but a Non-Static context can access an static context![[Pasted image 20260202184403.png]]
#note - If you are static in nature then you are good to go but if you are not static so either you get converted into static or get me your object instance for the access
![[Pasted image 20260202184908.png]]
#example In this you cannot access the non static variable inside the message method of class   Human which is static in nature. 
![[Pasted image 20260202190528.png]]
