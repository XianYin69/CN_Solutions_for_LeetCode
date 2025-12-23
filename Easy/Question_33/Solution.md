# 力扣题库 - 二叉树的后序遍历
## 想法
- 这里使用递归
## Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        def dfs(node):
            if not node:
                return
            dfs(node.left)
            dfs(node.right)
            res.append(node.val)
        dfs(root)
        return res
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：17.06MB
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
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* postorderTraversal(struct TreeNode* root, int* returnSize) {
    int* res = (int*)malloc(sizeof(int) * 100);
    *returnSize = 0;
    void helper(struct TreeNode* root, int* res, int* returnSize) {
        if (root == NULL) return;
        helper(root->left, res, returnSize);
        helper(root->right, res, returnSize);
        res[(*returnSize)++] = root->val;
    }
    helper(root, res, returnSize);
    return res;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：8.46MB
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
    private void helper(TreeNode node, List<Integer> res) {
        if (node == null) {
            return;
        }
        helper(node.left, res);
        helper(node.right, res);
        res.add(node.val);
    }
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        helper(root, res);
        return res;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：42.43MB