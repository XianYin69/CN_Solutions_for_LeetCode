# 力扣题库 - 爬楼梯
## 想法
- 我想到的是一种广度优先算法的变体，但是太复杂了
## Python
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1:
            return 1
        if n == 2:
            return 2
        two_steps_back = 1
        one_steps_back = 2
        for i in range(3, n + 1):
            current_ways = one_steps_back + two_steps_back
            two_steps_back = one_steps_back
            one_steps_back = current_ways
        return one_steps_back
```
### 复杂度
- 时间复杂度：O(N),执行时间：4ms
- 空间复杂度：O(1),消耗内存：17.39MB
## C
```c
int climbStairs(int n) {
    if (n == 1) {
        return 1;
    }
    if (n == 2) {
        return 2;
    }
    int two_steps_back = 1;
    int one_steps_back = 2;
    for (int i = 3; i < n + 1; i = i + 1) {
        int current_ways = one_steps_back + two_steps_back;
        two_steps_back = one_steps_back;
        one_steps_back = current_ways;
    }
    return one_steps_back;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：7.65MB
## Java
```java
class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        }
        if (n == 2) {
            return 2;
        }
        int two_steps_back = 1;
        int one_steps_back = 2;
        for (int i = 3; i < n + 1; i = i + 1) {
            int current_ways = one_steps_back + two_steps_back;
            two_steps_back = one_steps_back;
            one_steps_back = current_ways;
        }
        return one_steps_back;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：41.25MB