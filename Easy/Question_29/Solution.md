# 力扣题库 - 验证回文串
## 想法
- 双指针+递归
## Python
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        new_s = [char.lower() for char in s if char.isalnum()]
        left, right = 0, len(new_s) - 1
        while left < right:
            if new_s[left] != new_s[right]:
                return False
            left = left + 1
            right = right - 1
        return True
```
### 复杂度
- 时间复杂度：O(N),执行时间：11ms
- 空间复杂度：O(N),消耗内存：21.68MB
## C
```c
bool isPalindrome(char* s) {
    int index_end = strlen(s) - 1;
    int index_start = 0;
    while (index_end > index_start) {
        if (!isalnum(s[index_start])) {
            index_start = index_start + 1;
        } else if (!isalnum(s[index_end])) {
            index_end = index_end - 1;
        } else {
            if (tolower(s[index_start]) != tolower(s[index_end])) {
                return false;
            }
            index_end = index_end - 1;
            index_start = index_start + 1;
        }
    }
    return true;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：8.35MB
## Java
```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;
        while (left < right) {
            if (!Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            } else if (!Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            } else {
                if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                    return false;
                }
                left ++;
                right --;
            }
        }
        return true;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：3ms
- 空间复杂度：O(N),消耗内存：43.57MB