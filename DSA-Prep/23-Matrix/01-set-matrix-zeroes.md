# Set Matrix Zeroes

## Problem
If an element in a matrix is `0`, set its entire row and column to `0`, in place.

## Intuition
Use the first row and first column as marker storage instead of an extra matrix. Separately remember whether the original first row or first column contained zero.

## Java
```java
public void setZeroes(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;
    boolean firstRowZero = false;
    boolean firstColZero = false;

    for (int c = 0; c < cols; c++) {
        if (matrix[0][c] == 0) {
            firstRowZero = true;
        }
    }

    for (int r = 0; r < rows; r++) {
        if (matrix[r][0] == 0) {
            firstColZero = true;
        }
    }

    for (int r = 1; r < rows; r++) {
        for (int c = 1; c < cols; c++) {
            if (matrix[r][c] == 0) {
                matrix[r][0] = 0;
                matrix[0][c] = 0;
            }
        }
    }

    for (int r = 1; r < rows; r++) {
        for (int c = 1; c < cols; c++) {
            if (matrix[r][0] == 0 || matrix[0][c] == 0) {
                matrix[r][c] = 0;
            }
        }
    }

    if (firstRowZero) {
        Arrays.fill(matrix[0], 0);
    }

    if (firstColZero) {
        for (int r = 0; r < rows; r++) {
            matrix[r][0] = 0;
        }
    }
}
```

## Complexity
Time O(rows × cols), space O(1).