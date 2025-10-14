给你链表的头结点 head ，请将其按 升序 排列并返回 排序后的链表 。

```
class Solution {
    public ListNode sortList(ListNode head) {
        if(head==null||head.next==null)return head;
        ListNode fast = head.next, slow = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode temp = slow.next;
        slow.next = null;
        ListNode left = sortList(head);
        ListNode right = sortList(temp);
        ListNode newHead = new ListNode();
        ListNode resList = newHead;
        while(left!=null&&right!=null){
            if(left.val<right.val){
                newHead.next = left;
                left = left.next;
            }else{
                newHead.next = right;
                right = right.next;
            }
            newHead = newHead.next;
        }
        newHead.next = left != null ? left : right;
        return resList.next;
    }
}
```
