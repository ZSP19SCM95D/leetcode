### Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

~~~java
public class Solution {
    
    public ListNode mergeTwoLists(ListNode l1, ListNode l2){
		if(l1 == null) return l2;
		if(l2 == null) return l1;
		if(l1.val < l2.val){
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		} else{
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
}
}
~~~

![image-20190729211751765](/Users/zhongzhuding/Library/Application Support/typora-user-images/image-20190729211751765.png)



**Algorithm**

We model the above recurrence directly, first accounting for edge cases. Specifically, if either of `l1` or `l2` is initially `null`, there is no merge to perform, so we simply return the non-`null` list. Otherwise, we determine which of `l1` and `l2` has a smaller head, and recursively set the `next` value for that head to the next merge result. Given that both lists are `null`-terminated, the recursion will eventually terminate.

