# Spiral Traversal of Matrix
Given a Matrix, print the given matrix in spiral order.

## Optimized
```ts
const matrix = [
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9, 10, 11, 12],
  [13, 14, 15, 16],
];

const rows = matrix.length;
const columns = matrix[0].length;

const result = [];

let top = 0;
let bottom = rows - 1;
let left = 0;
let right = columns - 1;

while (top <= bottom && left <= right) {
  for (let i = left; i <= right; i++) {
    result.push(matrix[top][i]);
  }
  top++;

  for (let i = top; i <= bottom; i++) {
    result.push(matrix[i][right]);
  }
  right--;

  if (top <= bottom) {
    for (let i = right; i >= left; i--) {
      result.push(matrix[bottom][i]);
    }
    bottom--;
  }

  if (left <= right) {
    for (let i = bottom; i >= top; i--) {
      result.push(matrix[i][left]);
    }
    left++;
  }
}

console.log(result);
```
Time Complexity: O(M*N)

Space Complexity: O(M*N)

Space Complexity: O(1)
