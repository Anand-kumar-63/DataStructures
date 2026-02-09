## find Ascii values 
```java
static void ascii(char ch){  
    System.out.println(ch+0);   
}
```

## Convert String to int
```java
// `Integer.parseInt()`, `Double.parseDouble()` , or `Long.parseLong()`
   int s = Integer.parseInt(String s);
// if the input is way too long that it cannot be handled by int or even long
import java.math.BigInteger;
   // convert the binary string into decimal
   BigInteger a1 = new BigInteger(a, 2);
   BigInteger b1 = new BigInteger(b, 2);
   // it doesn't support normal sum  
   BigInteger sum = a1.add(b1);
   return sum.toString(2);
```
## add without using add or sub operator using binary operators
```java
public int getSum(int a, int b) {
       while (b != 0) {
            int carry = (a & b) << 1;  // carry
            a = a ^ b;                // sum without carry
            b = carry;               // add carry in next step
        }
        return a;  
    }
```