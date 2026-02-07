## Maze Problem 
![[Pasted image 20260130022423.png]]
![[Pasted image 20260130022458.png]]
// print the total number of ways you can reach the last element in the 2d matrix of size [n*n]
// and also the direction or ways you are taking like [dd , dld , ....]
![[Pasted image 20260130155424.png]]

```java
public class mazeProblem {  
    public static void main(String[] args) {  
        int result = findpath("",3,3);  
        System.out.println(result);  
    }  
    static int findpath(String s , int r , int c){  
        if(r==1||c==1){  
            System.out.println(s);    
            return 1;  
        }  
        int left = findpath(s+'D',r-1,c);  
        int right = findpath(s+'L',r,c-1);  
        return left+right;  
    }
// follow same thoery as of processed and unprocessed subsets problem for writing the paths      
```
```java
*If you want to return the ArrayList containing all the possible paths*
```java
static ArrayList<String> PathList(String p , int r , int c){  
   if(c==1||r==1){  
       ArrayList<String> path = new ArrayList<>();  
       path.add(p);  
       return path;  
   }  
   ArrayList<String> result =  new ArrayList<>();  
   if(r>1){  
       result.addAll(PathList(p+"D",r-1,c));  
   }  
   if(c>1){  
       result.addAll(PathList(p+"L",r,c-1));  
   }  
   return result;  
}
```

*If you can move diagonally as well*
![[Pasted image 20260130161709.png]]
```java
// if you can traverse in the dialonal as well  
static ArrayList<String> Path(String s,int r,int c){  
    if(r==1||c==1){  
        ArrayList<String> path = new ArrayList<>();  
        path.add(s);  
        return path;  
    }  
    ArrayList<String> result = new ArrayList<>();  
    if(r>1){  
        result.addAll(Path(s+"D",r-1,c));  
    }  
    if(c>1){  
        result.addAll(Path(s+"L",r,c-1));  
    }  
    if(r>1 && c>1){  
        result.addAll(Path(s+"Di",r-1,c-1));  
    }  
    return result;  
}
//output - 
```

***Problem- Maze with obstacles***
```java
static void PathRestrictions(String s,  
                             boolean[][] maze , int r, int c)  
{  
    if(r==maze.length-1 && c==maze[0].length-1){  
        System.out.println(s);  
        return;  
    }  
    if(!maze[r][c]){  
        return;  
    }  
    if(r < maze.length-1){  
        PathRestrictions(s+"D",maze,r+1,c);  
    }  
    if(c < maze[0].length-1){  
        PathRestrictions(s+"L",maze,r,c+1);  
    }  
}}
// output - ddll , lldd
```

***When you are allowed to move in all the directions be it down , right , diagonally as well as  
left and Upwards
- *there are some points you have to remember*
- *if you wanna do it recursively then you just need to put that cell on false on that recursion call then set it to true while going out of that recursion call * - because without this you will fall into the stack overflow kind of situation as you are ending up at the same cell again and again..
- *so just before entering the cells put that cell to false to prevent it to get used in the same recursion call and  then whileyou are leaving it put that cell to true to use it by other recursion call*
```java
// what If every direction is  
// allowed to move in then what will be all the possible combinations  
static void AllPath(String s, boolean[][] maze , int r , int c ){  
    if(r==maze.length-1||c==maze[0].length-1){  
        System.out.println(s);  
        return;  
    }  
    if(!maze[r][c]){  
        return;  
    }  
    // you are entering this cell so you have to put  
    // it to false so that  further deeper recursion funtions    // cannot access it    maze[r][c]= false;  
    if(r < maze.length-1){  
        PathRestrictions(s+"D",maze,r+1,c);  
    }  
    if(c < maze[0].length-1){  
        PathRestrictions(s+"R",maze,r,c+1);  
    }  
    if(r > 0){  
       PathRestrictions(s+"U",maze,r-1,c);  
    }  
    if(c > 0){  
        PathRestrictions(s+"L",maze,r,c-1);  
    }  
    // Now When you Will be leaving this recursion fnc.  
    maze[r][c] = true;  
}
```




