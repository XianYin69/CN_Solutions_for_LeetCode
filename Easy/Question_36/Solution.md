# 力扣题库 - 多数元素
## 想法
- 这里是使用AI推荐的“投票算法” 反正就类似于计算权重啦，还是带点贪心算法的那种。
## Python
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        candidate = None
        for num in nums:
            if count == 0:
                candidate = num
            count += (1 if num == candidate else -1)
        return candidate
```
### 复杂度
- 时间复杂度：O(N),执行时间：3ms
- 空间复杂度：O(1),消耗内存：19.05MB
## C
```c
int majorityElement(int* nums, int numsSize) {
    int count = 0;
    int candidate;
    for (int i = 0; i < numsSize; i++) {
        if (count == 0) {
            candidate = nums[i];
        }
        count = candidate == nums[i] ? count + 1 : count - 1;
    }
    return candidate;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：10.10MB
## Java
```java
class Solution {
    public int majorityElement(int[] nums) {
        int candidate = nums[0];
        int count = 1;
        for (int i = 1; i < nums.length; i++) {
            if (count == 0) {
                candidate = nums[i];
                count = 1;
            } else {
                count += (nums[i] == candidate) ? 1 : -1;
            }
        }
        return candidate;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：2ms
- 空间复杂度：O(1),消耗内存：54.59MB