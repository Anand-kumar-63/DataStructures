
- 237 , 876 , Middle element GFG practice , 2095 delete middle element , Delete middle element GFG Practice , 19 , Delete element from the last , Kth from End of Linked List GFG practice , intersection of two LinkedList GFG practice , 160 ,  1721 (swap the LinkedList element) ,  141(cycle LinkedList - fast and slow pointer) , same GFG practice ,  83 remove duplicate node in a sorted LinkedList , Merge two sorted linkedList , 148 , 
## 237
```java 
class Solution {
    public void deleteNode(ListNode node) {
        // so what you have to do is to copy the value of the next element and not and then delete the next node the not the node given to us
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

## Middle Element gfg Practice 
you can find the middle element using slow and fast pointer
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while(fast!=null && fast.next!=null){
              slow = slow.next;
              fast = fast.next.next;
        }
        return slow;
    }
}
```

1721
![[Pasted image 20260206235106.png]]
83
![[Pasted image 20260207163026.png]]
82
Delete all the duplicate node and return the unique nodes
 - [Method] - you can create a dummy node and then use two pointers to check for the value of Current node and next to the Current node if they are same then move the step pointer util you find a situation where step pointer value and base pointer value don't match then  you can set the next pointer of dummy node to that node at which next pointer points  to   
![[Pasted image 20260207171822.png]]
21 
![[Pasted image 20260207231605.png]]
- you have to take i and j pointer to both lists and a dummy node to store the find node adresss
- then compare the i and j value iteratively and increase i and j and k accordingly 
- you have to handle the edge case that if both values are same then you have to manually increase the value of k.next to either i or j
- and after every increase you have to set the value of k to k.next
- then at last it might be possible that i or j becomes null and j or i remaining nodes needs connection to the k so you have to do it outside the while loop accordingly
```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode i = list1;
        ListNode j = list2;
        ListNode dummy = new ListNode(-1);
        ListNode k = dummy;
        while(i!=null && j!=null){
            if(i.val == j.val){
                 k.next = i;
                 i = i.next;
            }
            else if(i.val < j.val){
                k.next = i;
                i = i.next;
            }  
            else{
                k.next = j;
                j = j.next;
            }
            k = k.next;
        }
        // if i is null so connect k to j
        if(i==null)
        {k.next = j;}
        else
        {k.next = i;}
        return dummy.next;
    }
}
```
