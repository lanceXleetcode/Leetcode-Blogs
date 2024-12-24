513.找树左下角的值
```Java
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
    public int findBottomLeftValue(TreeNode root) {
        Deque<TreeNode> queue = new LinkedList<TreeNode>();
        if(root==null)return 0;
        boolean b;
        queue.offer(root);
        if(root.left==null && root.right==null)return root.val;
        while(queue.size()!=0){
            int size = queue.size();
            b = false;
            for(int i=0;i<size;i++){
                TreeNode node = queue.poll();
                if(node.left!=null){
                    queue.offer(node.left);
                    if(node.left.left!=null || node.left.right!=null)b=true;
                }

                if(node.right!=null){
                    queue.offer(node.right);
                    if(node.right.left!=null || node.right.right!=null)b=true;
                }
            }
            if(!b){
                return queue.poll().val;
            }
        }
        return 0;
    }
}
```

112.路经总和
```Java
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
    public boolean hasPathSum(TreeNode root, int targetSum) {
        return dfs(root, targetSum, 0);
    }

    boolean dfs(TreeNode root, int targetSum, int value){
        if(root==null)return false;
        value+=root.val;
        if(root.left==null && root.right==null){
            if(value==targetSum)return true;
        }
        return dfs(root.left, targetSum, value) || dfs(root.right, targetSum, value);
    }
}
```

106.中序后序构建二叉树
