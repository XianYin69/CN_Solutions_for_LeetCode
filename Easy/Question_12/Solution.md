# 力扣题库 - 加一
## 想法
- python的是我自己想出来的，其他我用了AI
## Python
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        carry = 1
        for i in range(len(digits) - 1, -1, -1):
            digits[i] = digits[i] + carry
            carry = digits[i] // 10
            digits[i] = digits[i] % 10
            if carry == 0:
                return digits
        if carry == 1:
            digits.insert(0, 1)
        return digits
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：17.56MB
## C
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
     for (int i = digitsSize - 1; i >= 0; i--) {
        if (digits[i] < 9) {
            digits[i]++;
            *returnSize = digitsSize;
            return digits;
        } else {
            digits[i] = 0;
        }
    }
    *returnSize = digitsSize + 1;
    int* newDigits = (int*)calloc((*returnSize) ,sizeof(int));
    newDigits[0] = 1;
    return newDigits;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：9.22MB
## Java
```java
class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i = i - 1) {
            if (digits[i] < 9) {
                digits[i] ++;
                return digits;
            } else {
                digits[i] = 0;
            }
        }
        int [] Array = new int[digits.length + 1];
        Array[0] = 1;
        return Array;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：42.85MB