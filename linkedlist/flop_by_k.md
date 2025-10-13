给你链表的头节点 head ，每 k 个节点一组进行翻转，请你返回修改后的链表。

k 是一个正整数，它的值小于或等于链表的长度。如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。

你不能只是单纯的改变节点内部的值，而是需要实际进行节点交换。

思路：找到长度为k的区间，进行内部翻转
、、、
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
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode now = dummy;
        ListNode pre = now;
        while(now.next!=null){
            for(int i=1;i<=k&now!=null;i++){
                now = now.next;
            }
            if(now==null)break;
            ListNode begin = pre.next;
            ListNode end = now.next;
            now.next = null;
            pre.next = reverse(begin);
            begin.next = end;
            pre = begin;
            now = pre;
        }
        return dummy.next;
    }

    public ListNode reverse(ListNode head){
        ListNode pre = null;
        ListNode now = head;
        while(now!=null){
            ListNode next = now.next;
            now.next = pre;
            pre = now;
            now = next;
        }
        return pre;
    }
}
、、、
