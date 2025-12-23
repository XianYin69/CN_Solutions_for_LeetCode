# 力扣题库 - 相交链表
## 想法
- 这里使用迭代
## Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        if not headA or not headB:
            return None
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
### 复杂度
- 时间复杂度：O(N),执行时间：143ms
- 空间复杂度：O(1),消耗内存：31.88MB
## C
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    if (headA == NULL || headB == NULL) {
        return NULL;
    }
    struct ListNode* pA = headA;
    struct ListNode* pB = headB;
    while (pA != pB) {
        pA = pA == NULL ? headB : pA -> next;
        pB = pB == NULL ? headA : pB -> next;
    }
    return pA;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：71ms
- 空间复杂度：O(1),消耗内存：22.57MB
## Java
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        ListNode pa = headA;
        ListNode pb = headB;
        while (pa != pb) {
            pa = (pa == null) ? headB : pa.next;
            pb = (pb == null) ? headA : pb.next;
        }
        return pa;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：1ms
- 空间复杂度：O(1),消耗内存：52.02MB