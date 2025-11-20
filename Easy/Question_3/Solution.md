# 力扣题库 - 罗马数字转整数
## 想法
- 树形结构->匹配到对应的节点->结果相加
- 这题完全没有求助AI
## Python
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        s = s + 'E'
        indexNum = 0
        checkNum = 1
        listLen = len(s) - 1
        result = 0
        tmpRoma = 0
        
        while indexNum < listLen:
            match s[indexNum]:
                case 'I':
                    match s[checkNum]:
                        case 'V':
                            tmpRoma = 4
                            indexNum = indexNum + 1
                        case 'X':
                            tmpRoma = 9
                            indexNum = indexNum + 1
                        case _:
                            tmpRoma = 1
                case 'V':
                    tmpRoma = 5
                case 'X':
                    match s[checkNum]:
                        case 'L':
                            tmpRoma = 40
                            indexNum = indexNum + 1
                        case 'C':
                            tmpRoma = 90
                            indexNum = indexNum + 1
                        case _:
                            tmpRoma = 10
                case 'L':
                    tmpRoma = 50
                case 'C':
                    match s[checkNum]:
                        case 'D':
                            tmpRoma = 400
                            indexNum = indexNum + 1
                        case 'M':
                            tmpRoma = 900
                            indexNum = indexNum + 1
                        case _:
                            tmpRoma = 100
                case 'D':
                    tmpRoma = 500
                case 'M':
                    tmpRoma = 1000
                case _:
                    tmpRoma = 0
            result += tmpRoma
            indexNum = indexNum + 1
            checkNum = indexNum + 1
        return result
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：3ms
- 空间复杂度：O(1)O(1),消耗内存：17.53MB
## C
```c
int romanToInt(char* s) {
    int strRomeLen = strlen(s);
    int indexRomeNum = 0;
    int checkRomeNum = indexRomeNum + 1;
    int result = 0;
    int tmpRome = 0;

    while (indexRomeNum < strRomeLen) {
        switch (s[indexRomeNum]) {
            case 'I':
                switch (s[checkRomeNum]) {
                    case 'V':
                        tmpRome = 4;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    case 'X':
                        tmpRome = 9;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    default:
                        tmpRome = 1;
                        break;
                }
                break;
            case 'V':
                tmpRome = 5;
                break;
            case 'X':
                switch (s[checkRomeNum]) {
                    case 'L':
                        tmpRome = 40;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    case 'C':
                        tmpRome = 90;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    default:
                        tmpRome = 10;
                        break;
                }
                break;
            case 'L':
                tmpRome = 50;
                break;
            case 'C':
                switch (s[checkRomeNum]) {
                    case 'D':
                        tmpRome = 400;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    case 'M':
                        tmpRome = 900;
                        indexRomeNum = indexRomeNum + 1;
                        break;
                    default:
                        tmpRome = 100;
                        break;
                }
                break;
            case 'D':
                tmpRome = 500;
                break;
            case 'M':
                tmpRome = 1000;
                break;
            default:
                tmpRome = 0;
                break;
        }
        result = result + tmpRome;
        indexRomeNum = indexRomeNum + 1;
        checkRomeNum = indexRomeNum + 1;
    }
    return result;
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：0ms
- 空间复杂度：O(1)O(1),消耗内存：1MB
## Java
```java
class Solution {
    public int romanToInt(String s) {
        s = s + 'A';
        int result = 0;
        int indexRome = 0;
        int checkRome = indexRome + 1;
        int tmpRome = 0;
        int strRomeLen = s.length();

        while (indexRome < strRomeLen) {
            switch (s.charAt(indexRome)) {
                case 'I':
                    switch (s.charAt(checkRome)) {
                        case 'V':
                            tmpRome = 4;
                            indexRome = indexRome + 1;
                            break;
                        case 'X':
                            tmpRome = 9;
                            indexRome = indexRome + 1;
                            break;
                        default:
                            tmpRome = 1;
                            break;
                    }
                    break;
                case 'X':
                    switch (s.charAt(checkRome)) {
                        case 'L':
                            tmpRome = 40;
                            indexRome = indexRome + 1;
                            break;
                        case 'C':
                            tmpRome = 90;
                            indexRome = indexRome + 1;
                            break;
                        default:
                            tmpRome = 10;
                            break;
                    }
                    break;
                case 'C':
                    switch (s.charAt(checkRome)) {
                        case 'D':
                            tmpRome = 400;
                            indexRome = indexRome + 1;
                            break;
                        case 'M':
                            tmpRome = 900;
                            indexRome = indexRome + 1;
                            break;
                        default:
                            tmpRome = 100;
                            break;
                    }
                    break;
                case 'V':
                    tmpRome = 5;
                    break;
                case 'L':
                    tmpRome = 50;
                    break;
                case 'D':
                    tmpRome = 500;
                    break;
                case 'M':
                    tmpRome = 1000;
                    break;
                default:
                    tmpRome = 0;
                    break;
            }
            result = result + tmpRome;
            indexRome = indexRome + 1;
            checkRome = indexRome + 1;
        }
        return result;
    }
}
```
### 复杂度
- 时间复杂度：O(N)O(N),执行时间：4ms
- 空间复杂度：O(1)O(1),消耗内存：45.83MB