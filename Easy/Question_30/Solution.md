# 力扣题库 - 只出现一次的数字
## 想法
- 采用异或算法
## Python
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        def recurse(index, current_xor):
            if index == len(nums):
                return current_xor
            return recurse(index + 1, current_xor ^ nums[index])
        return recurse(0, 0)
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：24.36MB
## C
```c
int singleNumber(int* nums, int numsSize) {
    int res = 0;
    for (int i = 0; i < numsSize; i = i + 1) {
        res ^= nums[i];
    }
    return res;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：9.50MB
## Java
```java
class Solution {
    public int singleNumber(int[] nums) {
        int res = 0;
        for (int i = 0; i < nums.length; i = i + 1) {
            res ^= nums[i];
        }
        return res;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：1ms
- 空间复杂度：O(1),消耗内存：46.16MB