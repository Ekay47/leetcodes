给你一个单链表的头节点 head ，请你判断该链表是否为回文链表。如果是，返回 true ；否则，返回 false 。

通过快慢双指针，找到mid，将mid以后的节点翻转，然后从两头开始依次做判断

class Solution {
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null)return true;
        ListNode slow = head, fast = head;
        while(fast.next!=null && fast.next.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode head2 = reverseList(slow.next);
        ListNode n1 = head, n2 = head2; 

        while(n2!=null){
            if(n1.val!=n2.val)return false;
            n1 = n1.next;
            n2 = n2.next;
        }

        return true;
    }

    private ListNode reverseList(ListNode head){
        ListNode prev = null, curr = head;
        while(curr!=null){
            ListNode tmp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = tmp;
        }
        return prev;
    }
}
