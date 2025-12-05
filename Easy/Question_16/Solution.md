# 力扣题库 - 删除排序链表中的重复元素
## 想法
- 我原本想用递归来解决这题，但是可能会出现未预测的行为，故采用迭代来解决
## Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        current = head
        while current and current.next:
            if current.val == current.next.val:
                current.next = current.next.next
            else:
                current = current.next
        return head
```
### 复杂度
- 时间复杂度：O(N),执行时间0ms
- 空间复杂度：O(1),消耗内存：17.74MB
## C
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* deleteDuplicates(struct ListNode* head) {
    if (head == NULL) {
        return NULL;
    }
    struct ListNode* current = head;
    while (current != NULL && current -> next != NULL) {
        if (current -> val == current -> next -> val) {
            current -> next = current -> next -> next;
        }
        else {
            current = current -> next;
        }
    }
    return head;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：11.08MB
## Java
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) {
            return null;
        }
        ListNode current = head;
        while (current != null && current.next != null) {
            if (current.val == current.next.val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        return head;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：44.56MB