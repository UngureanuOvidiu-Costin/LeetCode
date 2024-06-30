# Intuition

The problem is to find the final value of an integer original after repeatedly doubling it until it is no longer present in a given array nums. This can be solved efficiently using a set to quickly check if the current value exists in the array.

## Approach

1. **Convert Array to Set:** Convert the array nums into a set to allow `O(1)` average-time complexity for membership checks.
2. **Check and Double:** Starting from `original`, check if it is present in the set. If it is, double its value and repeat the check.
3. **Return Result:** Once a value is found that is not present in the set, return this value.

## Complexity

- Time complexity: `O(n) + 𝑂(log(max value in nums))`
**Set Construction:** Constructing the set from the array takes O(n) time, where n is the length of nums.
**Doubling and Checking:** In the worst case, the value of original doubles `𝑂(log(max value in nums))` times until it is no longer in the set. Each membership check takes O(1) average-time complexity.

- Space complexity:
**Auxiliary Space:** The set `numsHash` stores all elements of nums, which takes `O(n)` space.

## Code

```Java
class Solution {
    public int findFinalValue(int[] nums, int original) {
        int i, result = original;
        Set<Integer> numsHash = new HashSet<>();
    
        for(i = 0; i < nums.length; i = i + 1) {
            numsHash.add(nums[i]);
        }

        while(numsHash.contains(result)) {
            result = result * 2;
        }

        return result;
    }
}
```
