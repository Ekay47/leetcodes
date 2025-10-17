给你一个链表数组，每个链表都已经按升序排列。

请你将所有链表合并到一个升序链表中，返回合并后的链表。

```
class Solution {
    class Status implements Comparable<Status> {
        int val;
        ListNode node;

        Status(int val, ListNode node) {
            this.val = val;
            this.node = node;
        }

        public int compareTo(Status status2) {
            return this.val - status2.val;
        }
    }

    PriorityQueue<Status> queue = new PriorityQueue<Status>();

    public ListNode mergeKLists(ListNode[] lists) {
        for (ListNode node : lists) {
            if (node != null) {
                queue.offer(new Status(node.val, node));
            }
        }
        ListNode head = new ListNode(0);
        ListNode tail = head;
        while (!queue.isEmpty()) {
            Status s = queue.poll();
            tail.next = s.node;
            tail = tail.next;
            if (s.node.next != null) {
                queue.offer(new Status(s.node.next.val, s.node.next));
            }
        }
        return head.next;
    }
}
```
