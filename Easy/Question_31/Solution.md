# 力扣题库 - 环形列表
## 想法
## Python
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        # 边界条件：空链表、单节点、双节点且无环，直接返回 False
        if not head or not head.next:
            return False
        
        slow = head
        fast = head.next # 让快指针先走一步，避免一开始就相等
        
        while fast and fast.next:
            if slow == fast: # 如果相遇，说明有环
                return True
            slow = slow.next
            fast = fast.next.next
            
        return False # 循环结束，快指针触及 None，说明无环
```
### 复杂度
- 时间复杂度：O(N),执行时间：51ms
- 空间复杂度：O(1),消耗内存：18.96MB
## C
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {
    // 1. Correct boundary condition: 
    // An empty list or a list with only one node (and no self-loop) cannot have a cycle.
    if (head == NULL || head->next == NULL) {
        return false;
    }

    // 2. Declare pointers correctly (using '*' for pointer variables)
    struct ListNode *slow = head;
    struct ListNode *fast = head->next; // Start fast one step ahead of slow

    // 3. Main loop:
    // We only need to check if 'fast' and 'fast->next' are not NULL. 
    // If they become NULL, we exit the loop and return false (no cycle).
    while (fast != NULL && fast->next != NULL) {
        // Check for collision *before* moving pointers for this starting configuration
        if (slow == fast) {
            return true; // Pointers met, a cycle is detected
        }

        // Move the pointers
        slow = slow->next;        // Slow moves 1 step
        fast = fast->next->next;  // Fast moves 2 steps
    }

    // If the loop finishes without collision, fast pointer reached the end of the list
    return false;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：11ms
- 空间复杂度：O(1),消耗内存：11.04MB
## Java
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        
        // Initialize fast and slow differently
        ListNode slow = head;
        ListNode fast = head.next;
        
        while (fast != null && fast.next != null) {
            // Move first, then check collision
            slow = slow.next;
            fast = fast.next.next;
            
            if (slow == fast) {
                return true;
            }
        }
        
        return false;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：46.07MB