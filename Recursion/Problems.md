## Array problems  using Recursion
Question1:-
```java
package Recursion;  
// check if array is sorted or not using recursion  
public class checksortedarray {  
    public static void main(String[] args){  
        int[] arr = {1,2,3,45,56};  
        System.out.println(check_sorted_array(arr,0));  
    }  
    static boolean check_sorted_array(int[] arr , int index){  
        if(index == arr.length-1){  
            return true;  
        }  
        return arr[index]<arr[index+1] && check_sorted_array(arr , index+1);  
    }  
}
```
Question2:- 
```java 
package Recursion;  
// find the target by applying linear recursion on the arary  public class LinerSearch {  
public static void main(String[] args){  
    int[] arr = {1,101,94,49,67,66,77,88};  
    System.out.println(liner_search(arr,0,66));  
}  
static int liner_search(int[] arr, int index , int target){  
    if(arr[index]==target){  
        return index;  
    } 
    if(index==array.length){
         return -1;
    }
    else if(target != arr[index]){  
        return liner_search(arr,index+1, target);  
    }else {  
        return Integer.MIN_VALUE;  
    }  
}  
}
```
## Pattern problems using Recursion 
Question3:- 
```java
package Recursion;  
// print a triangle pattern using recurrsion public class patterns {  
public static void main(String[] args){  
     form_pattern(0,4);  
}  
static void form_pattern(int c,int r){  
   if(r == 0){  
       return;  
   }  
   if(r>c){  
       System.out.print("*");  
       form_pattern(c+1 , r);  
   }  
   else {  
       System.out.println();  
       form_pattern(0,r-1);  
   }  
}}
```
Question4:-
```java
package Recursion;  
// print a triangle pattern using recurrsion  
public class patterns {  
public static void main(String[] args){  
     form_pattern(0,1);  
}  
static void form_pattern(int c,int r){  
   if(r == 0 || r == 5 ){  
       return;  
   }  
   if(r>c){  
       System.out.print("*");  
       form_pattern(c+1 , r);  
   }  
   else{  
       System.out.println();  
       form_pattern(0,r+1);  
   }  
}}
```
# sorting using recursion 
Question5:- Bubble sort 
```java 
package Recursion;  
import java.util.Arrays;  
// bubblesort using recursion
public class Bubblesort {  
public static void main(String[] args){  
    int[] test = {10,9,7,6,5,4,3,1};  
    int[] result = Recursive_bubble(test , 0 );  
    System.out.println(Arrays.toString(result));  
}  
static int[] Recursive_bubble( int[] arr , int i ){  
      if(i == arr.length-1) {  
          return arr;  
      }  
      for(int k = 0; k<arr.length-i-1; k++){  
           if(arr[k]>arr[k+1]){  
              int temp = arr[k];  
              arr[k] = arr[k+1];  
              arr[k+1] = temp;  
           }}  
      return Recursive_bubble(arr,i+1);  
}}
```
Question6:-
```java
package Recursion;  
import java.util.Arrays;  
// Bubble Sort Using Recursion col and row approach public class Bubblesort2 {  
public static void main(String[] args){  
  int[] test = {10,9,8,7,6,5,4,3,2,1};  
  int[] result = Bubble_sort(test , 0 , test.length-1);  
  System.out.println(Arrays.toString(result));  
}  
static int[] Bubble_sort(int[] array , int c, int r){  
    if(r==0){  
        return array;}  
    if(r>c){  
        if(array[c]>array[c+1]){  
            int temp = array[c];  
            array[c] = array[c+1];  
            array[c+1] = temp;  
        }  
       return Bubble_sort(array,c+1,r);}  
    else {  return Bubble_sort(array , 0  , r-1);  }}  
}
```
Question7:- Selection Sort 
```java 
package Recursion;  
import java.util.Arrays;  
public class SelectionSort {  
    public static void main(String[] args){  
        int[] test = {99,2,9,7,3,4,5,1,12};  
        int[] result = Selection_sort(test , 0 , test.length-1 , 1);  
        System.out.println(Arrays.toString(result));  
    }  
    static int[] Selection_sort(int[] array , int c , int r , int max_index){  
        if(r==0){return array;}  
        if(r>c){  
            if(array[c]>array[max_index]){  
                return Selection_sort( array , c+1 , r , c);  
            }else {  
                return Selection_sort(array , c+1 , r, max_index );  
            }}  
        else{  
            // now swap the thing  
            int temp = array[max_index];  
            array[max_index] = array[r];  
            array[r] = temp;  
            return Selection_sort(array, 0 , r-1 , 0);  
        }}}
```
## Merge sort using Recursion
![[Pasted image 20251214215058.png]]
```java
package Recursion;  
import java.sql.Array;  
import java.util.Arrays;  
public class Mergesort {  
    public static void main(String[] args){  
          int[] test = {99,87,101,106,56,43,49};  
          int[] result = merge_sort(test);  
          System.out.println(Arrays.toString(result));  
    }  
    static int[] merge_sort(int[] test_array ){  
      if(test_array.length==1){  
          return test_array;  
      }  
      int mid = test_array.length/2;  
      int[] left = merge_sort(Arrays.copyOfRange(test_array , 0 , mid));  
      int[] right = merge_sort(Arrays.copyOfRange(test_array,mid,test_array.length));  
      return merge(left , right);  
    }  
    static int[] merge(int[] first , int[] second){  
        int[] mix = new int[first.length + second.length];  
         int i = 0;  
         int j = 0;  
         int k = 0;  
        while(i < first.length && j < second.length){  
            if(first[i]>second[j]){  
                mix[k] = second[j];  
                j++;  
            }  
            else{  
                mix[k] = first[i];  
                i++;  
            }  
            k++;  
        }  
        while (i < first.length){  
            mix[k] = first[i];  
            k++;  
            i++;  
        }  
        while(j<second.length){  
            mix[k] = second[j];  
            j++;  
            k++;  
        }  
        System.out.println(Arrays.toString(mix));  
        return mix;  
    }  
}
```
#### Time complexity:-
![[Pasted image 20251220032510.png]]
- At every level n elements are merged together  so at each level how many Comparisions are made in worst case - (N-1) Comparisions....
- So time complexity - [ (N-1)log2N ] = [ (N-1)log2N ]
- Space complexity - [ N ]
- SWE[-<||>\\<||>-]