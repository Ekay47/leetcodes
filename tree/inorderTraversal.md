给定一个二叉树的根节点 root ，返回 它的 中序 遍历 。
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        Deque<TreeNode> stack = new ArrayDeque<>();
        while(root!=null||!stack.isEmpty()){
            if(root!=null){
                stack.push(root);
                root = root.left;
            }else{
                root = stack.pop();
                ans.add(root.val);
                root = root.right;
            }
        }
        return ans;
    }
}
```
