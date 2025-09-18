给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。

用两个指针，prev和next，分别指明null和head，然后往后一路交换

```
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null, nxt = head;
        if(nxt==null)return nxt;
        while(nxt!=null){
            ListNode tmp = nxt;
            nxt = nxt.next;
            tmp.next = prev;
            prev = tmp;
        }
        return prev;
    }
}
```
