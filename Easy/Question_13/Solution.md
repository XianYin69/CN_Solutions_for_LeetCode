# 力扣题库 - 二进制求和
## 想法
- 我写了点，写不下去直接上AI
## Python
```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        result = []
        i, j = len(a) - 1, len(b) - 1
        carry = 0
        while i >= 0 or j >= 0 or carry:
            total_sum = carry
            if i >= 0:
                total_sum += int(a[i])
                i -= 1
            if j >= 0:
                total_sum += int(b[j])
                j -= 1
            result.append(str(total_sum % 2))
            carry = total_sum // 2
        return "".join(result[::-1])
```
### 复杂度
- 时间复杂度：O(N),执行时间：4ms
- 空间复杂度：O(N),消耗内存：17.82MB
## C
```c
char* addBinary(char* a, char* b) {
    int len_a = strlen(a);
    int len_b = strlen(b);
    int max_len = (len_a > len_b?len_a : len_b) + 1;
    char* result = (char*)malloc(max_len + 1);
    if (result == NULL) {
        return NULL;
    }

    int i = len_a - 1;
    int j = len_b - 1;
    int carry = 0;
    int k = max_len;
    result[k--] = '\0';
    while (i >= 0 || j >= 0 || carry) {
        int sum = carry;
        if (i >= 0) {
            sum += a[i] - '0';
            i--;
        }

        if (j >= 0) {
            sum += b[j] - '0';
            j--;
        }

        result[k--] = (sum % 2) + '0';
        carry = sum / 2;
    }

    if (k == -1) {
        return result;
    } else {
        return result + (k + 1);
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(N),消耗内存：7.94MB
## Java
```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder result = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;
        while (i >= 0 || j >=0 || carry == 1) {
            int sum = carry;
            if (i >= 0) {
                sum += a.charAt(i) - '0';
                i--;
            }
            if (j >= 0) {
                sum += b.charAt(j) - '0';
                j--;
            }
            result.append(sum % 2);
            carry = sum / 2;
        }
        return result.reverse().toString();
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：2ms
- 空间复杂度：O(N),消耗内存：43.03MB