# 力扣题库 - 最长公共前缀
## 想法
- python是我自己写的
- 我爱语法糖
- 获取字符，遍历所有列表中字符串该下标的字符是否匹配，如果不匹配则中断。
- 这就是字典树吗。也是，单词是节点，字符连接各个节点
## Python
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        result = ""
        indexListElem = 0
        indexStrChara = 0
        tmpStrChara = ""
        sig = True
        indexMinStr = strs.index(min(strs))
        for indexStrChara in range(0, len(strs[indexMinStr])):
            tmpStrChara = strs[indexMinStr][indexStrChara]
            for indexListElem in strs:
                if indexListElem[indexStrChara] == tmpStrChara:
                    sig = True
                else:
                    sig = False
                    break
            if sig:
                result = result + tmpStrChara
            else:
                break
        return result
```
### 复杂度
- 时间复杂度：O(N∗M)O(N∗M),执行时间：0ms
- 空间复杂度：O(1)O(1),消耗内存：17.73MB
## C
```c
char* longestCommonPrefix(char** strs, int strsSize) {
    if (strsSize == 0) {
        char* result = (char*)malloc(1);
        result[0] = '\0';
        return result;
    }

    int min_len = strlen(strs[0]);
    for (int i = 1; i < strsSize; i++) {
        int current_len = strlen(strs[i]);
        if (current_len < min_len) {
            min_len = current_len;
        }
    }

    if (min_len == 0) {
        char* result = (char*)malloc(1);
        result[0] = '\0';
        return result;
    }

    char* result = (char*)malloc(min_len + 1);
    if (result == NULL) {
        return NULL;
    }

    int sig = 1;
    for (int idx_chara = 0; idx_chara < min_len; idx_chara++) {
        char tmp_chara = strs[0][idx_chara];

        for (int idx_list = 0; idx_list < strsSize; idx_list++) {
            if (strs[idx_list][idx_chara] != tmp_chara) {
                sig = 0;
                break;
            }
        }

        if (sig) {
            result[idx_chara] = tmp_chara;
        } else {
            result[idx_chara] = '\0';
            break;
        }
    }

    result[min_len] = '\0';

    return result;
}
```
### 复杂度
- 时间复杂度：O(Nm)O(Nm),执行时间：3ms
- 空间复杂度：O(N)O(N),消耗内存：8.05MB
## Java
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) {
            return "";
        }
        
        int minLen = strs[0].length();
        for (String s : strs) {
            if (s.length() < minLen) {
                minLen = s.length();
            }
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < minLen; i++) {
            char c = strs[0].charAt(i);
            for (String s : strs) {
                if (s.charAt(i) != c) {
                    return sb.toString();
                }
            }
            sb.append(c);
        }
        
        return sb.toString();
    }
}
```
### 复杂度
- 时间复杂度：O(N∗M),执行时间：1ms
- 空间复杂度：O(1),消耗内存：42.41MB