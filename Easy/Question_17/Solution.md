# 力扣题库 - 合并两个有序数组
## 想法
- 这题使用迭代方法
- 我觉得学校的计算机教育中应该强调序列中的索引就是指针
## Python
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        p1 = m - 1
        p2 = n - 1
        p = m + n - 1
        while p2 >= 0:
            if p1 >= 0 and nums1[p1] > nums2[p2]:
                nums1[p] = nums1[p1]
                p1 = p1 - 1
            else:
                nums1[p] = nums2[p2]
                p2 = p2 - 1
            p = p - 1 
```
### 复杂度
- 时间复杂度：O(M + N),执行时间：ms
- 空间复杂度：O(1),消耗内存：MB
## C
```c
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int p1 = m - 1;
    int p2 = n - 1;
    int p = m + n - 1;
    while (p2 >= 0) {
        if (p1 >= 0 && nums1[p1] > nums2[p2]) {
            nums1[p] = nums1[p1];
            p1 = p1 - 1;
        } else {
            nums1[p] = nums2[p2];
            p2 = p2 - 1;
        }
        p = p - 1;
    }
}
```
### 复杂度
- 时间复杂度：O(M + N),执行时间：ms
- 空间复杂度：O(1),消耗内存：MB
## Java
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = m - 1;
        int p2 = n - 1;
        int p = m + n - 1;
        while (p2 >= 0) {
            if (p1 >= 0 && nums1[p1] > nums2[p2]) {
                nums1[p] = nums1[p1];
                p1 = p1 - 1;
            } else {
                nums1[p] = nums2[p2];
                p2 = p2 - 1;
            }
            p = p - 1;
        }
    }
}
```
### 复杂度
- 时间复杂度：O(M + N),执行时间：ms
- 空间复杂度：O(1),消耗内存：MB