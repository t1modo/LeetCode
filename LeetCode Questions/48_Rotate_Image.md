# 48. Rotate Image

### Approach:
To rotate a square matrix 90 degrees clockwise, the process involves two main steps: transposing the matrix and performing a horizontal reflection. Transposing the matrix means flipping it over its diagonal, which effectively swaps rows with columns. This is achieved by iterating through the elements above the diagonal (where the row index is less than the column index) and swapping each element at position matrix[i][j] with the element at matrix[j][i]. After the transpose operation, the columns of the original matrix become the rows of the intermediate matrix.

The second step is to perform a horizontal reflection, which involves flipping the matrix symmetrically across its vertical axis. For each row, the elements at the beginning are swapped with the corresponding elements at the end. Specifically, for each row "i", the element at matrix[i][l] is swapped with the element at matrix[i][r], where "l" starts at the leftmost column (index 0) and "r" starts at the rightmost column (matrix[0].length - 1), moving inward until they meet.

### Code:
```
class Solution {
    public void rotate(int[][] matrix) {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = i + 1; j < matrix.length; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for (int i = 0; i < matrix.length; i++) {
            int r = matrix[0].length - 1;
            int l = 0;
            while (r > l) {
                int temp = matrix[i][l];
                matrix[i][l] = matrix[i][r];
                matrix[i][r] = temp;
                l++;
                r--;
            }
        }
    }
}
```