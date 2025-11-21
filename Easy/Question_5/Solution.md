# 力扣题库 - 有效的括号
## 想法
- 全部用AI写成。我目光狭隘没法顾及全局
- 括号是否正确闭合分为判断是否闭合和是否正确闭合。AI给出用栈的逻辑，把正括号以栈的形式放入一个堆中，如果反括号匹配则移出栈，直到堆中所有栈被移除。
## Python
```python
class Solution:
    def isValid(self, s: str) -> bool:
        BRACKET_MAP = {'}':'{', ']':'[', ')':'('}
        stack = []
        for char in s:
            if char in BRACKET_MAP.values():
                stack.append(char)
            else:
                if not stack or stack.pop() != BRACKET_MAP[char]:
                    return False
        return len(stack) == 0
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：3ms
- 空间复杂度：O(N)O(N),消耗内存：17.52MB
## C
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

bool isValid(char* s) {
    char bracket_map[128] = {0};
    bracket_map[')'] = '(';
    bracket_map[']'] = '[';
    bracket_map['}'] = '{';
    
    int max_stack_size = 100;
    char* stack = (char*)malloc(max_stack_size * sizeof(char));
    if (stack == NULL) return false;
    int stack_top = 0;
    
    int len = strlen(s);
    for (int i = 0; i < len; i++) {
        char ch = s[i];
        if (bracket_map[ch] == 0) {
            if (stack_top >= max_stack_size) {
                char* new_stack = (char*)realloc(stack, 2 * max_stack_size * sizeof(char));
                if (new_stack == NULL) {
                    free(stack);
                    return false;
                }
                stack = new_stack;
                max_stack_size *= 2;
            }
            stack[stack_top++] = ch;
        } else {
            if (stack_top == 0) {
                free(stack);
                return false;
            }
            char top_ch = stack[--stack_top];
            if (top_ch != bracket_map[ch]) {
                free(stack);
                return false;
            }
        }
    }
    
    bool result = (stack_top == 0);
    free(stack);
    return result;
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(N)O(N),消耗内存：8MB
## Java
```java
import java.util.HashMap;
import java.util.Map;
import java.util.Stack;

class Solution {
    private static final Map<Character, Character> BRACKET_MAP = new HashMap<>();

    static {
        BRACKET_MAP.put(')', '(');
        BRACKET_MAP.put(']', '[');
        BRACKET_MAP.put('}', '{');
    }

    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (BRACKET_MAP.containsValue(c)) {
                stack.push(c);
            } else if (BRACKET_MAP.containsKey(c)) {
                if (stack.isEmpty() || stack.pop() != BRACKET_MAP.get(c)) {
                    return false;
                }
            } else {
                return false;
            }
        }
        return stack.isEmpty();
    }
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：5ms
- 空间复杂度：O(N)O(N),消耗内存：42.49MB