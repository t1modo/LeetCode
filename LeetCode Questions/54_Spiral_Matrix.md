# 54. Spiral Matrix

### Approach:
The approach to solving the problem of traversing a matrix in spiral order involves maintaining four boundary markers (top, bottom, left, and right) to define the portion of the matrix currently being processed. Initially, top is set to 0 (the first row), bottom is set to the total number of rows (matrix.length), left is set to 0 (the first column), and right is set to the total number of columns (matrix[0].length). An empty list, result, is used to store the elements of the matrix in the desired spiral order.

The traversal proceeds in a clockwise manner, layer by layer, as long as the boundaries do not overlap. Within each iteration of the main loop, the algorithm performs four steps. First, it traverses the row defined by the top boundary from left to right, appending each element to the result list, and then increments the top boundary to exclude the processed row. Next, it traverses the column defined by the right - 1 boundary from top to bottom, appending each element, and decrements the right boundary to exclude the processed column. If there are remaining rows, it then traverses the row defined by the bottom - 1 boundary from right to left, appending elements and decrementing the bottom boundary. Similarly, if there are remaining columns, it traverses the column defined by the left boundary from bottom to top, appending elements and incrementing the left boundary.

This process continues until the top boundary meets or exceeds the bottom boundary or the left boundary meets or exceeds the right boundary, signaling that all elements have been processed. The algorithm guarantees that each element is visited exactly once, and the dynamically adjusted boundaries ensure that the traversal respects the spiral pattern. At the end of the traversal, the list result containing the elements in spiral order is returned.

### Code:
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int top = 0;
        int bottom = matrix.length;
        int left = 0;
        int right = matrix[0].length;
        List<Integer> result = new ArrayList<>();
        while (top < bottom && left < right) {
            for (int i = left; i < right; i++) {
                result.add(matrix[top][i]);
            }
            top++;
            for (int i = top; i < bottom; i++) {
                result.add(matrix[i][right - 1]);
            }
            right--;
            if (top >= bottom || left >= right) {
                break;
            }
            for (int i = right - 1; i >= left; i--) {
                result.add(matrix[bottom - 1][i]);
            }
            bottom--;
            for (int i = bottom - 1; i >= top; i--) {
                result.add(matrix[i][left]);
            }
            left++;
        }
        return result;
    }
}
```