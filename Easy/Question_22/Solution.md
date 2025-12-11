# 力扣题库 - 将有序数组转换为二叉搜索树
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
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        def buildTree(left, right):
            if left > right:
                return None
            mid = (left + right) // 2
            root = TreeNode(nums[mid])
            root.left = buildTree(left, mid - 1)
            root.right = buildTree(mid + 1, right)
            return root
        return buildTree(0, len(nums) - 1)
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(H),消耗内存：18.63MB
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
struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    struct TreeNode* buildTree(int* nums, int left, int right) {
        if (left > right) {
            return NULL;
        }
        int mid = (left + right) / 2;
        struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
        if (root == NULL) {
            exit(1);
        }
        root -> val = nums[mid];
        root -> left = buildTree(nums, left, mid - 1);
        root -> right = buildTree(nums, mid + 1, right);
        return root;
    }
    return buildTree(nums, 0, numsSize - 1);
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：7ms
- 空间复杂度：O(H),消耗内存：15.54MB
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
    public TreeNode sortedArrayToBST(int[] nums) {
        return buildTree(nums, 0, nums.length - 1);
    }
    private TreeNode buildTree(int[] nums, int left, int right) {
        if (left > right) {
            return null;
        }
        int mid = (left + right) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = buildTree(nums, left, mid - 1);
        root.right = buildTree(nums, mid + 1, right);
        return root;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(H),消耗内存：44.41MB