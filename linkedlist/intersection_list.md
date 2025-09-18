给你两个单链表的头节点 headA 和 headB ，请你找出并返回两个单链表相交的起始节点。如果两个链表不存在相交节点，返回 null 。

把两条链拼起来，一路比下去能在同样的长度找到相交节点
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null){
            return null;
        }
        ListNode tA = headA, tB = headB;
        while(tA!=tB){
            tA = tA == null ? headB : tA.next;
            tB = tB == null ? headA : tB.next;
        }
        return tA;
    }
}
```
