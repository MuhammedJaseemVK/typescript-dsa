# Count Subarray sum Equals K
Given an array of integers and an integer k, return the total number of subarrays whose sum equals k.
## Bruteforce
```ts
const array = [3, 1, 2, 4];
const k = 6;
let count = 0;

for (let i = 0; i < array.length; i++) {
  for (let j = i; j < array.length; j++) {
    let sum = 0;
    for (let m = i; m <= j; m++) {
      sum += array[m];
    }
    if (sum === k) {
      count++;
    }
  }
}

console.log(count);
```
Time Complexity:  O(N^3)

Space Complexity:  O(1)

## Better
```ts
const array = [3, 1, 2, 4];
const k = 6;
let count = 0;

for (let i = 0; i < array.length; i++) {
  let sum = 0;
  for (let j = i; j < array.length; j++) {
    sum += array[j];
    if (sum === k) {
      count++;
    }
  }
}

console.log(count);
```
Time Complexity:  O(N^2)

Space Complexity:  O(1)
