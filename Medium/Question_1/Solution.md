# 力扣题库 - 两数之和
## 想法
## Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
from typing import Optional

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        virtHead = ListNode(0)
        current = virtHead
        carry = 0

        while l1 or l2 or carry:
            val1 = l1.val if l1 else 0
            val2 = l2.val if l2 else 0
            total = val1 + val2 + carry
            current_val = total % 10
            carry = total // 10
            current.next = ListNode(current_val)
            current = current.next
            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next
        
        return virtHead.next
```
### 复杂度
- 时间复杂度：0,执行时间：0ms
- 空间复杂度：0,消耗内存：17.55MB
## C
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode* virtHead = (struct ListNode*)malloc(sizeof(struct ListNode));
    virtHead->val = 0;
    virtHead->next = NULL;
    struct ListNode* current = virtHead;
    int carry = 0;
    while (l1 != NULL || l2 != NULL || carry != 0) {
        int val1 = (l1 != NULL) ? l1 ->val : 0;
        int val2 = (l2 != NULL) ? l2 ->val : 0;
        int total = val1 + val2 + carry;
        int currentVal = total % 10;
        carry = total / 10;

        struct ListNode* newNode = (struct ListNode*)malloc(sizeof(struct ListNode));
        newNode->val = currentVal;
        newNode->next = NULL;
        current->next = newNode;
        current = current->next;

        if (l1 != NULL) l1 = l1->next;
        if (l2 != NULL) l2 = l2->next;
    }

    struct ListNode* result = virtHead->next;
    free(virtHead);
    return result;
}
```
### 复杂度
- 时间复杂度：0,执行时间：3ms
- 空间复杂度：0,消耗内存：12.38MB
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode virtHead = new ListNode(0);
        ListNode current = virtHead;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int val1 = (l1 != null) ? l1.val : 0;
            int val2 = (l2 != null) ? l2.val : 0;
            int total = val1 + val2 + carry;
            int currentVal = total % 10;
            carry = total / 10;
            current.next = new ListNode(currentVal);
            current = current.next;
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
        }
        return virtHead.next;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：3ms
- 空间复杂度：O(N),消耗内存：45.65MB