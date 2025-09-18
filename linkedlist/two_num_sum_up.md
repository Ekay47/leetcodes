给你两个 非空 的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储 一位 数字。

请你将两个数相加，并以相同形式返回一个表示和的链表。

你可以假设除了数字 0 之外，这两个数都不会以 0 开头。

这题思路很简单，就是一位一位做模拟，但就是要注意的情况比较繁杂：两条链一样长？不一样长？结束的位置？val和cache更新一定要用临时变量，不然会出现经典的hazard

```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int cache = 0;
        ListNode head = l1;
        int add;
        while (l1.next != null && l2.next != null) {
            add = l1.val + l2.val + cache;
            l1.val = add % 10;
            cache = add / 10;
            l1 = l1.next;
            l2 = l2.next;
        }
        add = l1.val + l2.val + cache;
        l1.val = add % 10;
        cache = add / 10;
        if (l1.next == null && l2.next == null) {
            if (cache == 1) {
                l1.next = new ListNode(1);
            }
            return head;
        }
        if (l2.next != null) {
            l1.next = l2.next;
        }
        while (l1.next != null) {
            l1 = l1.next;
            add = l1.val + cache;
            l1.val = add % 10;
            cache = add / 10;
        }
        if (cache == 1) {
            l1.next = new ListNode(1);
        }
        return head;
    }
}
```
