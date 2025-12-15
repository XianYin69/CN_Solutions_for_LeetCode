# 力扣题库 - 杨辉三角
## 想法
- 这里使用迭代
- 由 Gemini 生成
## Python
```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows == 0:
            return []
        triAngle = [[1]]
        for i in range(1, numRows):
            prev_row = triAngle[-1]
            current_row = [1]
            for j in range(1, len(prev_row)):
                new_element = prev_row[j - 1] + prev_row[j]
                current_row.append(new_element)
            current_row.append(1)
            triAngle.append(current_row)
        return triAngle
```
### 复杂度
- 时间复杂度：O(N^2),执行时间：0ms
- 空间复杂度：O(N^2),消耗内存：17.36MB
## C
```c
/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int* returnSize, int** returnColumnSizes) {
    if (numRows == 0) {
        *returnSize = 0;
        *returnColumnSizes = NULL;
        return NULL;
    }

    // 1. 设置返回参数
    *returnSize = numRows;
    // 分配内存存储每一行的列数 (例如，第 i 行有 i+1 个元素)
    *returnColumnSizes = (int*)malloc(numRows * sizeof(int));
    if (*returnColumnSizes == NULL) {
        // 错误处理：内存分配失败
        return NULL; 
    }

    // 2. 分配二维数组的行 (指针数组)
    int** triangle = (int**)malloc(numRows * sizeof(int*));
    if (triangle == NULL) {
        free(*returnColumnSizes);
        // 错误处理：内存分配失败
        return NULL;
    }

    // 3. 逐行生成杨辉三角
    for (int i = 0; i < numRows; i++) {
        // 第 i 行有 i + 1 个元素
        int currentColSize = i + 1;
        (*returnColumnSizes)[i] = currentColSize;

        // 为当前行分配内存
        triangle[i] = (int*)malloc(currentColSize * sizeof(int));
        if (triangle[i] == NULL) {
            // 错误处理：内存分配失败，需要释放之前分配的所有内存
            for (int k = 0; k < i; k++) {
                free(triangle[k]);
            }
            free(triangle);
            free(*returnColumnSizes);
            return NULL;
        }

        // 4. 填充当前行
        for (int j = 0; j < currentColSize; j++) {
            if (j == 0 || j == i) {
                // 行首和行尾的元素总是 1
                triangle[i][j] = 1;
            } else {
                // 中间元素：当前元素 = 左上方元素 + 右上方元素
                // 仅当 i > 0 时才执行
                // left_parent = triangle[i-1][j-1]
                // right_parent = triangle[i-1][j]
                triangle[i][j] = triangle[i - 1][j - 1] + triangle[i - 1][j];
            }
        }
    }

    return triangle;
}
```
### 复杂度
- 时间复杂度：O(N^2),执行时间：0ms
- 空间复杂度：O(N^2),消耗内存：10.70MB
## Java
```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
    // 1. 初始化结果列表
        List<List<Integer>> triangle = new ArrayList<>();

        if (numRows == 0) {
            return triangle;
        }

        // 2. 处理第 0 行：总是 [1]
        List<Integer> firstRow = new ArrayList<>();
        firstRow.add(1);
        triangle.add(firstRow);

        // 3. 从第 1 行开始迭代，直到 numRows - 1
        for (int i = 1; i < numRows; i++) {
            // 获取上一行（即 i-1 行）
            List<Integer> prevRow = triangle.get(i - 1);
            
            // 初始化当前行
            List<Integer> currentRow = new ArrayList<>();
            
            // 当前行的第一个元素总是 1
            currentRow.add(1);

            // 4. 计算中间元素：基于上一行的相邻元素之和
            // 循环范围：从上一行的索引 1 到 倒数第二个元素
            for (int j = 1; j < prevRow.size(); j++) {
                // 当前元素 = 上一行左侧元素 + 上一行右侧元素
                int newElement = prevRow.get(j - 1) + prevRow.get(j);
                currentRow.add(newElement);
            }

            // 当前行的最后一个元素总是 1
            currentRow.add(1);

            // 将新生成的行添加到结果列表中
            triangle.add(currentRow);
        }
        return triangle;
    }
}
```
### 复杂度
- 时间复杂度：O(N^2),执行时间：1ms
- 空间复杂度：O(N^2),消耗内存：42.65MB