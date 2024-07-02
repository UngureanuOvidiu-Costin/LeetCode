# Intuition

The problem requires counting the number of unique triplets `(i, j, k)` where all elements are distinct. By utilizing the frequency of each number in the array, we can efficiently count such triplets.

## Approach

1. **Frequency Counting**:
   - Use a `HashMap` called `occurrence` to store the frequency of each integer in the array `nums`.
   - Iterate through the array and populate the `occurrence` map.

2. **Count Unique Triplets**:
   - Initialize `a` to zero, which will track the cumulative count of processed elements.
   - Iterate through the values in the `occurrence` map:
     - For each value, calculate the number of elements remaining after excluding the current value and already processed elements (`temp`).
     - Update the result by adding the product of `temp`, `a`, and the current value.
     - Update `a` by adding the current value to it.

3. **Return**:
   - Return the `result`, which represents the number of unique triplets.

## Complexity

- **Time Complexity**: `O(n)`, where n is the length of the array `nums`. This includes the time to build the frequency map and to count the unique triplets.

- **Space Complexity**: `O(n)`, where n is the number of unique elements in the array `nums`. This space is used by the `HashMap`.

## Code

```Java
class Solution {
    public int unequalTriplets(int[] nums) {
        
        HashMap<Integer, Integer> occurence = new HashMap<>();
        int i, temp, result = 0, a = 0;

        for(i = 0; i < nums.length; i = i + 1) {
            occurence.put(nums[i], occurence.getOrDefault(nums[i], 0) + 1);
        }

        
        for(Integer value: occurence.values()) {
            temp = nums.length - value - a;
            result = result + temp * a * value;
            a = a + value;
        }

        return result;
    }
}
```
