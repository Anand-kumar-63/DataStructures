```java 
static void skip(String p , String up){  
    // when un changed string gets empty  
    if(up.isEmpty()){  
        System.out.println(p);  
        return;}  
    char ch = up.charAt(0);  
    if(ch == 'a'){  
        skip(p , up.substring(1));  
    }else {  
        skip(p+ch ,up.substring(1));  
    }  
}
```

```java 
static String skip2(String up){  
    if(up.isEmpty()){  
        return "";  
    }  
    char ch = up.charAt(0);  
    if(ch == 'a'){  
        return skip2(up.substring(1));  
    }else{  
        return ch + skip2(up.substring(1));  
    }  
}
```

```java
// if you want to skip that string starts with a particular string  
static String skipApple(String up){  
    if(up.isEmpty()){  
        return "";  
    }  
    char ch = up.charAt(0);  
    if(up.startsWith("apple")){  
        return skipApple(up.substring(5));  
    }  
    else {  
        return ch + skipApple(up.substring(1));  
    }  
}
```

```java
// you want to skip app only if apple comes  
static String Skipapp(String up){  
   if(up.isEmpty()){  
       return "";  
   }  
   if(up.startsWith("apple")){  
       return Skipapp(up.substring(3));  
   }  
   else{  
       return up.charAt(0) + Skipapp(up.substring(1));  
   }  
}
```

```java 
// skip app when not starts with apple  
static String Skipapp2(String up){  
    if(up.isEmpty()){  
        return "";  
    }  
    if(up.startsWith("apple")){  
        return Skipapp2(up.substring(5));  
    }  
    else if(up.startsWith("app")){  
        return Skipapp2(up.substring(3));  
    }  
    else{  
        return up.charAt(0) + Skipapp2(up.substring(1));  
    }  
}
```