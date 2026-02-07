# linked list declaration 
```java
package LinkedList;  
public class Basics {
    // how to make a node structure  
    public static class Node{  
        int data;  
        Node next;  
        Node(int data){  
            this.data = data;  
        }  
    }  
    public static void main(String[] args){  
        // you can create a node like this  
        Node one = new Node(1);  
        Node two = new Node(2);  
        Node three = new Node(3);  
        Node four = new Node(4);  
        // 1 2 3 4  
        one.next = two;  
        two.next = three;  
        three.next = four;  
        // 1->2->3->4    
    }  
}
```
## print linked list 
- Using for Loop
```java
 Node temp = head; // this will reference to the address of the first 
 while(temp!=null){
   System.out.println(temp.data);
   temp = temp.next;
 }
```
- Using Recursion
```java
// to print the linkedList using recurion 
    static void func(Node head){  
        // head -> [1| next] -> [2| next] -> [3| next] -> [4 | null]  
        if(head==null) return;  
        System.out.println(head.data); 
        func(head.next);   
    }
    public static void main(String[] args){  
        // you can create a node like this  
        Node one = new Node(1);  
        Node two = new Node(2);  
        Node three = new Node(3);  
        Node four = new Node(4);  
        // 1 2 3 4  
        one.next = two;  
        two.next = three;  
        three.next = four;  
        // 1->2->3->4    
    }  
```
- Reverse order 
```java
static void displayReverse(Node head){
  if(head==null)
  func(head.next);
  System.out.println(head.data+" ");
}
```
![[Pasted image 20260203234148.png]]
## length
![[Pasted image 20260205191417.png]]
```java
// using recursion
static int length(Node head){  
    int count=0;  
    int ans = 0;  
    if(head!=null){  
         count+=1;  
         ans = length(head.next);  
     }  
 // using loop    
static int findlength(Node head){  
    int count = 0;  
    while(head!=null){  
        count++;  
        head = head.next;  
    }  
    return count;  
}     
```

## Implementation
```java
package LinkedList;  
public class Implementation{  
    public static class Node{  
        int data;  
        Node next;  
        public Node(int data){  
            this.data = data;  
        }  
    }  
    public static class LinkedList{  
        Node head = null;  
        Node tail = null;  
        // to insertatend
        void insertatend(int val){  
            Node temp = new Node(val);  
            if(head==null){  
                head = temp;  
            }  
            else {  
                tail.next = temp;  
            }  
            tail = temp;  
        }  
        // to display the linkedList
        void display(){  
            Node temp = head;  
            while(temp!=null){  
                System.out.println(temp.data);  
                temp = temp.next;  
            }  
        }  
        // to find the size of the linked list
        int size(){  
            int count = 0;  
            Node temp = head;  
            while(temp!=null){  
                count++;  
                temp = temp.next;  
            }  
            return count;  
        }  
        // void insertatBeg  
        void insertAtBeg(int val){  
            Node temp = new Node(val);  
            if(head==null){  
                head = temp;  
                tail = temp;  
            }else{  
                temp.next = head;  
                head = temp;  
            }  
        }  
    }  
    public static void main(String[] args) {  
      LinkedList l1 = new LinkedList();  
      l1.insertatend(1);  
      l1.insertatend(2);  
      l1.insertatend(3);  
      l1.insertAtBeg(9);  
      l1.size();  
      l1.display();  
    }  
} 
```
# Insert Methods
#### Insert at beginning 
```java
        void insertAtBeg(int val){  
            Node temp = new Node(val);  
            if(head==null){  
                head = temp;  
                tail = temp;  
            }else{  
                temp.next = head;  
                head = temp;  
            }  
        }  
```

#### Insert at any index
![[Pasted image 20260205002624.png]]
```java
// insert at Anyindex  
void insertatAnyIndex(int index , int val){  
     Node first = new Node(val);  
     Node temp = head;  
     while(temp.next.data!=index){  
           temp = temp.next;  
     }  
     first.next = temp.next;  
     temp.next = first;  
}
```

## Get Element Methods
![[Pasted image 20260205185411.png]]
```java
// you can get value at any index  
int getAt(int idx)  
{
  if(idx<0||idx>size()){  
        return -1;}  
    Node temp = head;  
    for(int i=0; i<idx; i++){  
        temp = temp.next;  
    } return temp.data; 
}
```

## Delete Node at any given index
![[Pasted image 20260205194556.png]]
```java
// to delete Node at any Index  
void DeleteAtindex(int idx) {  
    Node temp = head;  
    if (idx < 0 || idx > size) {  
        return;  
    }  
// if the Node is to be removed is 0 indexed so you have to modify the value of head
    if(idx==0){
      head = temp.next;
      temp.next = null;
      size--;
      return; 
    }
// for other indexes
    for (int i = 0; i < idx-1; i++) {  
        temp = temp.next;  
    }  
    temp.next = temp.next.next;
    tail = temp;  
    size--; 
// Whenever you are Deleting the Node you have to decrease the size by one  
}
```
- index 0

## Evident limitations of the linked List

## Detect loop in Linked List 
![[Pasted image 20260206235515.png]]
- using Slow and Fast pointer
#note [It is not Neccessary that slow and fast both the pointers meet at the node that starts the cycle they can meet at any node after cycle starts.]
```java
class Solution {
    public boolean detectLoop(Node head) {
        // code here
        Node slow = head;
        Node fast = head;
        while(fast!=null&&fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(fast==slow)
             return true;
        }
        return false;
    }
}
```
![[Pasted image 20260207002800.png]]
- you have to take a base pointer at  head and move the base and slow pointer after the slow and fast pointer met at a Node so when base and start meet at any point that point is  going to be the Cycle start pointer.  
```java
class Solution {
    public int cycleStart(Node head) {
        // code here
        Node slow = head;
        Node fast = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow==fast){
                Node base = head;
                while(base!=slow){
                    slow = slow.next;
                    base = base.next;
                }
                return base.data;
            }
        }
        return -1;
    }
}
```
## Merge Sort on Linked List
- you just have to divide the list on the basis of middle node using slow and fast pointer and then put slow.next to null to divide in half then again divide and give base condition to head.next == null them after dividing merge the lists 
- merge the list and return back using dummy node and two pointer i and j
```java
class Solution {
    public Node mergeSort(Node head) {
        // code here
        if(head.next==null){
            return head;
        }
        Node slow = head;
        Node fast = head;
        while(fast.next!=null && fast.next.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        Node head2 = slow.next;
        slow.next= null; // you are breaking the linkedlist into two halfs
        Node half1 = mergeSort(head);
        Node half2 = mergeSort(head2);
        return merge(half1,half2);
    }
    Node merge(Node list1 , Node list2){
          Node i = list1;
          Node j = list2;
          Node dummy = new Node(-1);
          Node k = dummy;
          while(i!=null&&j!=null){
              if(i.data == j.data){
                  k.next = i;
                  i = i.next;
              }
              else if(i.data<j.data){
                  k.next = i;
                  i = i.next;
              }
              else{
                  k.next = j;
                  j = j.next;
              }
              k = k.next;
         }
    if(i==null){
        k.next = j;
    }
    else{
        k.next = i;
    }
    return dummy.next;
    }
}
```
