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
