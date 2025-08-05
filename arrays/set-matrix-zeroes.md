# Set Matrix Zero
Given a matrix if an element in the matrix is 0 then you will have to set its entire column and row to 0 and then return the matrix.

## Brute Force
```ts
const m = matrix.length;
const n = matrix[0].length;

for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
        if (matrix[i][j] === 0) {
            markRow(matrix, i, n);
            markColumn(matrix, m, j)
        }
    }
}

function markColumn(matrix: number[][], rowCount: number, columnIndex: number) {
    for (let i = 0; i < rowCount; i++) {
        if (matrix[i][columnIndex] !== 0) {
            matrix[i][columnIndex] = -Infinity;
        }
    }
}

function markRow(matrix: number[][], rowIndex: number, columnCount: number) {
    for (let i = 0; i < columnCount; i++) {
        if (matrix[rowIndex][i] !== 0) {
            matrix[rowIndex][i] = -Infinity;
        }
    }
}


for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
        if (matrix[i][j] === -Infinity) {
            matrix[i][j] = 0;
        }
    }
}


for (let i = 0; i < m; i++) {
    const roe: number[] = [];
    for (let j = 0; j < n; j++) {
        row.push(matrix[i][j]);
    }
    console.log(row);
}
```
Time Complexity: O((N*M)*(N + M)) + O(N*M)

Space Complexity: O(1)

## Better
```ts
const matrix = [
  [0, 1, 2, 0],
  [3, 4, 5, 2],
  [1, 3, 1, 5],
];
const m = matrix.length;
const n = matrix[0].length;

const rows: number[] = Array(m).fill(0);
const columns: number[] = Array(n).fill(0);

const values: number[][] = [];

for (let i = 0; i < m; i++) {
  for (let j = 0; j < n; j++) {
    if (matrix[i][j] === 0) {
      rows[i] = 1;
      columns[j] = 1;
    }
  }
}

for (let i = 0; i < m; i++) {
  for (let j = 0; j < n; j++) {
    if(rows[i]=== 1|| columns[j]===1){
        matrix[i][j] = 0;
    }
  }
}

for (let i = 0; i < m; i++) {
  const column: number[] = [];
  for (let j = 0; j < n; j++) {
    column.push(matrix[i][j]);
  }
  console.log(column);
}
```
Time Complexity: O(N*M) + O(N*M)

Space Complexity: O(N*M)


## Optimized
```ts
const matrix = [
  [0, 1, 2, 0],
  [3, 4, 5, 2],
  [1, 3, 1, 5],
];
const m = matrix.length;
const n = matrix[0].length;

const values: number[][] = [];

let col0:boolean = false;

for (let i = 0; i < m; i++) {
  for (let j = 0; j < n; j++) {
    if (matrix[i][j] === 0) {
      matrix[i][0] = 0;
      if (j !== 0) {
        matrix[0][j] = 0;
      } else {
        col0 = true;
      }
    }
  }
}

for (let i = 1; i < m; i++) {
  for (let j = 1; j < n; j++) {
    if (matrix[i][j] !== 0) {
      if (matrix[i][0] === 0 || matrix[0][j] === 0) {
        matrix[i][j] = 0;
      }
    }
  }
}

if(matrix[0][0] === 0){
    for(let i=0;i<n;i++){
        matrix[0][i] = 0;
    }
}

if(col0){
    for(let i=0;i<m;i++){
        matrix[i][0] = 0;
    }
}

for (let i = 0; i < m; i++) {
  const column: number[] = [];
  for (let j = 0; j < n; j++) {
    column.push(matrix[i][j]);
  }
  console.log(column);
}
```
Time Complexity: O(N*M) + O(N*M)

Space Complexity: O(1)
