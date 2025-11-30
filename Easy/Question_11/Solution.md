# 力扣题库 - 最后一个单词的长度
## 想法
## Python
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        length = 0
        for i in range(len(s) - 1, -1, -1):
            if s[i] != ' ':
                length += 1
            elif length > 0:
                return length
        return length
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：17.69MB
## C
```c
int lengthOfLastWord(char* s) {
    int counter = 0;
    for (int i = strlen(s) - 1; i >= 0; i --) {
        if (s[i] != ' ') {
            counter += 1;
        } else if (counter > 0) {
            return counter;
        }
    }
    return counter;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：7.93MB
## Java
```java
class Solution {
    public int lengthOfLastWord(String s) {
        int counter = 0;
        for (int i = s.length() - 1; i >= 0; i = i - 1) {
            if (s.charAt(i) != ' ') {
                counter = counter + 1;
            } else if (counter > 0) {
                return counter;
            }
        }
        return counter;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：42.18MB