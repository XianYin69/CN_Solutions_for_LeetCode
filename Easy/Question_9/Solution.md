# 力扣题库 - 找出字符串中一个匹配的下标
## 想法
## Python
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if not needle:
            return -1

        len_h = len(haystack)
        len_n = len(needle)

        for i in range(len_h - len_n + 1):
            if haystack[i:i+len_n] == needle:
                return i
        return -1
```
### 复杂度
- 时间复杂度：O(N∗M),执行时间：0ms
- 空间复杂度：O(M),消耗内存：17.55MB
## C
```c
int strStr(char* haystack, char* needle) {
    int len_h = strlen(haystack);
    int len_n = strlen(needle);

    if (len_n == 0 || len_h == 0) {
        return -1;
    }

    for (int i = 0; i < len_h - len_n + 1; i = i + 1){
        if (haystack[i] == needle[0]) {
            int j = 0;
            while (j < len_n && haystack[i + j] == needle[j]) {
                j = j + 1;
            }
            if (j == len_n) {
                return i;
            }
        }
    }
    return -1;
}
```
### 复杂度
- 时间复杂度：O(N∗M),执行时间：0ms
- 空间复杂度：O(M),消耗内存：7.84MB
## Java
```java
class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.length() == 0) {
            return 0;
        }

        int len_h = haystack.length();
        int len_n = needle.length();

        for (int i = 0; i <= len_h - len_n; i++) {
            
            if (haystack.charAt(i) == needle.charAt(0)) {
                
                int j = 0;
                while (j < len_n && haystack.charAt(i + j) == needle.charAt(j)) {
                    j++;
                }

                if (j == len_n) {
                    return i;
                }
            }
        }

        return -1;
    }
}
```
### 复杂度
- 时间复杂度：O(N∗M),执行时间：0ms
- 空间复杂度：O(M),消耗内存：42.04MB