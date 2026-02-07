When to use-
- when in problem you have to deal with permutations and combinations 
- when you are dealing with non-adjacent collections..
  [1,2,3,4] - [1,2] , [2,3] , [4,5] , [5,6] , [2,4] ,[1,2,4] ,[1,2,3] ,[1] etc.
   elements can be continuous or not 
## Recursion and iteration 
```java 
str = "abc";
ans = ["a","b","c","ab","bc","ac","abc"];
// total number of substrings - 7
```

#important #whentouse #subsetpattern
 [this pattern of taking some elements and removing some elements is known as subset pattern...]
 [for every character we have two choices either take it or ignore it...]
-  There are two String and one is processed[empty string] and one is unprocessed.["abc"] 
-  At every recursion call either you will select a char or not going to select to add in the   processed String.
![[Pasted image 20260128002421.png]]
	 - Return all the answers in the base case situations to the above function calls... 
 ## Question
 How many sequence are possible with the given string ??? 
  ```java
  
  // p is processed varibale and up is unprocessed variable
  package Recursion;  
public class Subsets{  
    public static void main(String[] args){  
      subsequence("","cba");  
    }  
    static void subsequence(String p , String up) {  
        if (up.isEmpty()) {  
            System.out.println(p);  
            return;  
        }  
        subsequence(p + up.charAt(0), up.substring(1));  
        subsequence(p, up.substring(1));  
    }  
}
  ```
  output- 
  ![[Pasted image 20260128005409.png]]
```java 
// if you want to return the whole arraylist containing the all the -  
static ArrayList<String> ReturnList(String p , String up){  
    if(up.isEmpty())  
    {  
        ArrayList<String> result = new ArrayList<>();  
        result.add(p);  
        return result;  
    }  
    ArrayList<String> left = ReturnList(p+up.charAt(0),up.substring(1));  
    ArrayList<String> right = ReturnList(p,up.substring(1));  
    left.addAll(right);  
    return left;  
}
```
Output -
![[Pasted image 20260128160826.png]]
```java
/// if you want to print corresponding ascii values
static void SubsequenceAscii(String p , String up){  
    if(up.isEmpty()){  
        System.out.println(p);  
        return;}  
    SubsequenceAscii(p+(up.charAt(0)+0) , up.substring(1));  
    SubsequenceAscii(p,up.substring(1));  
}
// output - [ 979899 , 9798 ,...... 99]
```

```java
// If you want the ascii values corresponding to the subsequences 
// and store them all in the arraylist and return back...
static ArrayList<String> ReturnList2( String p, String up){  
    if(up.isEmpty()){  
        ArrayList<String> result = new ArrayList<>();  
        result.add(p);  
        return result;  
    }  
    ArrayList<String> left = ReturnList2(p + (up.charAt(0)+0),up.substring(1));  
    ArrayList<String> right = ReturnList2(p , up.substring(1));  
    left.addAll(right);  
    return left;  
}
```
output-
![[Pasted image 20260128181401.png]]
## Array subsets using Iteration 
```java
public class ArraySubsets {  
    public static void main(String[] args){  
        int[] arr = new int[]{1,2,3};  
        List<List<Integer>> result = sub(arr);  
        for(int i=0; i<result.size();i++){  
            System.out.println(result.get(i));;  
        }}  
    static List<List<Integer>> sub(int[] arr){ 
    // You have to make an Outer ArrayList that is going to contain the
    // all the subsets[]   
        List<List<Integer>> outer = new ArrayList<>();  
    // first of all you will add an empty ArrayList [[] ]   
      outer.add(new ArrayList<>());  
    // now you are going to loop over different elements [1,2,3,]  
        for(int item:arr){  
            int n = outer.size(); // 1 for itme:1 , 2 for item:2 , 4 for item:4  
            for(int i=0;i<n;i++){  
                List<Integer> internal = new ArrayList<>(outer.get(i));  
                internal.add(item);  
                outer.add(internal);  
     // for item:1 the outer arraylist will now  be containing 2  arraylist [[],   [1]] then -> [[],[1],[2],[1,2]] then -> [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
            }}  
        return outer;
    }}
```

Question- 
If you have Quetions where you have to return the total number of combinations of the String characters like abc - [ abc  ,  bca  , cba , acb , bac , cab ]
![[Pasted image 20260129224156.png]]
```java
// If you have quetions where you have to return the total number of combinations     of the String characters like abc - [abc , bca , cba , acb , bac , cab]
static void permutations(String p , String up){  
    if(up.isEmpty()){  
        System.out.println(p);  
        return;  
    }  
    char ch = up.charAt(0);  
    for(int i =0 ; i<= p.length();i++){  
        String f = p.substring(0,i);  
        String s = p.substring(i,p.length());  
        permutations( f+ch+s , up.substring(1));  
    }  
}
// if you want to return the arrayList
static ArrayList<String> permutationsList(String p , String up){  
      if(up.isEmpty()){  
          ArrayList<String> ans = new ArrayList<>();  
          ans.add(p);  
          return ans;  
      }  
      ArrayList<String> result = new ArrayList<>();  
      char ch = up.charAt(0);  
      for(int i = 0; i<=p.length() ;i++){  
          String f = p.substring(0,i);  
          String e = p.substring(i,p.length());  
          result.addAll(permutationsList(f+ch+e,up.substring(1)));  
      }  
      return result;  
}

// if you want to count the permutations 
// PermutationsCount-  
static int permutaioncount(String p , String up){  
    int count = 0;  
    if(up.isEmpty()){return 1;}  
    char ch = up.charAt(0);  
    for( int i=0; i<=p.length(); i++ ){  
         String s = p.substring(0,i);  
         String e = p.substring(i,p.length());  
         count += permutaioncount(s+ch+e,up.substring(1));  
    }  
    return count;  
}
```

Problem 17
![[Pasted image 20260130003454.png]]
```java 
public class problem17 {  
    public static void main(String[] args) {  
        System.out.println(pod("","12"));  
    }  
    static ArrayList<String> pod(String p , String up){  
        if(p.isEmpty()){  
            ArrayList<String> res = new ArrayList<>();  
            res.add(p);  
            return res;  
        }  
        ArrayList<String> result = new ArrayList<>();  
        int digit = up.charAt(0)-'0'; // this will convert '2' to 2  
        for(int i=(digit-1)*3 ; i < digit*3 ; i++){  
                char ch = (char)('a'+i);  
                result.addAll(pod(p+ch,up.substring(1)));  
        }  
        return result;  
    }  
}
```

Dice problem -
![[Pasted image 20260130004134.png]]