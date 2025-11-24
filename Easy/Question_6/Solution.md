# 力扣题库 - 合并两个有序链表
## 想法
- 这题使用递归（AI 说的），但是我第一想到是创建一个新数组然后迭代
## Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
from typing import Optional
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if not list1:
            return list2
        if not list2:
            return list1
        
        if list1.val < list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(1)O(1),消耗内存：17.73MB
## C
```c
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    if (list1 == NULL) {
        return list2;
    }
    if (list2 == NULL) {
        return list1;
    }
    if (list1->val < list2->val) {
        list1->next = mergeTwoLists(list1->next, list2);
        return list1;
    } else {
        list2->next = mergeTwoLists(list1, list2->next);
        return list2;
    }
}

```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(N)O(N),消耗内存：10.51MB
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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 == null) {
            return list2;
        }
        
        if (list2 == null) {
            return list1;
        }

        if (list1.val < list2.val) { 
            list1.next = mergeTwoLists(list1.next, list2);
            return list1;
        } else {
            list2.next = mergeTwoLists(list1, list2.next);
            return list2;
        }
    }
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(N)O(N),消耗内存：43.39MB