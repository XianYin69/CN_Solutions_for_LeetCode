# 力扣题库 - 二叉树中的遍历
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
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        retList = []
        def traversal(node):
            if node is None:
                return
            traversal(node.left)
            retList.append(node.val)
            traversal(node.right)
        traversal(root)
        return retList
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：17.43MB
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
int* inorderTraversal(struct TreeNode* root, int* returnSize) {
    void inorder(struct TreeNode* root, int* res, int* resSize) {
        if (!root) {
            return;
        }
        inorder (root -> left, res, resSize);
        res[(*resSize)++] = root -> val;
        inorder(root -> right, res, resSize);
    }

    int* res = malloc(sizeof(int) * 501);
    *returnSize = 0;
    inorder(root, res, returnSize);
    return res;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：8.52MB
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
    public void inorder(TreeNode root, List<Integer> res) {
    if (root == null) {
        return;
    }
        inorder(root.left, res);
        res.add(root.val);
        inorder(root.right, res);
    }
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        inorder(root, res);
        return res;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：42.64MB