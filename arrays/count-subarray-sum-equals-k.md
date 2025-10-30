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

## Optimized
```js
function countSubArraySumEqualsK(nums, k) {
  let count = 0;
  let prefixSum = 0;
  const map = new Map();
  map.set(0, 1);

  for (const num of nums) {
    prefixSum += num;

    const remove = prefixSum - k;
    if (map.has(remove)) {
      count += map.get(remove);
    }

    map.set(prefixSum, (map.get(prefixSum) || 0) + 1);
  }
  return count;
}

console.log(countSubArraySumEqualsK([1, 2, 3, -3, 1, 1, 1, 4, 2, -3], 3));
```
Time Complexity:  O(N)

Space Complexity:  O(N)
