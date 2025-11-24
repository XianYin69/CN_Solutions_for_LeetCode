# 力扣题库 - 删除有序数组中的重复项
## 想法
- 这题让我对我的语言产生了不自信，我觉得这题应该返回数组和计数，但是这题是返回技术和修改原数组
## Python
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        counter = 0
        result = []
        for tmp in nums:
            if tmp not in result:
                result.append(tmp) 
                counter = counter + 1
        nums.clear()
        for tmp in result:
            nums.append(tmp)
        return counter
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：19ms
- 空间复杂度：O(N)O(N),消耗内存：18.64MB
## C
```c
int removeDuplicates(int* nums, int numsSize) {
    int counter = 0;
    int indexFlag = 0;
    if (numsSize <= 1) {
        return numsSize;
    }

    for (int checkFlag = 0; checkFlag < numsSize; checkFlag = checkFlag + 1) {
        if (nums[indexFlag] != nums[checkFlag]) {
            indexFlag = indexFlag + 1;
            nums[indexFlag] = nums[checkFlag];
            counter = counter + 1;
        }
    }

    return counter + 1;
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(1)O(1),消耗内存：12.02MB
## Java
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int counter = 0;
        int indexFlag = 0;

        for (int checkFlag = 0; checkFlag < nums.length; checkFlag = checkFlag + 1) {
            if (nums[indexFlag] != nums[checkFlag]) {
                indexFlag = indexFlag + 1;
                nums[indexFlag] = nums[checkFlag];
                counter = counter + 1;
            }
        }

        return counter + 1;
    }
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：1ms
- 空间复杂度：O(1)O(1),消耗内存：46.22MB