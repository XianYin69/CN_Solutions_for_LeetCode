# 力扣题库 - 二叉树的前序遍历
## 想法
## Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        def traverse(node):
            if not node:
                return
            res.append(node.val)
            traverse(node.left)
            traverse(node.right)
        traverse(root)
        return res
        
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：16.92MB
## C
```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 * int val;
 * struct TreeNode *left;
 * struct TreeNode *right;
 * };
 */

// 辅助函数：执行递归遍历
void traverse(struct TreeNode* root, int* res, int* returnSize) {
    if (root == NULL) return;
    
    // 根 -> 左 -> 右
    res[(*returnSize)++] = root->val;
    traverse(root->left, res, returnSize);
    traverse(root->right, res, returnSize);
}

int* preorderTraversal(struct TreeNode* root, int* returnSize) {
    // 预分配内存（题目节点数通常不超过 100，实际开发中可根据需求动态调整）
    int* res = (int*)malloc(sizeof(int) * 100);
    *returnSize = 0;
    
    traverse(root, res, returnSize);
    return res;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：8.50MB
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
        private void traverse(TreeNode node, List<Integer> res) {
            if (node == null) return;
            res.add(node.val);
            traverse(node.left, res);
            traverse(node.right, res);
        }
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        traverse(root, res);
        return res;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：42.59MB