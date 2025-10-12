给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。

依旧双指针，一前一后和dummy开始的位置节点做操作
```
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode();
        dummy.next = head;
        if(dummy.next==null||dummy.next.next==null)return head;
        ListNode pre, post, now = dummy;
        while(now.next!=null && now.next.next!=null){
            pre = now.next;
            post = pre.next;
            now.next = post;
            pre.next = post.next;
            post.next = pre;
            now = pre;
        }
        return dummy.next;
    }
}
```
