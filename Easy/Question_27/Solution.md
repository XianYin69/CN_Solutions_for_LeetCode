# 力扣题库 - 杨辉三角II
## 想法
## Python
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        if rowIndex == 0:
            return [1]
        triAngle = [[1]]
        for i in range(1, rowIndex + 1):
            prev_row = triAngle[-1]
            current_row = [1]
            for j in range(1,len(prev_row)):
                new_element = prev_row[j - 1] + prev_row[j]
                current_row.append(new_element)
            current_row.append(1)
            triAngle.append(current_row)
        return triAngle[rowIndex]
```
### 复杂度
- 时间复杂度：O(N**2),执行时间：0ms
- 空间复杂度：O(N),消耗内存：17.45MB
## C
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize) {
    int size = rowIndex + 1;
    *returnSize = size;
    int* result = (int*)malloc(size * sizeof(int));
    for (int i = 0; i < size; i++) {
        result[i] = 0;
    }
    result[0] = 1;
    for (int i = 1; i <= rowIndex; i++) {
        result[i] = 1;
        for (int j = i - 1; j >= 1; j--) {
            result[j] = result[j] + result[j - 1];
        }
    }
    return result;
}
```
### 复杂度
- 时间复杂度：O(N**2),执行时间：0ms
- 空间复杂度：O(N),消耗内存：8.48MB
## Java
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
       List<Integer> result = new ArrayList<>();
       result.add(1);
       for (int i = 1; i <= rowIndex; i++) {
        result.add(1);
        for (int j = i - 1; j >= 1; j--) {
            int newVal =result.get(j) + result.get(j - 1);
            result.set(j, newVal);
        }
       }
       return result;
    }
}
```
### 复杂度
- 时间复杂度：O(N**2),执行时间：1ms
- 空间复杂度：O(N),消耗内存：42.09MB