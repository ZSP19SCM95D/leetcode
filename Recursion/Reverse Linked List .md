### Reverse Linked List

Reverse a singly linked list.

**Example:**

```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```



### 迭代

~~~java
//iteratively
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        while(cur!=null){
            ListNode next = cur.next;
            cur.next = pre;
            pre = cur;
            cur = next;
        }
        return pre;  
        
    }
}
~~~



### 递归

~~~java
//recursively

class Solution {
    public ListNode reverseList(ListNode head) {
        while(head==null || head.next ==null){
            return head;
        }
        ListNode p =reverseList(head.next);
        head.next.next = head;
        head.next = null
        
        return p;
    }
}
~~~

