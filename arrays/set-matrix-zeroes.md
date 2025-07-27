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
