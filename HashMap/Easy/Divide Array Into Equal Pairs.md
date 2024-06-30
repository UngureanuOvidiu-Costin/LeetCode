# Intuition

The problem is to determine whether it is possible to divide the array into pairs such that each pair consists of equal elements. This means each element in the array must appear an even number of times.

## Approach

1. **Frequency Count:** Use a hash map to count the frequency of each element in the array.
2. **Check Frequencies:** Iterate over the frequency map to check if every frequency is even.
3. **Return Result:** If all frequencies are even, return `true`; otherwise, return `false`.

## Complexity

- Time complexity:
**Frequency Count:** Building the frequency map takes `O(n)` time, where `n` is the length of the array nums.
**Check Frequencies:** Iterating over the frequency map takes `O(m)` time, where `m` is the number of unique elements in the array.

- Space complexity:
**Auxiliary Space:** The space required for the frequency map is `O(m)`, where `m` is the number of unique elements in the array. In the worst case, `m` could be `n`, so the space complexity is `O(n)`.

## Code

```Java
class Solution {
    public boolean divideArray(int[] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            frequency.put(nums[i], frequency.getOrDefault(nums[i], 0) + 1);
        }

        for(Integer key: frequency.keySet()) {
            if(frequency.get(key) % 2 != 0) {
                return false;
            }
        }

        return true;
    }
}
```
