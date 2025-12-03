# 力扣题库 - x的平方根
## 想法
- 我第一次想到的是穷举出结果，但是效率太低了，于是就使用二分法查找
## Python
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x < 2:
            return x
        left, right = 1, x // 2
        while left <= right:
            mid = left + (right - left) // 2
            square = mid * mid
            if square == x:
                return mid
            elif square < x:
                left = mid + 1
            else:
                right = mid - 1
        return right

```
### 复杂度
- 时间复杂度：O(logN),执行时间：0ms
- 空间复杂度：O(1),消耗内存：17.69MB
## C
```c
int mySqrt(int x) {
    int left = 1;
    int right = x / 2;
    
    if (x < 2) {
        return x;
    }
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        long square = (long)mid * mid; 
        if (square == x) {
            return mid;
        } else if (square < x) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return right;
}
```
### 复杂度
- 时间复杂度：O(logN),执行时间：3ms
- 空间复杂度：O(1),消耗内存：8.33MB
## Java
```java
class Solution {
    public int mySqrt(int x) {
        int left = 1;
        int right = x / 2;
        if (x < 2) {
            return x;
        }
        while (left <= right) {
            int mid = left + (right - left) / 2;
            long square = (long)mid * mid;
            if (square == x) {
                return mid;
            } else if (square < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return right;
    }
}
```
### 复杂度
- 时间复杂度：O(logN),执行时间：1ms
- 空间复杂度：O(1),消耗内存：41.98MB