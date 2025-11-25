# 力扣题库 - 移除元素
## 想法
- 这题依然使用双指针
## Python
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        counter = 0
        for indexFlag in range(0, len(nums)):
            if nums[indexFlag] != val:
                nums[counter] = nums[indexFlag]
                counter = counter + 1
        return counter
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：17.66MB
## C
```c
int removeElement(int* nums, int numsSize, int val) {
    int counter = 0;
    for (int indexFlag = 0; indexFlag < numsSize; indexFlag = indexFlag + 1) {
        if (nums[indexFlag] != val) {
            nums[counter] = nums[indexFlag];
            counter = counter + 1;
        }
    }
    return counter;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：9.54MB
## Java
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int counter = 0;
        for (int indexFlag = 0; indexFlag < nums.length; indexFlag = indexFlag + 1) {
            if (nums[indexFlag] != val) {
                nums[counter] = nums[indexFlag];
                counter = counter + 1;
            }
        }
        return counter;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：42.64MB