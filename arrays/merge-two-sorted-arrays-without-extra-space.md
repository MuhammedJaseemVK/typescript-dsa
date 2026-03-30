# Merge two Sorted Arrays Without Extra Space

# Variation 1
Problem Statement: Given two sorted integer arrays nums1 and nums2 of sizes m and n, rearrange their elements such that both arrays remain sorted in non-decreasing order, and all elements in nums1 are less than or equal to all elements in nums2.
The total set of elements across both arrays should remain the same.

Input:

nums1 = [0, 7, 8]

nums2 = [1, 3, 9, 10]

Output:

nums1 = [0, 1, 3]

nums2 = [7, 8, 9, 10]

# Good
```ts
function mergeWithoutExtraSpace(nums1, nums2) {
  let left = nums1.length - 1;
  let right = 0;

  while (left >= 0 && right < nums2.length && nums1[left] > nums2[right]) {
    [nums1[left], nums2[right]] = [nums2[right], nums1[left]];
    left--;
    right++;
  }

  nums1.sort((a, b) => a - b);
  nums2.sort((a, b) => a - b);

  return { nums1, nums2 };
}

const nums1 = [1, 3, 5, 7];
const nums2 = [0, 2, 6, 8, 9];

const result = mergeWithoutExtraSpace(nums1, nums2);
console.log(result.nums1); // [0, 1, 2, 3]
console.log(result.nums2); // [5, 6, 7, 8, 9]
```

Time Complexity: O( min(n,m) + m log n + n log m )

Space Complexity: O(N)

## Better - Shell sort
```ts
function mergeSortedArrays(nums1: number[], nums2: number[]): void {
  const m = nums1.length;
  const n = nums2.length;

  function swapIfGreater(arr1: number[], arr2: number[], i: number, j: number) {
    if (arr1[i] > arr2[j]) {
      [arr1[i], arr2[j]] = [arr2[j], arr1[i]];
    }
  }

  let gap = Math.ceil((m + n) / 2);

  while (gap > 0) {
    let left = 0;
    let right = left + gap;

    while (right < m + n) {
      if (left < m && right >= m) {
        swapIfGreater(nums1, nums2, left, right - m);
      } else if (left >= m) {
        swapIfGreater(nums2, nums2, left - m, right - m);
      } else {
        swapIfGreater(nums1, nums1, left, right);
      }

      left++;
      right++;
    }

    if (gap === 1) {
      break;
    }
    gap = Math.ceil(gap / 2);
  }
}

// Example usage
const nums1 = [1, 3, 5, 7];
const nums2 = [0, 2, 6, 8, 9];

mergeSortedArrays(nums1, nums2);

console.log(nums1); // [0, 1, 2, 3]
console.log(nums2); // [5, 6, 7, 8, 9]
```

Time Complexity: O( log(n+m) * (n+m) )

Space Complexity: O(1)
