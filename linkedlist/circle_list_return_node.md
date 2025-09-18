定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

解题思路：还是快慢指针先找有没有环，没找到就返回null；设置a=入环前的步数，b=环的长度
技巧点在于，fast = 2 slow = slow + nb（能相遇是因为fast多走了整数圈） => slow = nb 如果slow想要到入口，需要走a + nb
观察nb 和 a + nb 可以知道，其实再走a步，slow就可以达到入口节点，如何确定a呢？找一个新的从head出发的节点，和slow一起走，相遇的时候就是入口
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if(head == null||head.next == null) return null;
        ListNode slow = head.next, fast = head.next.next;
        while(slow!=fast){
            if(fast==null||fast.next==null)return null;
            fast = fast.next.next;
            slow = slow.next;
        }
        ListNode tmp = head;
        while(slow!=tmp){
            slow = slow.next;
            tmp = tmp.next;
        }
        return slow;
    }
}
```
