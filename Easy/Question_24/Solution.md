# 力扣题库 - 二叉树的最小深度
## 想法
- 这里我最先想到的是DSF（深度优先搜索）但是逻辑上稍微有点问题
## Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if root == None:
            return 0
        leftDepth = self.minDepth(root.left)
        rightDepth = self.minDepth(root.right)
        if root.left == None:
            return rightDepth + 1
        elif root.right == None:
            return leftDepth + 1
        else:
            return 1 + min(leftDepth, rightDepth)
```
### 复杂度
- 时间复杂度：O(N),执行时间：80ms
- 空间复杂度：O(H),消耗内存：49.26MB
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
int minDepth(struct TreeNode* root) {
    if (root == NULL) {
        return 0;
    }
    int leftDepth = minDepth(root -> left);
    int rightDepth = minDepth(root -> right);
    if (root -> left == NULL) {
        return 1 + rightDepth;        
    } else if (root -> right == NULL) {
        return 1 + leftDepth;
    } else {
        return 1 + (leftDepth < rightDepth ? leftDepth : rightDepth);
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：16ms
- 空间复杂度：O(H),消耗内存：78.66MB
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
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int leftDepth = minDepth(root.left);
        int rightDepth = minDepth(root.right);
        if (root.left == null) {
            return 1 + rightDepth;
        } else if (root.right == null) {
            return 1 + leftDepth;
        } else {
            return 1 + Math.min(leftDepth, rightDepth);
        }
    } 
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：8ms
- 空间复杂度：O(H),消耗内存：80.43MB