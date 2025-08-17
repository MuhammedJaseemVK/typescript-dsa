# Rotate Image by 90 degree
Given an nxn matrix, your task is to rotate the matrix 90 degrees clockwise.

## Bruteforce
```ts
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

const rows = matrix.length;
const columns = matrix[0].length;

const result: Array<number[]> = [];

for (let i = 0; i < rows; i++) {
  const column = new Array(columns).fill(0);
  result.push(column);
}

for (let i = 0; i < rows; i++) {
  for (let j = 0; j < columns; j++) {
    if (i === 0) {
      result[j][columns-1] = matrix[i][j];
    } else if (i === columns-1) {
      result[j][0] = matrix[i][j];
    } else {
      result[j][i] = matrix[i][j];
    }
  }
}

for (let i = 0; i < rows; i++) {
  const column: number[] = [];
  for (let j = 0; j < columns; j++) {
    column.push(result[i][j]);
  }
  console.log(column);
}
```
Time Complexity:  O(N^2)

Space Complexity:  O(N^2)

## Optimized
```ts
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

const rows = matrix.length;
const columns = matrix[0].length;

// finding transpose
for (let i = 0; i < rows; i++) {
  for (let j = i + 1; j < columns; j++) {
    [matrix[j][i], matrix[i][j]] = [matrix[i][j], matrix[j][i]];
  }
}

// reversing
for (let i = 0; i < rows; i++) {
  let left = 0;
  let right = columns - 1;
  while (left< right) {
    [matrix[i][left], matrix[i][right]] = [matrix[i][right], matrix[i][left]];
    left++;
    right--;
  }
}

for (let i = 0; i < rows; i++) {
  console.log(matrix[i]);
}
```
Time Complexity:  O(N^2) + O(N^2)

Space Complexity:  O(1)
