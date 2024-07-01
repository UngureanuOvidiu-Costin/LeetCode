# Intuition

The problem requires counting the number of pairs and leftover integers from a given array of integers. A pair consists of two identical integers.

## Approach

1. **Frequency Counting**:
   - Use a `HashMap` to count the frequency of each integer in the array `nums`.
   - Traverse the array `nums` and populate the frequency map `numsFrequency`.

2. **Counting Pairs and Leftovers**:
   - Initialize an array `result` of size 2 to store the number of pairs and leftover integers.
   - Iterate through the keys of `numsFrequency`:
     - For each key, if its frequency is greater than 1, calculate the number of pairs by integer division of the frequency by 2, and add it to `result[0]`.
   - Calculate the number of leftover integers by subtracting twice the number of pairs from the total number of integers, and store it in `result[1]`.

3. **Return**:
   - Return the `result` array containing the number of pairs and leftover integers.

## Complexity

- **Time Complexity**: `O(n)`, where n is the length of the array `nums`. We traverse the array twice: once to build the frequency map and once to count pairs.

- **Space Complexity**: `O(n)` in the worst case, where `n` is the number of unique integers in the array `nums`. This space is used by the frequency map.

## Code

```Java
class Solution {
    public int[] numberOfPairs(int[] nums) {
        HashMap<Integer, Integer> numsFrequency = new HashMap<>();
        int i;
        int []result = new int[2];

        for(i = 0; i < nums.length; i = i + 1) {
            numsFrequency.put(nums[i], numsFrequency.getOrDefault(nums[i], 0) + 1);
        }

        for(Integer key: numsFrequency.keySet()) {
            if(numsFrequency.get(key) != 1){
                result[0] = result[0] + numsFrequency.get(key) / 2; 
            }
        }

        result[1] = nums.length - 2 * result[0];
        return result;
    }
}
```
