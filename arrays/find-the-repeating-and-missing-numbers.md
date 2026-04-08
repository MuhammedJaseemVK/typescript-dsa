# Find the repeating and missing numbers

Given an integer array nums of size n containing values from [1, n] and each value appears exactly once in the array, except for A, which appears twice and B which is missing.
Return the values A and B, as an array of size 2, where A appears in the 0-th index and B in the 1st index.

Example 1:

Input:
 nums = [3, 5, 4, 1, 1]  
 
Output: [1, 2]  

# Brute force
```ts
function findMissingAndRepeating(nums) {
  let missingNumber = null;
  let repeatingNumber = null;

  const n = nums.length;

  for (let i = 1; i <= n; i++) {
    if (missingNumber !== null && repeatingNumber !== null) break;

    let count = 0;

    for (let j = 0; j < n; j++) {
      if (nums[j] === i) {
        count++;
      }
    }

    if (count === 0) {
      missingNumber = i;
    } else if (count === 2) {
      repeatingNumber = i;
    }
  }

  return { repeatingNumber, missingNumber };
}

const nums = [3, 5, 4, 1, 1];
console.log(findMissingAndRepeating(nums));
```

Time Complexity: O (n^2)

Space Complexity: O(1)

# Better
```ts
function findMissingAndRepeating(nums: number[]): { missing: number; repeating: number } {
  const n = nums.length;
  const count: number[] = new Array(n).fill(0);

  for (const num of nums) {
    count[num - 1]++;
  }

  let missing = -1;
  let repeating = -1;

  for (let i = 0; i < n; i++) {
    if (count[i] === 0) {
      missing = i + 1;
    }

    if (count[i] === 2) {
      repeating = i + 1;
    }
  }

  return { missing, repeating };
}

const nums: number[] = [3, 5, 4, 1, 1];
const result = findMissingAndRepeating(nums);

console.log(result);
```

Time Complexity: O (n)

Space Complexity: O(n)
