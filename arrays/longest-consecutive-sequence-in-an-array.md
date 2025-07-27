# Longest Consecutive Sequence in an Array
You are given an array of ‘N’ integers. You need to find the length of the longest sequence which contains the consecutive elements
## Bruteforce
```ts
function search(array: number[], element: number) {
    for (let i = 0; i < array.length; i++) {
        if (array[i] === element) {
            return true;
        }
    }
    return false;
}

if(nums.length === 0){
    print(0);
    return 0;
}

let maxLength = 1;
for (let i = 0; i < nums.length; i++) {
    let length = 1;
    let element = nums[i];
    while (search(nums, element + 1) === true) {
        length += 1;
        element += 1;
    }
    maxLength = Math.max(length, maxLength);
}
return maxLength;
```
Time Complexity:  O(N^2)

Space Complexity:  O(1)

## Better
```ts
if (nums.length === 0) {
    return 0;
}

nums.sort((a, b) => a - b); //O(NlogN)

let count = 1;
let maxLength = count;
for (let i = 0; i < nums.length - 1; i++) {
    if (nums[i] + 1 === nums[i + 1]) {
        count++;
    }
    else if (nums[i] !== nums[i + 1]) {
        count = 1;
    }
    maxLength = Math.max(maxLength, count);
}

return maxLength
```

