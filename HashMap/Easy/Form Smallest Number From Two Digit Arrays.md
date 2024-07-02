# Intuition

The problem requires finding the smallest number that satisfies specific conditions in two arrays. The solution involves using a `TreeMap` to track frequencies and sorting the arrays for direct comparison.

## Approach

1. **Frequency Tracking**:
   - Use a `TreeMap` called `frequency` to store the count of each number from `nums1` and `nums2`.
   - Iterate through `nums1` and add each number to the `frequency` map with an initial count of `1`.
   - Iterate through `nums2` and update the count in the `frequency` map.

2. **Find the Minimum Number**:
   - Iterate through the keys of the `frequency` map:
     - Check if the number appears exactly twice (`frequency.get(key) == 2`).
     - Return the number immediately if it meets this condition.

3. **Sort Arrays for Backup**:
   - If no number satisfies the condition, sort both `nums1` and `nums2`.
   - Return the smallest number formed by combining the smallest elements from both sorted arrays.

4. **Return Result**:
   - Return the smallest number found either from the `frequency` map or from the sorted arrays.

## Complexity

- **Time Complexity**: O(n log n), where n is the length of the longer array between `nums1` and `nums2`. This includes the time to sort the arrays.

- **Space Complexity**: O(n), where n is the total number of unique elements across `nums1` and `nums2`. This space is used by the `TreeMap`.

## Code

```Java
class Solution {
    public int minNumber(int[] nums1, int[] nums2) {
        TreeMap<Integer, Integer> frequency = new TreeMap<>();

        for (int num : nums1) {
            frequency.put(num, 1);
        }

        for (int num : nums2) {
            frequency.put(num, frequency.getOrDefault(num, 0) + 1);
        }

        int result = -1;
        for (int key : frequency.keySet()) {
            if (frequency.get(key) == 2) {
                return key;
            }
        }

        Arrays.sort(nums1);
        Arrays.sort(nums2);
        
        return Math.min(nums1[0], nums2[0]) * 10 + Math.max(nums1[0], nums2[0]);
    }
}
```
