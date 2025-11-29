# 力扣题库 - 搜索插入位置
## 想法
## Python
```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
```
### 复杂度
- 时间复杂度：O(Logn),执行时间：0ms
- 空间复杂度：O(1),消耗内存：18.33MB
## C
```c
int searchInsert(int* nums, int numsSize, int target) {
    int left = 0;
    int right = numsSize - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return left;
}
```
### 复杂度
- 时间复杂度：O(Logn),执行时间：0ms
- 空间复杂度：O(1),消耗内存：8.22MB
## Java
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return left;
    }
}
```
### 复杂度
- 时间复杂度：O(Logn),执行时间：0ms
- 空间复杂度：O(1),消耗内存：44.12MB