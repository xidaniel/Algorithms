## Problem

https://app.laicode.io/app/problem/121

Traverse an N * N 2D array in spiral order clock-wise starting from the top left corner. Return the list of traversal sequence.

**Assumptions**

- The 2D array is not null and has size of N * N where N >= 0

**Examples**

{ {1,  2,  3},

 {4,  5,  6},

 {7,  8,  9} }

the traversal sequence is [1, 2, 3, 6, 9, 8, 7, 4, 5]



## The Way of Thinking

1. high level idea: **recursion or iteration **

2. 因为是N*N的矩阵

   1. 考虑N为基数和N为偶数的情况

3. 合理设置offset偏移量(offset每次加一),和每次子问题的size大小(size每次减二)

   

## Recursion Solution

```java
public class Solution {
  public List<Integer> spiral(int[][] matrix) {
    List<Integer> result = new ArrayList<>();
    helper(matrix, 0, matrix.length, result);
    return result;
  }

  public void helper(int[][] matrix, int offset, int size, List<Integer> result) {
    if (size == 0) {
      return;
    }
    if (size == 1) {
      result.add(matrix[offset][offset]);
      return;
    }

    for (int i = 0; i < size - 1; i++) {
      result.add(matrix[offset][offset + i]);
    }
    for (int i = 0; i < size - 1; i++) {
      result.add(matrix[offset + i][offset + size - 1]);
    }
    for (int i = size - 1; i > 0; i--) {
      result.add(matrix[offset + size - 1][offset + i]);
    }
    for (int i = size - 1; i > 0; i--) {
      result.add(matrix[offset + i][offset]);
    }
    helper(matrix, offset + 1, size - 2, result);
  }
}
```

## Iteration Solution

- high level idea: **iteration **
- 因为是N*N的矩阵

  1. 如果N = 3;  start = 0, end = 2;  -->  start = 1, end = 1,   **单独进行post-processing**
  2. 如果N = 4; start = 0, end = 3; --> start  = 1, end = 2; --> start = 2, end = 1

3. while (start < end)

```java
public class Solution {
  public List<Integer> spiral(int[][] matrix) {
    List<Integer> result = new ArrayList<>();

    int start = 0;
    int end = matrix.length - 1;
    while (start < end) {
      for (int i = start; i < end; i++) {
        result.add(matrix[start][i]);
      }
      for (int i = start; i < end; i++) {
        result.add(matrix[i][end]);
      }
      for (int i = end; i > start; i--) {
        result.add(matrix[end][i]);
      }
      for (int i = end; i > start; i--) {
        result.add(matrix[i][start]);
      }
      start++;
      end--;
    }
    if (start == end) {
      result.add(matrix[start][end]);
    }
    return result;
  }
}
```



end.