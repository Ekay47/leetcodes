给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

双指针，用一个dummyhead作为头节点的前一个节点，在用一个指针去找间隔为n的位置

```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode temp = head;
        ListNode dummyHead = new ListNode();
        dummyHead.next = head;
        for(int i=1;i<n;i++){
            temp = temp.next;
        }
        ListNode now = dummyHead;
        while(temp.next!=null){
            now = now.next;
            temp = temp.next;
        }
        now.next = now.next.next;
        return dummyHead.next;
    }
}
```
