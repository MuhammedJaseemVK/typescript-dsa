# Next permutation

find next lexicographically greater permutation

## Bruteforce

```ts
function permute(nums: number[]): number[][] {
  const permutations = [];
  const visited = new Array(nums.length).fill(0);
  const stack = [];

  permutation(nums, visited, stack, permutations);

  return permutations;
}
function permutation(
  nums: number[],
  visited: number[],
  stack: number[],
  permutations: number[][]
) {
  if (stack.length === nums.length) {
    permutations.push([...stack]);
    return;
  }

  for (let i = 0; i < visited.length; i++) {
    if (visited[i] !== 1) {
      visited[i] = 1;
      stack.push(nums[i]);

      permutation(nums, visited, stack, permutations);

      stack.pop();
      visited[i] = 0;
    }
  }
}

function nextPermutation(permutations: number[][], current: number[]) {
  const index = permutations.findIndex(permutation=>arraysEqual(permutation,current));
  return index < permutations.length - 1 ? index + 1 : 0;
}

function arraysEqual(a:number[],b:number[]):boolean{
    return a.length === b.length && a.every((val,index)=>val === b[index])
}

const array = [1,2,3];
const permutations = permute(array);
const index = nextPermutation(permutations,array);

console.log(permutations[index]);
```
Time Complexity:  N! x N

Space Complexity:  O(N)
