请你设计并实现一个满足  LRU (最近最少使用) 缓存 约束的数据结构。
实现 LRUCache 类：
LRUCache(int capacity) 以 正整数 作为容量 capacity 初始化 LRU 缓存
int get(int key) 如果关键字 key 存在于缓存中，则返回关键字的值，否则返回 -1 。
void put(int key, int value) 如果关键字 key 已经存在，则变更其数据值 value ；如果不存在，则向缓存中插入该组 key-value 。如果插入操作导致关键字数量超过 capacity ，则应该 逐出 最久未使用的关键字。
函数 get 和 put 必须以 O(1) 的平均时间复杂度运行。

```
class LRUCache {

    private static class Node{
        int key, val;
        Node prev, next;

        Node(int k, int v){
            key = k;
            val = v;
        }
    }

    private final int capacity;
    private final Node dummy = new Node(0,0);
    private final Map<Integer, Node> keyToNode = new HashMap<>();

    public LRUCache(int capacity) {
        this.capacity = capacity;
        dummy.prev = dummy;
        dummy.next = dummy;
    }
    
    public int get(int key) {
        Node node = getNode(key);
        return node != null ? node.val : -1;
    }
    
    public void put(int key, int value) {
        Node node = getNode(key);
        if(node != null){
            node.val = value;
            return;
        }
        node = new Node(key, value);
        keyToNode.put(key, node);
        pushFront(node);
        if(keyToNode.size()>capacity){
            Node endNode = dummy.prev;
            keyToNode.remove(endNode.key);
            remove(endNode);
        }
    }

    private Node getNode(int key){
        if(!keyToNode.containsKey(key)){
            return null;
        }
        Node node = keyToNode.get(key);
        remove(node);
        pushFront(node);
        return node;
    }

    private void remove(Node n){
        n.prev.next = n.next;
        n.next.prev = n.prev;
    }

    private void pushFront(Node n){
        n.prev = dummy;
        n.next = dummy.next;
        n.prev.next = n;
        n.next.prev = n;
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```
