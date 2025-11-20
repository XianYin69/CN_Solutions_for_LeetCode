# 力扣题库 - 回文数
## 想法
- 大于零 且 倒置前后相等
- 我原本想在 python 里用一行实现（语法糖真是太好用了你知道吗）但是大于121小于130的数字被判定为回文数是我不能理解的，如果又哪位大佬能解释一下的话，鄙人感激不尽
- 如果在生产中像我注释那行写的话，那只能祝你平安~哦/祝你平安……
## Python
```python
class Solution:
def isPalindrome(self, x: int) -> bool:
#        return x >= 0 and (x % 10 != 0 or x == 0)and x == (lambda f: f(f, x))(lambda self, n: 0 if n == 0 else self(self, n // 10) * 10 + n % 10) #我不知道为什么在(121, 130)区间内的数被判定为回文数#
    if x < 0 or (x % 10 == 0 and x != 0):
        return False
    oriNum = x
    transNum = 0
    while x > 0:
        lastNum = x % 10
        transNum = transNum * 10 + lastNum
        x = x // 10
    return transNum == oriNum 
    
```
### 复杂度
- 时间复杂度：O(Log10(N))O(Log10(N)),执行时间：15ms
- 空间复杂度：O(1)O(1),消耗内存：17.75MB
## C
```c
bool isPalindrome(int x) {
    int oriNum = x;
    int lastNum = 0;
    long long transNum = 0;
    if ((oriNum < 0) && ((oriNum % 10 == 0) || (oriNum == 0))) {
        return false;
    }
    while (x > 0) {
        lastNum = x % 10;
        transNum = transNum * 10 + lastNum;
        x = x / 10;
    }
    return (oriNum == transNum);
}
```
### 复杂度
- 时间复杂度：O(Log(N))O(Log(N)),执行时间：0ms
- 空间复杂度：O(1)O(1),消耗内存：8.14MB
## Java
```java
class Solution {
    public boolean isPalindrome(int x) {
        int oriNum = x;
        int lastNum = 0;
        int transNum = 0;
        if (oriNum < 0 || (oriNum % 10 == 0 && oriNum != 0)) {
            return false;
        }
        while(x > 0) {
            lastNum = x % 10;
            transNum = transNum * 10 + lastNum;
            x = x / 10;
        }
        return oriNum == transNum;
    }
}
```
### 复杂度
- 时间复杂度：O(Log(N))O(Log(N)),执行时间：5ms
- 空间复杂度：O(1)O(1),消耗内存：45.15MB