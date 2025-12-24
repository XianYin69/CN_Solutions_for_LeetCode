# 力扣题库 - Excel 表格名称
## 想法
- 就是输出字符串
## Python
```python
class Solution:
    def convertToTitle(self, columnNumber: int) -> str:
        res = []
        while columnNumber > 0:
            columnNumber -= 1
            remainder = columnNumber % 26
            res.append(chr(ord('A') + remainder))
            columnNumber //= 26
        return "".join(reversed(res))
```
### 复杂度
- 时间复杂度：O(Log(N)),执行时间：0ms
- 空间复杂度：O(N),消耗内存：17.41MB
## C
```c
char* convertToTitle(int columnNumber) {
    char* res = (char*)malloc(sizeof(char) * 10);
    int index = 0;
    while (columnNumber > 0) {
        columnNumber--;
        res[index++] = (columnNumber % 26) + 'A';
        columnNumber /= 26;
    }
    res[index] = '\0';
    int left = 0, right = index - 1;
    while (left < right) {
        char temp = res[left];
        res[left] = res[right];
        res[right] = temp;
        left++;
        right--;
    }
    return res;
}
```
### 复杂度
- 时间复杂度：O(Log(N)),执行时间：0ms
- 空间复杂度：O(N),消耗内存：7.92MB
## Java
```java
class Solution {
    public String convertToTitle(int columnNumber) {
        StringBuilder sb = new StringBuilder();
        while (columnNumber > 0) {
            columnNumber--;
            char c = (char) (columnNumber % 26 + 'A');
            sb.append(c);
            columnNumber /= 26;
        }
        return sb.reverse().toString();
    }
}
```
### 复杂度
- 时间复杂度：O(Log(N)),执行时间：0ms
- 空间复杂度：O(N),消耗内存：41.76MB