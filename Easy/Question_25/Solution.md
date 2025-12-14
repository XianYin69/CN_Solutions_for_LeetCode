# 力扣题库 - 路径总和
## 想法
- 这里还是DFS
## Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        remainingSum = targetSum - root.val
        if not root.left and not root.right:
            return remainingSum == 0
        return self.hasPathSum(root.left, remainingSum) or self.hasPathSum(root.right, remainingSum)
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(H),消耗内存：18.82MB
## C
```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
bool hasPathSum(struct TreeNode* root, int targetSum) {
    if (root == NULL) {
        return false;
    }
    int remainingSum = targetSum - root->val;
    if (root->left == NULL && root->right == NULL) {
        return remainingSum == 0;
    }
    return hasPathSum(root->left, remainingSum) || hasPathSum(root->right, remainingSum);
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(H),消耗内存：11.29MB
## Java
```java
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
        if (root == null) {
            return false;
        }
        int remainingSum = targetSum - root.val;
        if (root.left == null && root.right == null) {
            return remainingSum == 0;
        }
        return hasPathSum(root.left, remainingSum) || hasPathSum(root.right, remainingSum);
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(H),消耗内存：44.32MB