# Permutations

## Recursion
This solution maintains lexical order of permuatations.
```ts
function permute(nums: number[]): number[][] {
    const permutations = [];
    const visited = new Array(nums.length).fill(0);
    const stack = [];

    permutation(nums, visited, stack, permutations)

    return permutations
};
function permutation(nums: number[], visited: number[], stack: number[], permutations: number[][]) {
    if (stack.length === nums.length) {
        permutations.push([...stack])
        return;
    }
    
    for (let i = 0; i < visited.length; i++) {
        if (visited[i] !== 1) {
            visited[i] = 1;
            stack.push(nums[i]);

            permutation(nums, visited, stack, permutations)

            stack.pop();
            visited[i] = 0;
        }
    }
}

const permutations = permute([1,2,3])
console.log(permutations)
```
Time Complexity:  N! x N

Space Complexity:  O(N)

## Backtracking
This solution does not maintains lexical order of permuatations.
```ts
function permute(nums: number[]): number[][] {
    const permutations = [];
    permutation(nums, 0, permutations)
    return permutations

};
function permutation(nums: number[], index: number, permutations: number[][]) {
    if (index === nums.length) {
        permutations.push([...nums]);
        return;
    }

    for (let i = index; i < nums.length; i++) {
        swap(nums, i, index);
        permutation(nums, index + 1, permutations);
        swap(nums, i, index);
    }
}

function swap(nums: number[], i: number, j: number) {
    const temp = nums[i]
    nums[i] = nums[j]
    nums[j] = temp
}

const permutations = permute([1,2,3]);
console.log(permutations)
```
Time Complexity: O(N! X N)

Space Complexity: O(1)

