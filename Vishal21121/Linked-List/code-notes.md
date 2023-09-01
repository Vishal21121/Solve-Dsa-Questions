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
