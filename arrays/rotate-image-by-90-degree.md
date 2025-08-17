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
