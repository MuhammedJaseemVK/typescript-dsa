# Permutations

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
        console.log(stack);
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

permutations = permute([1,2,3])
console.log(permutations)
```