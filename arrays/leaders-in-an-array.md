# Leaders in an Array
Given an array, print all the elements which are leaders. A Leader is an element that is greater than all of the elements on its right side in the array.

## Bruteforce
```ts
const arr = [6, 16, 17, 4, 3, 5, 2];
const leaders = [];
for(let i=0;i<arr.length;i++){
    let isLeader = true;
    for(let j=i+1;j<arr.length;j++){
        if(arr[i]<arr[j]){
            isLeader = false;
            break;
        }
    }
    if(isLeader){
        leaders.push(arr[i]);
    }
}
console.log(leaders);
```
Time Complexity:  O(N^2)

Space Complexity:  O(N)

## Optimal
```ts
const nums = [6, 16, 17, 4, 3, 5, 2];

const n = nums.length;
let max = nums[n-1];

const leaders = [max];

for (let i = n-2;i>=0;i--){
    if(nums[i] > max){
        max = nums[i];
        leaders.push(nums[i])
    }
}

console.log(leaders);
```
Time Complexity:  O(N)

Space Complexity:  O(1)
