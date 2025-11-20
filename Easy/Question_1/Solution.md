# 力扣题库 - 两数相加
## 想法
- 不用遍历整个数组
## Python
```python
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int indexFlag = 0;
        int selectFlag = 1;
        int MAX_SELECT_FLAG = nums.length - 1;
        int[] result = new int[2];
        while (nums[indexFlag] + nums[selectFlag] != target) {
            if (selectFlag < MAX_SELECT_FLAG) {
                selectFlag = selectFlag + 1;
            } else {
                indexFlag = indexFlag + 1;
                selectFlag = indexFlag + 1;
            }
        }
        result[0] = indexFlag;
        result[1] = selectFlag;
        return result;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：49ms
- 空间复杂度：O(1),消耗内存：45.41MB
## C
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    int indexFlag = 0;
    int selectFlag = indexFlag + 1;
    int MAX_SELECT_FLAG = numsSize - 1;
    int* returnList = (int*)malloc(2 * sizeof(int));
    *returnSize = 2;
    while (nums[indexFlag] + nums[selectFlag] != target) {
        if (selectFlag < MAX_SELECT_FLAG) {
            selectFlag = selectFlag + 1;
        } else {
            indexFlag = indexFlag + 1;
            selectFlag = indexFlag + 1;
        }
    }
    returnList[0] = indexFlag;
    returnList[1] = selectFlag;
    return returnList;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：135ms
- 空间复杂度：O(1),消耗内存：8.41MB
## Java
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int indexFlag = 0;
        int selectFlag = 1;
        int MAX_SELECT_FLAG = nums.length - 1;
        int[] result = new int[2];
        while (nums[indexFlag] + nums[selectFlag] != target) {
            if (selectFlag < MAX_SELECT_FLAG) {
                selectFlag = selectFlag + 1;
            } else {
                indexFlag = indexFlag + 1;
                selectFlag = indexFlag + 1;
            }
        }
        result[0] = indexFlag;
        result[1] = selectFlag;
        return result;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：73ms
- 空间复杂度：O(1),消耗内存：45.63MB