# Intuition

The problem requires finding unique arithmetic triplets in an array, where the difference between consecutive elements in the triplet is a given value `diff`.

## Approach

1. **Set for Lookup**:
   - Use a `HashSet` called `presentNums` to store all the integers from the array `nums`. This allows for O(1) average time complexity for lookups.
   - Traverse the array `nums` and add each element to the `HashSet`.

2. **Finding Triplets**:
   - Initialize a counter `result` to zero to keep track of the number of valid triplets.
   - Iterate through the `HashSet`:
     - For each element `key` in the `HashSet`, check if `key + diff` and `key + 2 * diff` are also in the `HashSet`.
     - If both are present, increment the `result` counter.

3. **Return**:
   - Return the `result` counter, which represents the number of unique arithmetic triplets in the array.

## Complexity

- **Time Complexity**: O(n), where n is the length of the array `nums`. This includes the time to add elements to the `HashSet` and the time to check for triplets.
- **Space Complexity**: O(n), where n is the length of the array `nums`. This space is used by the `HashSet`.

## Code

```Java
class Solution {
    public int arithmeticTriplets(int[] nums, int diff) {
        Set<Integer> presentNums = new HashSet<>();
        int i, result = 0;

        for(i = 0 ; i < nums.length; i = i + 1) {
            presentNums.add(nums[i]);
        }

        for(Integer key: presentNums) {
            if(presentNums.contains(key + diff) && presentNums.contains(key + diff + diff)) {
                result++;
            }
        }

        return result;
    }
}
```
