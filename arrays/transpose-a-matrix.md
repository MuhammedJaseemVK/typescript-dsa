# Transpose a Matrix
Given a matrix, your task is to find its transpose of the given matrix.
Transpose: The transpose of a matrix means, interchanging its rows into columns or columns into rows.

## Brute Force
```ts
const matrix = [
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9, 10, 11, 12],
  [13, 14, 15, 16],
];

const rows = matrix.length;
const columns = matrix[0].length;

const result: Array<number[]> = [];
for (let i = 0; i < columns; i++) {
  result.push(new Array(rows).fill(0));
}

for (let i = 0; i < rows; i++) {
  for (let j = 0; j < columns; j++) {
    result[j][i] = matrix[i][j];
  }
}

for (let i = 0; i < columns; i++) {
    console.log(result[i]);
}
```
Time Complexity: O(N*N) + O(N*N)

Space Complexity: O(N*N)

## Optimized (In-place transpose (for square matrices only, i.e N*N)
```ts
const matrix = [
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9, 10, 11, 12],
  [13, 14, 15, 16],
];

const rows = matrix.length;
const columns = matrix[0].length;

for (let i = 0; i < rows; i++) {
  for (let j = i; j < columns; j++) {
    [matrix[j][i], matrix[i][j]] = [matrix[i][j], matrix[j][i]];
  }
}

for (let i = 0; i < rows; i++) {
  console.log(matrix[i]);
}
```
Time Complexity: O(N*N)

Space Complexity: O(1)
