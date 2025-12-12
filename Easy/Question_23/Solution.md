# 力扣题库 - 平衡二叉树
## 想法
- 这里是官方的自上而下的解法
## Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def height(root: TreeNode) -> int:
            if not root:
                return 0
            return max(height(root.left), height(root.right)) + 1

        if not root:
            return True
        return abs(height(root.left) - height(root.right)) <= 1 and self.isBalanced(root.left) and self.isBalanced(root.right)
```
### 复杂度
- 时间复杂度：O(N),执行时间：11ms
- 空间复杂度：O(H),消耗内存：18.59MB
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
bool isBalanced(struct TreeNode* root) {
    int checkDepth(struct TreeNode* root) {
        if (root == NULL) {
            return 0;
        } else {
            return fmax(checkDepth(root -> left), checkDepth(root -> right)) + 1;
        }
    }

    if (root == NULL) {
        return true;
    } else {
        return fabs(checkDepth(root->left) - checkDepth(root->right)) <= 1 && isBalanced(root->left) && isBalanced(root->right);
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：3ms
- 空间复杂度：O(H),消耗内存：12.23MB
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
    public boolean isBalanced(TreeNode root) {
        if (root == null) {
            return true;
        } else {
            return Math.abs(height(root.left) - height(root.right)) <= 1 && isBalanced(root.left) && isBalanced(root.right);
        }
    }

    public int height(TreeNode root) {
        if (root == null) {
            return 0;
        } else {
            return Math.max(height(root.left), height(root.right)) + 1;
        }
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：1ms
- 空间复杂度：O(H),消耗内存：44.84MB