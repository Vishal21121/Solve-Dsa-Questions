# LinkedList

### Question-1

- [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

- topic - `LinkedList`

- #### Approach

  - We have to return a LinkedList in which there are no repeated elements.
  - In this approach I am using a pointer for unique elements (`unique`) and one pointer (`temp`) for iterating the linked list.
  - Initially I am taking the first element as unique element and then iterating till we get element where `unique.val!=temp.val` then I am pointing the next of the unique node to this node and then shifting the unique pointer to this node and I am iterating until we reach the end of the LinkedList
  - At the end I am checking whether the LinkedList is empty or not if its not empty then I am setting `unique.next` to `null` so that our LinkedList will be from head to node where unique is pointing to.

- #### Code

```java
    /**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode unique = head;
        ListNode temp = head;
        while(temp!=null){
            if(temp.val != unique.val){
                unique.next = temp;
                unique = temp;
            }
            temp = temp.next;
        }
        if(head!=null){
            unique.next = null;
        }
        return head;
    }
}
```

### Question-2

- [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

- topic - `LinkedList`

- #### Approach

  - We have to return a LinkedList with two sorted LinkedList merged together.
  - We will iterate each LinkedList until `list1!=null` and `list2!=null` and check if `list1.val < list2.val` then add the `list1` else add `list2` and at the end one of LinkedList will be traversed fully and one will be left.
  - Add the left LinkedList `temp.next = (list1!=null) ? list1 : list2;`

- #### Code

```java
    /**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode LL = new ListNode();
        ListNode temp = LL;
        while(list1!=null && list2!=null){
            if(list1.val <= list2.val){
                temp.next = list1;
                list1 = list1.next;
                temp = temp.next;
            }else{
                temp.next = list2;
                list2 = list2.next;
                temp = temp.next;
            }
        }
        temp.next = (list1!=null) ? list1 : list2;
        return LL.next;
    }
}
```

### Question-3

- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

- topic - `LinkedList`

- #### Approach

  - We need to find whether there is cycle in the LinkedList
  - We are using **fast-slow pointer method**
  - In the fast-slow-pointer method fast pointer moves by two position while slow pointer moves by one position.
  - And in this way fast and slow pointer will meet each other if there is cycle in the LinkedList.
  - So we are iterating till `fast!=null` and `fast.next!=null` if this condition breaks means fast is at tha last Node.
  - If the above condition does not break then we are moving fast by two position and slow pointer moves by one position and if they meet each other means we got the cycle.

- #### Code

```java
   /**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
    // This method is known as fast and slow pointer method
       ListNode fast = head;
       ListNode slow = head;

       // we are having this condition to check that fast is pointing to last node of linked list. If yes then break
       while(fast!=null && fast.next!=null){
           fast = fast.next.next;
           slow = slow.next;
           if(fast==slow){
               return true;
           }
       }
       return false;
    }
}
```

### Note:

- Time complexity: O(n)
- Space complexity: O(1)

### Question-4

- [Find length of Loop](https://practice.geeksforgeeks.org/problems/find-length-of-loop/1)

- topic - `LinkedList`

- #### Approach

  - We need to find whether there is cycle in the LinkedList
  - We are using **fast-slow pointer method**
  - In the fast-slow-pointer method fast pointer moves by two position while slow pointer moves by one position.
  - And in this way fast and slow pointer will meet each other if there is cycle in the LinkedList.
  - So we are iterating till `fast!=null` and `fast.next!=null` if this condition breaks means fast is at tha last Node.
  - If the above condition does not break then we are moving fast by two position and slow pointer moves by one position and if they meet each other means we got the cycle.
  - At this point slow and fast pointer points to the same node, now we will run the slow pointer till it comes back to this position and we will count the length.
  - In this way we will get the length of the loop.

- #### Code

```java
  //{ Driver Code Starts
// driver code

import java.util.*;
import java.io.*;
import java.lang.*;

class Node
{
    int data;
    Node next;

    Node(int x)
    {
        data = x;
        next = null;
    }
}

class GFG
{
    public static void makeLoop(Node head, Node tail, int x){
        if (x == 0) return;

        Node curr = head;
        for(int i=1; i<x; i++)
            curr = curr.next;

        tail.next = curr;
    }

    public static void main (String[] args){
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while(t--> 0)
        {
            int n = sc.nextInt();

            int num = sc.nextInt();
            Node head = new Node(num);
            Node tail = head;

            for(int i=0; i<n-1; i++)
            {
                num = sc.nextInt();
                tail.next = new Node(num);
                tail = tail.next;
            }

            int pos = sc.nextInt();
            makeLoop(head, tail, pos);

            Solution x = new Solution();
            System.out.println( x.countNodesinLoop(head) );
        }
    }
}

// } Driver Code Ends


/*

class Node
{
    int data;
    Node next;
    Node(int d) {data = d; next = null; }
}

*/

//Function should return the length of the loop in LL.

class Solution
{
    //Function to find the length of a loop in the linked list.
    static int countNodesinLoop(Node head)
    {
        // This method is known as fast and slow pointer method
       Node fast = head;
       Node slow = head;

       // we are having this condition to check that fast is pointing to last node of linked list. If yes then break
       while(fast!=null && fast.next!=null){
           fast = fast.next.next;
           slow = slow.next;
           if(fast==slow){
                int length = 0;
                do{
                    slow = slow.next;
                    length++;
                }while(slow!=fast);
                return length;
           }
       }
       return 0;
    }
}
```

### Note:

- Time complexity: O(n)
- Space complexity: O(1)

### Question-5

- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

- topic - `LinkedList`

- #### Approach
- Initialize two pointers, fast and slow, both pointing to the head of the linked list.
- Move fast two steps at a time and slow one step at a time until they meet or the end of the list is reached.
  If there is no cycle, return null.
- Calculate the length of the cycle by moving slow one step at a time until it meets fast again, incrementing a counter for each step.
- Move slow and fast back to the head of the list, and then move slow ahead by the size of the loop and then move both fast and slow pointers one step at a time until they meet again and this point is the start of the loop so return this node of the cycle.

- #### Code

```java
    /**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        int count = 0;
        while(fast!=null && fast.next != null){
            fast=fast.next.next;
            slow = slow.next;
            if(fast==slow){
                do{
                    slow = slow.next;
                    count++;
                }while(slow!=fast);
                break;
            }
        }
        if(count==0){
            return null;
        }
        slow = head;
        fast = head;

        for(int i=1;i<=count;i++){
            slow = slow.next;
        }
        while(fast!=slow){
            fast=fast.next;
            slow = slow.next;
        }
        return fast;
    }
}
```

#### Note:

- Time complexity: O(n)
- Space complexity: O(1)

### Question-6

- [Happy Number](https://leetcode.com/problems/happy-number/)

- topic - `LinkedList`

- #### Approach

1. The isHappy(int n) method is the main method that checks if a given integer n is a Happy Number. It uses the Floyd Cycle detection algorithm (also known as the "tortoise and the hare" algorithm) to detect if there's a cycle in the sequence of sums of squares of digits.

- Two pointers, slow and fast, are initialized to the input number n.
- In a loop, slow is replaced by the sum of squares of its digits, while fast is replaced twice (this is why it's "faster").
- If at any point slow equals fast, it means a cycle is detected.
- If the cycle is at 1 (i.e., slow==1), then the number is a Happy Number and the method returns true. If not, it returns false tutorialstonight.com.

2. The findSquare(int num) method is a helper method that calculates and returns the sum of the squares of the digits of a given number num.

- It initializes a sum (ans) to 0.
- Then in a loop, it calculates the remainder of num divided by 10 (which gives the last digit), squares it, and adds it to ans.
- num is then divided by 10 to remove the last digit.
- This process continues until num becomes 0, at which point ans is returned

- #### Code

```java
    class Solution {
    public boolean isHappy(int n) {
        int slow = n;
        int fast = n;
        do{
            slow = findSquare(slow);
            fast = findSquare(findSquare(fast));
        }while(slow!=fast);
        if(slow==1){
            return true;
        }
        return false;
    }
    static int findSquare(int num){
        int ans = 0;
        while(num>0){
            int rem = num % 10;
            ans += rem * rem;
            num/= 10;
        }
        return ans;
    }
}
```

#### Note:

- Time complexity: O(n)
- Space complexity: O(1)

### Question-7

- [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

- topic - `LinkedList`

- #### Approach

1. The middleNode(ListNode head) method is the main method that finds the middle node of a linked list.

- It initializes two pointers, slow and fast, to the head of the list.
- Then, in a loop, slow moves one step at a time while fast moves two steps at a time.
- The loop continues until fast reaches the end of the list or has no next node.
- When the loop ends, slow will be at the middle of the list, so it is returned as the middle node

2. The ListNode class is a definition for a node in a singly linked list.

- Each ListNode has an integer value (val) and a reference to the next ListNode (next).
- There are three constructors: a default constructor, a constructor that takes a value, and a constructor that takes a value and a next node

- #### Code

```java
    /**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```

#### Note:

- Time complexity: O(n)
- Space complexity: O(1)
